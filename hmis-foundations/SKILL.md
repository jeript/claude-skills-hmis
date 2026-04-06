---
name: hmis-foundations
description: >
  HMIS Standard Reporting Terminology Glossary - foundational building blocks for all HMIS reports.
  Use this skill whenever implementing HMIS report logic in R, when a report specification references
  "Glossary" sections (Active Clients, Leavers/Stayers, Age, Household Types, etc.), or when writing
  R code for HUD reporting (APR, CAPER, SPM, CE APR, LSA, PATH). This skill provides the shared
  programming logic that all HMIS federal reports depend on. Always invoke this skill alongside
  report-specific skills like hmis-apr-core, hmis-apr-income-exits, hmis-apr-populations, or hmis-spm.
---

# HMIS Standard Reporting Terminology Glossary (FY 2026)

Source: HUD FY 2026 HMIS Data Standards | Released October 2025 | Effective October 1, 2025

## Definitions

- **Adult**: Client aged 18+. **Child**: Client under 18.
- **Household**: Person(s) served together, linked in a project enrollment.
- **Lodging project**: Temporary overnight accommodations (e.g., emergency shelter).
- **Residential project**: Overnight accommodations including long-term (e.g., PSH).
- **Report Date Range**: User-supplied `[report start date]` and `[report end date]`.

## Active Clients

Data elements: 2.02, 3.10, 3.11, 3.20, 4.12, 4.14, W1, P1, R14, V2

### Method 1: Active Clients by Start/Exit (default)

```
[project start date] <= [report end date]
and ([project exit date] is null or [project exit date] >= [report start date])
```

### Method 2: Active Clients by Date of Service

For NbN shelters, street outreach, services-only projects. Must include Method 1 as basis, then filter on service dates within enrollment. `[date of activity]` is generic for bed-night, current living situation, or service date.

```
[date of activity] >= [project start date]
and (
    [project exit date] is null
    or if [project type] = 1 and [activity type] = bed-night
    then [date of activity] < [project exit date]
    else [date of activity] <= [project exit date]
)
and (
    ([project exit date] >= [report start date] and [project exit date] <= [report end date])
    or (
        [project start date] <= [report end date]
        and ([project exit date] is null or [project exit date] > [report end date])
        and [date of activity] >= [report start date]
        and [date of activity] <= [report end date]
    )
)
```

### Method 3: Active Clients in Residence

Requires client to be in residence. For NbN shelters (type 1): needs bed-night in range. For ES-EE/TH/SH (type 0,2,8): start/exit only. For PH (type 3,9,10,13): requires `[housing move-in date]` in range. See `references/active-clients-methods-3-5.md` for full pseudocode.

### Method 4: Post-Exit Services

```
[data collection stage] = 6
and [date of service] >= [report start date] and [date of service] <= [report end date]
```

### Method 5: 1+ Nights Active

Like Method 3 but PH projects do NOT require `[housing move-in date]`. See `references/active-clients-methods-3-5.md`.

## Age (3.03, 3.10)

```
If [project start date] <= [report start date] Then
    Age = [report start date] - [date of birth]
Else
    Age = [project start date] - [date of birth]
```

Use `[date of birth data quality]` to handle blank/default DOB. For multiple project stays, use latest `[project start date]` or `[report start date]`, whichever is greater.

### Youth Households

Households where age is known >= 12 and <= 24 for at least one member and no member is known to be 25+. Clients with unknown age do not impact this determination.

## Household Types (5.09)

Determined using all active clients sharing the same `[household ID]`. Apply in order:

| Type | Adults | Children | Unknown Age |
|------|--------|----------|-------------|
| With Children and Adults | 1+ | 1+ | any |
| Without Children | 1+ | 0 | 0 |
| With Only Children | 0 | 1+ | 0 |
| Unknown | any not above | | 1+ |

## Unduplicated Counts (5.08, 5.09, 3.15)

- **Household counts**: Distinct count of `[personal ID]` where `[relationship to head of household]` = Self.
- **By individual attribute**: Use head of household's data for the most recent HoH.
- **Client counts by household type**: Distinct count of clients by household type. Sum may exceed total (client in multiple households).

## Project Leavers and Stayers (3.10, 3.11)

Based on client's **last project enrollment** during reporting period.

**Leavers:**
```
[project exit date] >= [report start date] and [project exit date] <= [report end date]
```

**Stayers:**
```
[project start date] <= [report end date]
and ([project exit date] is null or [project exit date] > [report end date])
```

## Bed-Night and Length of Stay (2.02, 3.10, 3.11, 3.20, 4.14)

| Project Type | Method |
|-------------|--------|
| 0, 2, 4, 6, 7, 8, 11, 12, 14 | Method 1: `[min(exit, end+1)] - [max(start, report_start)]` |
| 1 (NbN ES) | Method 2: Count unique bed-night dates in range within enrollment |
| 3, 9, 10, 13 (PH) | Method 3: `[min(exit, end+1)] - [max(move-in, report_start)]` |

## Handling Housing Move-In Dates (3.20)

- Disregard `[housing move-in date]` if before `[project start date]`, after `[project exit date]`, or after `[report end date]` (treat as null).
- If member's `[project start date]` <= HoH's `[housing move-in date]`: inherit HoH's date (unless member exited before move-in).
- If member's `[project start date]` > HoH's `[housing move-in date]`: use member's `[project start date]`.

## Contact (3.10, 3.11, 4.12)

Street outreach contacts via `[current living situation]`. Each contact counts unless report says otherwise.

```
[project start date] <= [report end date]
and ([project exit date] is null or [project exit date] >= [report start date])
and [date of CLS] >= [report start date] and [date of CLS] <= [report end date]
and [date of CLS] >= [project start date]
and ([date of CLS] <= [project exit date] or [project exit date] is null)
```

## Date of Engagement (4.13)

One per enrollment. Count engaged clients:
```
[date of engagement] >= [report start date] and <= [report end date]
and >= [project start date] and (<= [project exit date] or exit is null)
```

## Date of Enrollment (PATH only, P3)

Client enrolled if `[client became enrolled in PATH]` = Yes. `[date of status determination]` = enrollment date.

## References

For detailed specifications on complex topics, read these reference files:

- `references/chronic-homelessness.md` - CH at Project Start flowchart, CH at Point-in-Time calculation, CH due to household members
- `references/income-annual-assessment.md` - 7-row income determination table, 10-step annual assessment selection
- `references/data-quality-report.md` - HMIS Data Quality Report Q1-Q7 programming instructions
- `references/active-clients-methods-3-5.md` - Full pseudocode for Methods 3 and 5
- `references/exit-destinations.md` - Exit destination classification matrix (which destinations are positive/excluded by project type)
- `references/appendix-crosswalk.md` - Federal Reports and Glossary Crosswalk table
