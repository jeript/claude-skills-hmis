---
name: hmis-projects
description: >
  HMIS Project Descriptor data elements (2.01-2.03, 2.06-2.09) - everything that defines a
  project: organization, project info, CoC, funding sources, bed/unit inventory, HMIS participation,
  and CE participation. Use this skill when working with project-level data in R, including:
  project setup, project types, operating dates, inventory and utilization analysis, funding
  source filtering, HIC reporting, or any analysis involving Project.csv, Inventory.csv,
  Funder.csv, ProjectCoC.csv, HMISParticipation.csv, or CEParticipation.csv. Inventory
  fluctuates over time - always account for inventory start/end dates and operating dates.
  Always invoke hmis-foundations alongside this skill for Active Clients and Household Types.
---

# HMIS Project Descriptors (FY 2026)

Source: FY 2026 HMIS Data Standards | Released October 2025

## Project Descriptor Elements Overview

| Element | Name | CSV File | What It Defines |
|---------|------|----------|----------------|
| 2.01 | Organization Information | Organization.csv | Org name, ID, victim service provider status |
| 2.02 | Project Information | Project.csv | Project name, type, housing type, RRH subtype, operating dates, continuum project flag |
| 2.03 | Continuum of Care Information | ProjectCoC.csv | CoC code(s), geocode, geography type, address |
| 2.06 | Funding Sources | Funder.csv | Federal partner funding, grant ID, grant start/end dates |
| 2.07 | Bed and Unit Inventory | Inventory.csv | Beds, units, dedicated beds, bed type, availability |
| 2.08 | HMIS Participation Status | HMISParticipation.csv | HMIS participation type and date range |
| 2.09 | CE Participation Status | CEParticipation.csv | CE access point status, referral acceptance |

## Project Types (2.02.6) - Critical Reference

| Code | Type | Abbreviation | Residential? | Inventory? |
|------|------|-------------|:------------:|:----------:|
| 0 | Emergency Shelter - Entry Exit | ES-EE | Yes | Yes |
| 1 | Emergency Shelter - Night-by-Night | ES-NbN | Yes | Yes |
| 2 | Transitional Housing | TH | Yes | Yes |
| 3 | PH - Permanent Supportive Housing | PH-PSH | Yes | Yes |
| 4 | Street Outreach | SO | No | No |
| 6 | Services Only | SSO | No | No |
| 8 | Safe Haven | SH | Yes | Yes |
| 9 | PH - Housing Only | PH-HO | Yes | Yes |
| 10 | PH - Housing with Services | PH-HSO | Yes | Yes |
| 11 | Day Shelter | DS | No | No |
| 12 | Homelessness Prevention | HP | No | No |
| 13 | PH - Rapid Re-Housing | PH-RRH | Subtype 2 only | Subtype 2 only |
| 14 | Coordinated Entry | CE | No | No |

RRH subtypes: 1 = Services Only (no inventory), 2 = Housing with or without services (has inventory).

## Operating Dates (2.02)

- `OperatingStartDate`: First day project provided services/housing
- `OperatingEndDate`: Last day (NULL if still operating; may be future date)
- When a project closes, **all clients must be exited on or before the operating end date**

## Data Quality Gotchas - Common Admin Mistakes

**Inventory without operating end date alignment:**
HMIS admins sometimes set an `OperatingEndDate` on a project without closing inventory records. When this happens, treat open inventory records as ending on the `OperatingEndDate`:

```r
# Fix: cap inventory end dates at project operating end date
inventory_fixed <- Inventory %>%
  left_join(Project %>% select(ProjectID, OperatingEndDate), by = "ProjectID") %>%
  mutate(
    EffectiveEndDate = case_when(
      !is.na(InventoryEndDate) ~ InventoryEndDate,
      !is.na(OperatingEndDate) ~ OperatingEndDate,
      TRUE ~ NA_Date_
    )
  )
```

**Inventory ended but project still operating:**
This is legitimate - a project may lose beds/funding while continuing to operate. Treat as **0 inventory** for that period. Do NOT assume the last known inventory continues.

```r
# Point-in-time inventory respecting both dates
pit_inventory <- inventory_fixed %>%
  filter(
    InventoryStartDate <= target_date,
    is.na(EffectiveEndDate) | EffectiveEndDate >= target_date,
    is.na(DateDeleted)
  )
# Projects with no matching inventory record have 0 beds on that date
```

## Inventory - Key Concepts

**Inventory fluctuates over time.** Each record has `InventoryStartDate` and `InventoryEndDate`. See `references/inventory-details.md` for full rules.

### Point-in-Time Inventory
```r
filter(InventoryStartDate <= target_date,
       is.na(EffectiveEndDate) | EffectiveEndDate >= target_date)
```

### Period Inventory (weighted average for utilization)
```r
mutate(
  effective_start = pmax(InventoryStartDate, report_start_date),
  effective_end = pmin(coalesce(EffectiveEndDate, report_end_date), report_end_date),
  days_active = as.numeric(effective_end - effective_start) + 1,
  weight = days_active / as.numeric(report_end_date - report_start_date + 1),
  weighted_beds = BedInventory * weight
)
```

### One Active Record Rule
One active record per: ProjectID + CoCCode + HouseholdType + ESBedType + Availability

### ES-Specific Fields (types 0 and 1 only)
- **Bed Type**: 1=Facility-based, 2=Voucher, 3=Other (NULL for non-ES)
- **Availability**: 1=Year-round, 2=Seasonal, 3=Overflow (NULL for non-ES)

### Dedicated Beds (mutually exclusive categories)
CHVetBedInventory + YouthVetBedInventory + VetBedInventory + CHYouthBedInventory + YouthBedInventory + CHBedInventory + OtherBedInventory = BedInventory

## Funding Sources (2.06) - Filtering for Reports

Grant dates define when funding is active. Critical for SPM Measure 4 and other fund-specific analyses:
```r
# Select projects with active CoC funding in report range
coc_funded <- Funder %>%
  filter(
    Funder %in% c(2, 3, 4, 5, 6, 43, 44, 54, 55, 56),
    StartDate <= report_end_date,
    is.na(EndDate) | EndDate >= report_start_date
  )
```

## HMIS Participation (2.08)

| Code | Status |
|------|--------|
| 0 | Not Participating |
| 1 | HMIS Participating |
| 2 | Comparable Database Participating |

Has `HMISParticipationStatusStartDate` and `HMISParticipationStatusEndDate`. When participation status changes, old record is closed and new one created.

When a project stops participating: exit all clients on or before the end date, create new "Not Participating" record, do NOT change inventory.

## CE Participation (2.09)

Tracks whether project is a CE access point and/or receives CE referrals. Has start/end dates for status changes.

## Emergency Shelter Considerations

- **ES-EE vs ES-NbN**: Different project types with different reporting implications
- NbN: client entered once, each night recorded separately via bed-night dates
- NbN auto-exit: community sets standard (e.g., 90 days from last bed-night), exit date = day after last bed-night
- If shelter type changes (EE↔NbN): must create new project, exit all clients, re-enter in new project
- Bed Type must be consistent with Housing Type: facility-based = site-based, voucher = tenant-based
- If ES has both facility-based AND voucher beds: should be **two separate HMIS projects**

## References

- `references/inventory-details.md` - Full inventory management rules, lifecycle, dedicated beds, determining counts
- `references/project-setup.md` - Project setup rules, SSO affiliations, RRH subtypes, multi-funding
- Source: `C:\Users\Jeri\Documents\R\HMIS-Skills\HMIS-Data-Standards_2026 MD.md`
