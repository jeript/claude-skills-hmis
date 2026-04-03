# Chronic Homelessness Status

**HMIS Data Standards Fields:** 2.02, 3.08, 3.10, 3.917, 4.12, 4.05, 4.06, 4.07, 4.08, 4.09, 4.10

## Overview

The HMIS Data Standards specify that data entry in [prior living situation] requires dependent fields such that fields used in determining chronic homelessness (CH) are only answerable under certain conditions. Fields must be examined in a specific sequence to determine if a client definitely meets CH status, definitely does not, or if CH status is unknown due to incomplete data.

## Disabling Condition

The Data Standards allow auto-population of [disabling condition] with "Yes" when a client answers "Yes" to disability criteria: Physical Disability (4.05), Chronic Health Condition (4.07), Mental Health Disorder (4.09), Substance Use Disorder (4.10) where Dependent Field A = "Yes", or Developmental Disability (4.06) or HIV/AIDS (4.08) where Field 2 = "Yes".

Reporting should always count these clients as having a disabling condition. If there is incongruency between [disabling condition] and responses to disability elements, a "Yes" for any should count as having a disabling condition.

> Defining Chronically Homeless Final Rule: https://www.hudexchange.info/resource/4847/hearth-defining-chronically-homeless-final-rule/

## CH at Project Start

All adults and heads of household have a CH status at project start using their own data from that entry ([data collection stage] = 1). In PH projects, [project start date] is used (not [housing move-in date]). Process data using each row from top to bottom, left to right. Processing may stop on a particular row.

### CH at Project Start Because of Other Household Members

- Members present at household start can cause other members to be considered CH AND the household as a whole to be CH.
- CH status of household cannot change by addition of members after household start date.
- If qualifying CH member leaves, household maintains CH status only while that member was present.
- When HoH and all adults have indeterminate CH status, children carry the same CH status as HoH.
- Reporting on CH-at-start may require examining data on clients who left prior to report date range.

### CH at Project Start Flowchart

| Row | Data Standards Field | Value/Decision 1 | Value/Decision 2 | Value/Decision 3 | Value/Decision 4 |
|-----|---------------------|-------------------|-------------------|-------------------|-------------------|
| 1 | [disabling condition] (3.08) OR special needs (4.05-4.10) at stage 1 | Any = 1 (yes): CONTINUE to line 3 or 8 | [disabling condition] = 0 (no): CH = NO. STOP | = 8 or 9: CH = DK/PNTA. STOP | = 99 or null: CH = missing. STOP |
| **3.917A** | | | | | |
| 3 | [project type] (2.02.6) | If 0, 1, 4, or 8: CONTINUE line 4 | | | |
| 4 | [approximate date started] (3.917.3) | If <= [project start date] - 365 days: CH = YES. STOP | If missing or < 365 days before start: CONTINUE line 5 | | |
| 5 | [number of times on streets/ES/SH] (3.917.4) | 4+ times: CONTINUE line 6 | 1-3 times: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| 6 | [total months homeless] (3.917.5) | >= 12: CH = YES. STOP | 1-11 months: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| **3.917B** | | | | | |
| **Homeless Situation:** | | | | | |
| 9 | [prior living situation] (3.917.1) | If in 100:199: CONTINUE line 10 | | | If null: CH = missing. STOP |
| 10 | [approximate date started] (3.917.3) | If <= [project start date] - 365 days: CH = YES. STOP | If missing or < 365 days before start: CONTINUE line 11 | | |
| 11 | [number of times] (3.917.4) | 4+ times: CONTINUE line 12 | 1-3 times: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| 12 | [total months homeless] (3.917.5) | >= 12: CH = YES. STOP | 1-11 months: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| **Institutional Situation:** | | | | | |
| 14 | [prior living situation] (3.917.1) | If in 200:299: CONTINUE line 15 | | | If null: CH = missing. STOP |
| 15 | [did you stay < 90 days?] (3.917.2A) | If 1 (yes): CONTINUE line 16 | If 0 (no): CH = NO. STOP | | If null: CH = missing. STOP |
| 16 | [night before on streets/ES/SH?] (3.917.2C) | If 1 (yes): CONTINUE line 17 | If 0 (no): CH = NO. STOP | | If null: CH = missing. STOP |
| 17 | [approximate date started] (3.917.3) | If <= start - 365 days: CH = YES. STOP | If missing or < 365 days: CONTINUE line 18 | | |
| 18 | [number of times] (3.917.4) | 4+ times: CONTINUE line 19 | 1-3: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| 19 | [total months homeless] (3.917.5) | >= 12: CH = YES. STOP | 1-11: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| **Temporary/Permanent/Other:** | | | | | |
| 21 | [prior living situation] (3.917.1) | If in 0:99 or 300:499: CONTINUE line 22 | | | If null: CH = missing. STOP |
| 22 | [did you stay < 7 nights?] (3.917.2A) | If 1 (yes): CONTINUE line 23 | If 0 (no): CH = NO. STOP | | If null: CH = missing. STOP |
| 23 | [night before on streets/ES/SH?] (3.917.2C) | If 1 (yes): CONTINUE line 24 | If 0 (no): CH = NO. STOP | | If null: CH = missing. STOP |
| 24 | [approximate date started] (3.917.3) | If <= start - 365 days: CH = YES. STOP | If missing or < 365 days: CONTINUE line 25 | | |
| 25 | [number of times] (3.917.4) | 4+ times: CONTINUE line 26 | 1-3: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |
| 26 | [total months homeless] (3.917.5) | >= 12: CH = YES. STOP | 1-11: CH = NO. STOP | 8 or 9: CH = DK/PNTA. STOP | 99 or null: CH = missing. STOP |

