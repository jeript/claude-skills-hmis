---
name: hmis-inventory
description: >
  HMIS Bed and Unit Inventory (data element 2.07) - project inventory management, utilization
  analysis, and reporting. Use this skill when working with inventory data in R, including:
  bed counts, unit counts, inventory start/end dates, dedicated beds, household type breakdowns,
  bed type and availability (ES), utilization rates, HIC reporting, or any analysis involving
  Inventory.csv. Inventory fluctuates over time - always account for inventory start and end
  dates when calculating point-in-time or period-based inventory counts. Always invoke
  hmis-foundations alongside this skill for Active Clients and Household Types logic.
---

# HMIS Bed and Unit Inventory (Element 2.07)

Source: FY 2026 HMIS Data Standards | Released October 2025

## Applicability

Residential projects only (excludes SO, SSO, Day Shelter, HP, CE):

| Project Type | Code | Inventory Required |
|-------------|------|-------------------|
| Emergency Shelter - Entry Exit | 0 | Yes |
| Emergency Shelter - Night-by-Night | 1 | Yes |
| Transitional Housing | 2 | Yes |
| PH - Permanent Supportive Housing | 3 | Yes |
| Safe Haven | 8 | Yes |
| PH - Housing Only | 9 | Yes |
| PH - Housing with Services | 10 | Yes |
| PH - Rapid Re-Housing (Housing subtype only) | 13 (subtype 2) | Yes |
| PH - RRH Services Only | 13 (subtype 1) | **No** |

## Inventory Start and End Dates - Critical Concept

**Inventory is NOT static.** Each inventory record has an `InventoryStartDate` and an optional `InventoryEndDate` that define when that inventory was active. When analyzing inventory:

- **Current/active inventory**: `InventoryEndDate` is NULL (or after the date of interest)
- **Point-in-time inventory**: Filter to records where `InventoryStartDate` <= target date AND (`InventoryEndDate` is NULL OR `InventoryEndDate` >= target date)
- **Period-based inventory**: For a date range, inventory is relevant if it overlaps the range: `InventoryStartDate` <= range end AND (`InventoryEndDate` is NULL OR `InventoryEndDate` >= range start)

### When Inventory Changes

A project's inventory changes are documented by **closing the old record** (setting `InventoryEndDate` to the day before the change) and **creating a new record** (with `InventoryStartDate` on the effective date). This applies when:

- Beds are added or removed (new record with updated total)
- Dedicated bed counts change
- Any other field value changes

There should only be **one active inventory record** per combination of: ProjectID + CoCCode + HouseholdType + ESBedType + Availability.

### R Pattern for Point-in-Time Inventory

```r
# Get inventory active on a specific date
inventory_on_date <- Inventory %>%
  filter(
    InventoryStartDate <= target_date,
    is.na(InventoryEndDate) | InventoryEndDate >= target_date,
    is.na(DateDeleted)
  )
```

### R Pattern for Average Inventory Over a Period

```r
# For utilization rates over a reporting period, calculate weighted average
# based on days each inventory record was active in the period
inventory_weighted <- Inventory %>%
  filter(
    InventoryStartDate <= report_end_date,
    is.na(InventoryEndDate) | InventoryEndDate >= report_start_date,
    is.na(DateDeleted)
  ) %>%
  mutate(
    effective_start = pmax(InventoryStartDate, report_start_date),
    effective_end = pmin(
      coalesce(InventoryEndDate, report_end_date),
      report_end_date
    ),
    days_active = as.numeric(effective_end - effective_start) + 1,
    total_days = as.numeric(report_end_date - report_start_date) + 1,
    weight = days_active / total_days,
    weighted_beds = BedInventory * weight,
    weighted_units = UnitInventory * weight
  )
```

## Inventory Structure

### Multiple Records Per Project

