# Inventory Management Details

## Inventory Record Lifecycle

### Creating Records

- Created at initial HMIS project setup
- Reviewed/updated no less than annually
- Must be finalized and accurate by time of HIC
- `InventoryStartDate` = date inventory became available (estimate OK if precise date unknown)
- For under-development beds: `InventoryStartDate` = expected availability date (may be future)

### One Active Record Rule

There should only be **one active inventory record** per combination of:
- ProjectID
- CoCCode
- HouseholdType
- ESBedType (for ES projects)
- Availability (for ES projects)

At annual review, if multiple records exist for beds of the same type with all `InventoryStartDate` values more than one year before the most recent HIC, they should be consolidated:
1. Close individual records (set `InventoryEndDate` to day before current date)
2. Create new combined record with total inventory and the **earliest** `InventoryStartDate` from the individual records

### Inventory Increases

When a project adds beds of the same type/availability/household type/CoC:
1. Close existing record: set `InventoryEndDate` = day before new inventory available
2. Create new record: `InventoryStartDate` = date new inventory available, with updated total bed count

### Inventory Decreases

When a project reduces beds but continues serving:
1. Close existing record: set `InventoryEndDate` = day before effective reduction
2. Create new record: `InventoryStartDate` = effective date of reduction, with smaller bed count

### Eliminating All Inventory for a Household Type

Set `InventoryEndDate` = last date beds were available. No new record needed.

### Changes to Dedicated Bed Counts

1. Close old record: `InventoryEndDate` = day before effective date of change
2. Create new record: `InventoryStartDate` = effective date of change, with updated dedicated counts

## Significant vs Minor Changes

- **Minor day-to-day fluctuations**: Need NOT be recorded
- **Significant changes**: Should be recorded as they occur (e.g., project exhausts annual budget in 6 months)
- What constitutes "significant" is left to community to define
- Inventory should reflect reality of residential project operations

### Timing of Updates

- Must be accurate within last week of January, April, July, October (for APR and LSA)
- CoC should backdate revised inventory to actual date of significant change
- Multiple changes can be entered at once to reflect history
- For gradual changes over weeks, pick a single mid-period date

## Determining Total Bed Inventory

`BedInventory` = total number of beds available for occupancy as of `InventoryStartDate`

- Generally equivalent to number of persons a project can house on a given night
- For ES: count distinctly for each Bed Type + Availability combination

### Projects Serving Multiple Household Types Without Designated Beds

Distribute total beds among household types using one of:
1. **HIC night distribution**: Based on how beds were used on HIC night. If not at capacity, extrapolate from prorated distribution.
2. **Average utilization**: Based on average usage over time. E.g., 100 beds, half used by HH without children, half by HH with children → 50/50 split.

### Projects Without Fixed Bed Counts

- **Units only, no fixed beds**: Estimate beds = average household size × units (e.g., 30 family units × avg size 3 = 90 beds)
- **Fixed vouchers**: Beds/units based on number of vouchers currently funded and available
- **No fixed units/vouchers** (e.g., ES hotel/motel, RRH, some scattered-site PSH): Beds/units based on maximum number of persons/households that can be housed on a given night

## Determining Unit Inventory

`UnitInventory` = total units available for occupancy as of `InventoryStartDate`

- Projects without fixed units (e.g., congregate shelter): May record bed inventory, number of residential facilities, or number of rooms as unit inventory

## Dedicated Bed Categories

All categories are **mutually exclusive**. Each dedicated bed falls into exactly one category.

| Category | Who It Serves |
|----------|--------------|
| CH Veterans | Veterans experiencing chronic homelessness + household members |
| Youth Veterans | Veterans age ≤ 24 experiencing homelessness + household members |
| Other Veterans | Veterans not youth and not CH + household members |
| CH Youth | Youth age ≤ 24 experiencing chronic homelessness + household members |
| Other Youth | Youth age ≤ 24, not Veterans, not CH + household members |
| Other CH | Non-youth, non-Veteran persons experiencing CH + household members |
| Non-dedicated | All other beds not in any dedicated category |

**DedicatedPLUS beds**: Do NOT qualify as dedicated. Only include in dedicated counts if a subset is truly dedicated per the definitions above.

**Validation**: `BedInventory` must equal sum of all dedicated categories + `OtherBedInventory` (non-dedicated).

## Bed Type and Housing Type Consistency

`ESBedType` should be logically consistent with `HousingType` at project level:
- Facility-based beds → Project `HousingType` = "Site-based"
- Voucher beds → Project `HousingType` = "Tenant-based"

If an ES has both facility-based beds AND hotel/motel vouchers, these should be **two separate HMIS projects**.

## Inventory.csv Field Reference

| DE# | CSV Field | Type | Null | Notes |
|-----|-----------|------|------|-------|
| | InventoryID | S32 | | Unique identifier |
| | ProjectID | S32 | | FK to Project.csv |
| 2.07.3 | CoCCode | S6 | Y | FK to ProjectCoC.csv |
| 2.07.4 | HouseholdType | I | | 1=w/o children, 3=w/ children+adults, 4=only children |
| 2.07.6 | Availability | I | Y | 1=Year-round, 2=Seasonal, 3=Overflow. NULL if not ES |
| 2.07.15 | UnitInventory | I | | Total units |
| 2.07.14 | BedInventory | I | | Total beds |
| 2.07.7 | CHVetBedInventory | I | Y | Dedicated CH Veteran beds |
| 2.07.8 | YouthVetBedInventory | I | Y | Dedicated Youth Veteran beds |
| 2.07.9 | VetBedInventory | I | Y | Dedicated Other Veteran beds |
| 2.07.10 | CHYouthBedInventory | I | Y | Dedicated CH Youth beds |
| 2.07.11 | YouthBedInventory | I | Y | Dedicated Other Youth beds |
| 2.07.12 | CHBedInventory | I | Y | Dedicated Other CH beds |
| 2.07.13 | OtherBedInventory | I | Y | Non-dedicated beds |
| 2.07.5 | ESBedType | I | Y | 1=Facility, 2=Voucher, 3=Other. NULL if not ES |
| 2.07.1 | InventoryStartDate | D | | Date inventory became active |
| 2.07.2 | InventoryEndDate | D | Y | NULL if current/active |