## CH at a Point in Time

For households in SO, shelters, safe havens ([project type] = 0, 1, 4, 8). Clients in other project types use CH at project start only.

Multi-person households are CH if at least one adult or minor HoH is CH at the point-in-time date.

Each report using CH at point-in-time must specify the `[point-in-time date]`. Use only the latest data with `[information date]` <= `[point-in-time date]` and <= `[project exit date]`.

### Months Homeless Prior to Start

```
[months homeless prior to start] = months between [approximate date started] and [project start date]
```

Use "one day in a month counts the whole month" strategy. Set to 1 if no data in [approximate date started].

### Months in Project

**Entry-Exit Emergency Shelters:** Count months from `[project start date]` to lesser of `[point-in-time date]` or `[project exit date]`. Count entire month if present for any day. Subtract 1 if start date is not the first of the month (to avoid double-counting with months prior to start).

**Night-by-Night Emergency Shelters:** Use individual bed-night dates:
```
[information date] >= [project start date]
and < [project exit date]
and <= [point-in-time date]
and > month indicated in [project start date]
```

**Street Outreach:** Use [current living situation] (4.12) where location = 116, 101, 118 (streets, ES, SH):
```
[information date] >= [project start date]
and < [project exit date]
and <= [point-in-time date]
and > month indicated in [project start date]
and [location of contact] = 116, 101, 118
```

### Examples

Client enters 1/31/2023, exits 3/2/2023, approximate date started = 4/30/2022:
- [months homeless prior to start] = 10 (April 2022 - January 2023)
- [months in project] = 2 (February and March; January excluded)

NbN client: start 1/31/2023, bed-nights on 1/31 and 3/1, approximate date = 4/30/2022:
- [months homeless prior to start] = 10
- [months in project] = 1 (January excluded, no bed-night in Feb, one in March)

### CH at Point-in-Time Flowchart

| Row | Field/Variable | Decision 1 | Decision 2 | Decision 3 | Decision 4 |
|-----|---------------|------------|------------|------------|------------|
| 1 | [disabling condition] or special needs on/before PIT date | Any = 1: CONTINUE | = 0: CH = NO. STOP | = 8/9: CH = DK/PNTA. STOP | = 99/null: CH = missing. STOP |
| 2 | [months prior] + [months in project] | >= 12: CH = YES. STOP | < 12: CONTINUE line 3 | | |
| 3 | [number of times] (3.917.4) | 4+: CONTINUE line 4 | 1-3: CH = NO. STOP | 8/9: CH = DK/PNTA. STOP | 99/null: CH = missing. STOP |
| 4 | [total months homeless] (3.917.5) | >= 12: CH = YES. STOP | 1-11: CONTINUE line 5 | 8/9: CH = DK/PNTA. STOP | 99/null: CH = missing. STOP |
| 5 | [total months] + [months in project] | >= 12: CH = YES. STOP | < 12: CH = NO. STOP | | |