A project can have multiple **simultaneous** active inventory records when it:
- Serves more than one **Household Type** (separate record per type)
- Has more than one **Bed Type** or **Availability** (ES only - separate record per combination)
- Operates in more than one **CoC** (separate record per CoC)

### Household Type (2.07.4)

| Code | Type |
|------|------|
| 1 | Households without children |
| 3 | Households with at least one adult and one child |
| 4 | Households with only children |

### Bed Type (2.07.5) - Emergency Shelter Only (types 0 and 1)

| Code | Type | Description |
|------|------|-------------|
| 1 | Facility-based beds | Beds in a dedicated homeless assistance facility |
| 2 | Voucher beds | Hotel/motel beds via vouchers |
| 3 | Other beds | Beds in non-dedicated facility (e.g., church) |

NULL for all non-ES project types.

### Availability (2.07.6) - Emergency Shelter Only (types 0 and 1)

| Code | Type | Description |
|------|------|-------------|
| 1 | Year-round | Available all year |
| 2 | Seasonal | Planned periods of higher demand, set start/end dates |
| 3 | Overflow | Ad hoc/temporary during demand exceeding capacity |

NULL for all non-ES project types.

## Bed Inventory Breakdown

Total bed inventory = sum of all dedicated + non-dedicated beds. Categories are **mutually exclusive**.

| CSV Field | DE# | Description |
|-----------|-----|-------------|
| CHVetBedInventory | 2.07.7 | Dedicated: Chronically homeless Veterans |
| YouthVetBedInventory | 2.07.8 | Dedicated: Youth Veterans (age <= 24) |
| VetBedInventory | 2.07.9 | Dedicated: Other Veterans (not youth, not CH) |
| CHYouthBedInventory | 2.07.10 | Dedicated: Chronically homeless Youth |
| YouthBedInventory | 2.07.11 | Dedicated: Other Youth (not Veteran, not CH) |
| CHBedInventory | 2.07.12 | Dedicated: Other CH (not youth, not Veteran) |
| OtherBedInventory | 2.07.13 | Non-dedicated beds |
| BedInventory | 2.07.14 | **Total** bed inventory |
| UnitInventory | 2.07.15 | **Total** unit inventory |

**Validation:** `BedInventory` should equal the sum of all dedicated fields + `OtherBedInventory`.

**DedicatedPLUS beds** do NOT count as dedicated beds unless a subset is truly dedicated.

## Utilization Analysis

Utilization = clients served / inventory capacity.

### Point-in-Time Utilization

```r
# Beds occupied on a specific date vs inventory on that date
utilization_pit <- active_clients_on_date %>%
  count(ProjectID, HouseholdType, name = "clients") %>%
  left_join(inventory_on_date, by = c("ProjectID", "HouseholdType")) %>%
  mutate(utilization_rate = clients / BedInventory)
```

### Period Utilization (Bed-Night Based)

For ES-NbN: total bed-nights recorded / (inventory * days in period)
For other types: total client-nights / (inventory * days in period)

See `references/inventory-details.md` for full utilization methodology and determining bed/unit counts for projects without fixed inventory.

## Inventory for HIC Reporting

- Inventory must be accurate within the last week of January, April, July, October
- HIC night: use inventory active on that specific date
- For projects serving multiple household types without designated beds: distribute based on HIC night usage or average utilization

## References

- `references/inventory-details.md` - Detailed inventory management rules, determining bed/unit counts, historical tracking
- Source Data Standards: `C:\Users\Jeri\Documents\R\HMIS-Skills\HMIS-Data-Standards_2026 MD.md` (section 2.07, line 1489)

## Glossary Dependencies

This skill works with `hmis-foundations` for:
- Active Clients (for utilization calculations)
- Household Types (inventory is split by household type)
- Bed-Night and Length of Stay (for occupancy calculations)

This skill works with `hmis-csv` for:
- Inventory.csv field definitions and join keys
- Project.csv for ProjectType filtering
- ProjectCoC.csv for CoC-level inventory
