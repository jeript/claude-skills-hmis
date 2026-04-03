# Measure 4: Employment and Income Growth

## Overview

Six metrics measuring income changes for adults in **CoC-funded projects only**.

| Metric | Population | Income Type |
|--------|-----------|-------------|
| 4.1 | System stayers | Earned income |
| 4.2 | System stayers | Non-employment cash income |
| 4.3 | System stayers | Total income |
| 4.4 | System leavers | Earned income |
| 4.5 | System leavers | Non-employment cash income |
| 4.6 | System leavers | Total income |

**Data elements:** 2.02.6, 2.06, 3.03, 3.10, 3.11, 4.02
**Project types:** TH (2), PH-PSH (3), SH (8), PH-OTH (9), PH-HO (10), PH-RRH (13)
**Glossary Reference:** Active Clients Methods 1&2, Age, Determining Total and Earned Income

## Step 1: Select relevant projects

```
[federal partner programs and components] is 2, 3, 4, 5, 6, 43, 44, 54, 55, 56
and [grant start date] <= [report end date]
and ([grant end date] is null or [grant end date] >= [report start date])
and [project type] is 2, 3, 8, 9, 10, or 13
```

## Step 2: System Stayers (Metrics 4.1-4.3)

**2a.** Select stays active on `[report end date]`:
```
[project start date] <= [report end date]
and ([project exit date] is null or [project exit date] > [report end date])
```

**2b.** Remove stays with Length of Stay < 365 days (include time before report start).

**2c.** Keep only latest `[project start date]` per client (lowest enrollment ID for ties).

**2d.** Remove if client age < 18.

**2f.** Find **later** data point: most recent annual assessment (stage 5) where:
```
[information date] <= [report end date]
and [data collection stage] = 5
and [information date] within 30 days of anniversary month/day of earliest [project start date] for that [household ID]
```

**2g.** Find **earlier** data point: second most recent annual assessment before the later point, OR project start (stage 1) if no prior annual exists:
```
[information date] < [later assessment information date]
and ([data collection stage] = 1
     or ([data collection stage] = 5 and within 30 days of anniversary))
```

**2h.** Clients missing earlier data point: exclude entirely from universe (cell C2).
**2i.** Clients missing later data point: include in C2 but cannot count as increased (C3).

## Step 3: System Leavers (Metrics 4.4-4.6)

**3a-b.** Select exits in report range:
```
[project exit date] >= [report start date] and [project exit date] <= [report end date]
```
Client must NOT be active on `[report end date]` in any relevant project.

**3c.** Keep latest `[project start date]` per client.

**3d.** Remove if age < 18.

**3f.** Later data point = income at exit (stage 3, information date = exit date).

**3g.** Earlier data point = income at start (stage 1, information date = start date).

**3h.** Missing start income: exclude from universe. **3i.** Missing exit income: include in C2, not in C3.

## Step 4: Calculate Income Amounts

Use Glossary "Determining Total and Earned Income" for `[effective total monthly income]`.

- `[earned income]` = dollar value in 4.02.3.A (blank/null/negative = $0)
- `[non-employment cash income]` = `[effective total monthly income]` - `[earned income]`

## Step 5: Compare Earlier vs Later

- Any increase = report in cell C3
- Missing data points or null income = cannot report as increase
- Metrics 4.1/4.4: compare `[earned income]`
- Metrics 4.2/4.5: compare `[non-employment cash income]`
- Metrics 4.3/4.6: compare `[effective total monthly income]`

Cell C4 = C3/C2 * 100.00 (2 decimal places)
