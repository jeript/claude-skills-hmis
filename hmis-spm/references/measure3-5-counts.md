# Measure 3: Number of Persons Experiencing Homelessness

## Metric 3.1 - PIT Counts (not programmed from HMIS)

Manually entered from PIT count data previously submitted. Not required to be programmed.

## Metric 3.2 - Annual HMIS Counts

**Data elements:** 2.02.6, 3.10, 3.11
**Universe:** ES-EE (0), ES-NbN (1), SH (8), TH (2)
**Glossary Reference:** Active Clients - Method 5: 1+ Nights Active

### Programming Instructions

1. Determine unduplicated counts of active clients for each project type using Method 5:
   - Cell C3: Emergency Shelter total (types 0 and 1)
   - Cell C4: Safe Haven (type 8)
   - Cell C5: Transitional Housing (type 2)
   - Cell C2: Total unduplicated across ALL applicable types

---

# Measure 5: Number of Persons Who Become Homeless for the First Time

## Overview

Of clients entering homeless projects, how many had NO prior enrollments in ES, SH, TH, or PH within 24 months.

## Metrics

| Metric | Entry Project Types | Lookback Project Types |
|--------|-------------------|----------------------|
| 5.1 | ES-EE (0), ES-NbN (1), SH (8), TH (2) | ES-EE, ES-NbN, SH, TH, AND PH |
| 5.2 | ES-EE (0), ES-NbN (1), SH (8), TH (2), PH (3,9,10,13) | Same as entry types + PH |

**Data elements:** 2.02.6, 3.10, 3.11

## Programming Instructions

**Step 1.** Select clients entering applicable project types in report range:
```
[project start date] >= [report start date] and [project start date] <= [report end date]
```

**Step 2.** Report total distinct clients in cell C2.

**Step 3.** Get earliest `[project start date]` for each client = `[client start date]`.

**Step 4.** Look backwards from `[client start date]` up to 730 days or `[lookback stop date]` (whichever is later) for prior enrollments in ES-EE, ES-NbN, SH, TH, AND PH:
```
[project start date] < [client start date]
and ([project exit date] is null or [project exit date] >= greater of ([lookback stop date], [client start date] - 730 days))
```

NOTE: For metric 5.1, the lookback includes PH even though PH is not in the entry universe.

**Step 5.** If prior enrollment found: report in cell C3 (not newly homeless). Cell C4 = C2 - C3 (newly homeless).
