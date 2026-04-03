# Measure 1: Length of Time Persons Experience Homelessness

## Overview

Average and median length of time experiencing homelessness for active clients across relevant project types. Includes time during AND prior to the report range.

**Measure 1a**: Uses start/exit/bed-night dates strictly as entered in HMIS (no 3.917 data). Goes back no further than `[lookback stop date]` or `[date of birth]`.

**Measure 1b**: Also includes `[approximate date this episode of homelessness started]` (3.917.3) and time in PH between `[project start date]` and `[housing move-in date]`. Can extend prior to `[lookback stop date]` but never before `[date of birth]`.

## Universes

| Metric | Project Types |
|--------|--------------|
| 1a Row 2 | ES-EE (0), ES-NbN (1), SH (8) |
| 1a Row 3 | ES-EE (0), ES-NbN (1), SH (8), TH (2) |
| 1b Row 2 | ES-EE (0), ES-NbN (1), SH (8), PH (3,9,10,13) |
| 1b Row 3 | ES-EE (0), ES-NbN (1), SH (8), TH (2), PH (3,9,10,13) |

**Glossary Reference:** Active Clients - Method 5: 1+ Nights Active

**Data elements:** 2.02.6, 3.10, 3.11, 3.917.3, 3.20

## Programming Instructions (9 Steps)

### Step 1: Select active clients and preserve bed nights

Select active clients using Method 5 (1+ Nights Active) across all relevant project types in the CoC.

**Bed night definitions:**
- **ES-EE, SH, TH**: Every date from `[project start date]` to lesser of (`[project exit date]` - 1) or `[report end date]`. Exit date itself is NOT a bed night.
- **ES-NbN**: Individual bed-night records between `[project start date]` and lesser of (`[project exit date]` - 1) or `[report end date]`.
- **PH (Measure 1b only)**: Every date from `[project start date]` up to but NOT including `[housing move-in date]`. Only for stays meeting Literal Homelessness criteria. If move-in > report end, include through report end. If move-in is null, include through lesser of (exit - 1) or report end.

PH stays in Measure 1b must meet:
```
Literal Homelessness criteria met
And (
    ([project start date] >= [report start date] and <= [report end date])
    Or ([housing move-in date] >= [report start date] and <= [report end date])
    Or ([housing move-in date] is null and [project exit date] >= [report start date] and <= [report end date])
)
```

### Step 2: Negate overlapping bed nights

Higher-priority housing overrides lower-priority:
- **1a Row 2 and 1b Row 2**: TH negates overlapping ES/SH time
- **1b Row 2**: TH also negates overlapping PH homeless time
- **All measures**: PH `[housing move-in date]` negates overlapping homeless time (only when move-in <= report end and not null)

Remove clients with zero bed nights after negation.

### Step 3: Determine `[client end date]`

Each client's latest homeless bed night that is >= `[report start date]` and <= `[report end date]`.
- For ES-EE: one day prior to exit date or report end, whichever earlier
- For ES-NbN: based on actual bed-night records
- Measure 1b: do NOT include `[housing move-in date]` itself

### Step 4: Determine `[client start date]`

`[client start date]` = `[client end date]` - 365 days (no earlier than `[lookback stop date]`)

### Step 5 (Measure 1b only): Include 3.917 data

Only for stays meeting Literal Homelessness criteria:
- **Entry-exit stays**: If `[project start date]` >= `[lookback stop date]`, add every night from `[approximate date started]` through `[project start date]`
- **NbN stays**: If `[earliest bed night]` >= `[lookback stop date]`, add every night from `[approximate date started]` through `[earliest bed night]`
- Skip if no usable date in 3.917.3
- Propagate HoH's 3.917 to children (age <= 17) with same project start date if HMIS doesn't collect on children
- Never include time before `[date of birth]`

### Step 6: Expand dataset forwards and backwards

**6a. Forward** from `[client start date]` to `[client end date]`:
- Add all bed nights from relevant project types (non-contiguous OK)
- Include 3.917 data for Measure 1b
- Apply Step 2 negation logic

**6b. Backward** from `[client start date]`:
- Add **contiguous** bed nights going back to `[lookback stop date]` or a gap of at least one day
- Contiguous = no more than one day earlier than another date already in dataset
- Include 3.917 data backwards from project start dates
- Apply Step 2 negation logic
- Include data from closed projects

### Step 7: Compile final dataset

Each client now has a dataset of bed nights from:
- Initial selection (Step 1) - may not be contiguous
- Extended history (Step 6) - backwards must be contiguous
- Dates should not include time negated by higher-priority housing

### Step 8: Calculate `[length of time homeless]`

Count **distinct** dates in each client's dataset (each date counted once even if in multiple projects).

### Step 9: Report results

- **Column B**: Number of active clients
- **Column D**: Average of `[length of time homeless]` (2 decimal places)
- **Column G**: Median of `[length of time homeless]` (2 decimal places)

**Average**: Sum of all clients' LOT / count of distinct clients
**Median**: Sort LOT values; for odd count take middle value; for even count average the two middle values
