# Measure 6: Homeless Prevention (Category 3)

## Overview

Mirrors Measures 2 and 7 but limited to **Category 3 homeless** in CoC-funded projects. Currently no CoC has been designated as high-performing, so this measure is not required. HMIS vendors not contracted with high-performing communities need not program this.

**Data elements:** 2.02.6, 3.10, 3.11, 3.12, plus system-specific Category 3 tag

### Metrics
- **6a.1/6b.1**: Returns to homelessness (mirrors Measure 2) for TH (2), SH (8), PH (3,13)
- **6c.1**: Exits to PH (mirrors 7b.1) for SH (8), TH (2), PH-RRH (13), PH-PSH (3 without move-in)
- **6c.2**: Retention in PH (mirrors 7b.2) for PH-PSH (3 with move-in)

### Programming: Reuse Measures 2 and 7 logic with Category 3 filter.

---

# Measure 7: Successful Placement and Retention

## Overview

Three metrics measuring exits to positive destinations and retention in housing.

**Data elements:** 2.02.6, 3.10, 3.11, 3.12, 3.20

## Metric 7a.1: Street Outreach Exits

**Universe:** SO (4) leavers in report range who are not active in any SO project on `[report end date]`.

### Programming Instructions

1. Select SO leavers in report range.
2. Determine latest project exit per client.
3. Reference Appendix A "SO" column. Destinations marked X = exclude client entirely.
4. Cell C2 = remaining distinct clients.
5. Cell C3 = clients with "homeless, temporary or institutional" destination (checkmark in Appendix A).
6. Cell C4 = clients with "permanent" destination (values 400-499).
7. Cell C5 = (C3+C4)/C2 * 100.00

## Metric 7b.1: Exits to Permanent Housing

**Universe:** ES-EE (0), ES-NbN (1), SH (8), TH (2), PH-RRH (13) leavers, plus PH (3,9,10) leavers WITHOUT a housing move-in date.

### Programming Instructions

1. Select leavers from applicable project types. "Leaver" = exited and NOT active in any of these types on `[report end date]`.
2. Determine latest exit per client (lowest enrollment ID for ties).
3. If latest exit from non-RRH PH (3,9,10) WITH `[housing move-in date]` <= `[report end date]`: **exclude** (goes to 7b.2 instead). Include if no move-in date.
4. Reference Appendix A by exit project type. X = exclude entirely.
5. Cell C2 = remaining distinct clients.
6. Cell C3 = clients with permanent destination (400-499).
7. Cell C4 = C3/C2 * 100.00

## Metric 7b.2: Retention of Permanent Housing

**Universe:** PH-PSH (3), PH-HO (9), PH-HSO (10) stayers and leavers with a `[housing move-in date]`. Excludes PH-RRH (13).

### Programming Instructions

1. Select stayers and leavers in PH types 3, 9, 10.
2. Exclude PH-RRH (type 13) entirely.
3. Stayers: exclude if latest stay has no `[housing move-in date]` or move-in > `[report end date]`.
4. Leavers: determine latest exit. Exclude if no move-in date (goes to 7b.1).
5. Reference Appendix A "HP & PH (all)" column. X = exclude.
6. Cell C2 = distinct stayers + leavers.
7. Cell C3 = leavers with permanent destination (400-499) + ALL stayers.
8. Cell C4 = C3/C2 * 100.00
