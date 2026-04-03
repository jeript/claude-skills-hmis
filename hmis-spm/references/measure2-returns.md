# Measure 2: Returns to Homelessness

## Overview

Of clients who exited to permanent housing 2 years prior to the report range, how many returned to homelessness within 6, 12, and 24 months.

## Table Shell

| Row | Category | B - Total Exits to PH | C - Returns <6mo | E - Returns 6-12mo | G - Returns 13-24mo | I - Total Returns |
|-----|----------|-----------------------|-------------------|---------------------|---------------------|-------------------|
| 2 | Exit from SO | | | | | |
| 3 | Exit from ES | | | | | |
| 4 | Exit from TH | | | | | |
| 5 | Exit from SH | | | | | |
| 6 | Exit from PH | | | | | |
| 7 | TOTAL | sum | sum | sum | sum | sum |

Percentages in columns D, F, H, J (2 decimal places).

**Data elements:** 2.02.6, 3.10, 3.11, 3.12
**Universe:** SO (4), ES-EE (0), ES-NbN (1), TH (2), SH (8), PH (3,9,10,13) clients who exited to permanent housing 2 years prior to report range.

## Programming Instructions

**Step 1.** Select clients with exit dates 2 years prior to report range:
```
[project exit date] >= ([report start date] - 730 days)
And [project exit date] <= ([report end date] - 730 days)
```

**Step 2.** Find each client's **earliest** `[project exit date]` where `[destination]` was permanent housing (values 400-499). Use lowest `[enrollment ID]` for ties. Clients without a permanent housing exit are excluded.

**Step 3.** Report distinct clients by project type of their earliest PH exit (cells B2-B6). Cell B7 = total distinct clients regardless of project type.

**Step 4-5.** From each client's PH exit date, scan forward for re-entry into homelessness:
- Look for `[project start date]` in SO, ES, TH, SH, or PH that is:
  - In SO/ES/TH/SH: any new enrollment
  - In PH: must be >14 days after original exit AND not within another PH enrollment's date range (+1 day through +14 days after exit)
- Stop at first qualifying match

**Step 6.** Calculate days between PH exit and return. Report each client in exactly ONE column:
- C: 0-180 days
- E: 181-365 days
- G: 366-730 days
- Clients with no return: only in column B

**Steps 7-9.** Row 7 = sum of rows. Column I = sum of C+E+G. Percentages to 2 decimal places.
