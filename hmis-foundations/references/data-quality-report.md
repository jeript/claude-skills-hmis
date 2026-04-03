# HMIS Data Quality Report (Glossary Q1-Q7)

## Purpose

Support HMIS Leads/System Administrators and end users in identifying data quality issues. Used in CoC grant applications, APRs, and CAPERs.

## Report Configuration

- User enters start and end date (any period from one week to multiple years)
- Filter for one, some, or all projects the user has access to
- Each section must have a details mode for identifying specific error records

## Missing Data

"Missing" = data element field value of 99, null, or blank; associated data quality field = 99; or entire form/table record is absent.

## Project Stays to Include

Use each client's **latest project stay only**. For SO ([project type] = 4) and PATH-funded SSO ([project type] = 6), only count engaged clients (with [engagement date] before [report end date]). Remove unengaged clients before determining latest stay (exception: Q1).

---

## Q1. Report Validation Table

| Row | Category | B - DQ Count | C - All Count |
|-----|----------|-------------|---------------|
| 2 | Total persons served | | |
| 3 | Adults (18+) | | |
| 4 | Children (<18) | | |
| 5 | Unknown age | | |
| 6 | Leavers | | |
| 7 | Adult leavers | | |
| 8 | Adult and HoH leavers | | |
| 9 | Stayers | | |
| 10 | Adult stayers | | |
| 11 | Veterans | | |
| 12 | Chronically homeless | | |
| 13 | Youth under 25 | | |
| 14 | Parenting youth under 25 with children | | |
| 15 | Adult heads of household | | |
| 16 | Child and unknown-age HoHs | | |
| 17 | HoHs and adult stayers 365+ days | | |

**Rules:**
- Column B = DQ universe (engaged clients only for SO/PATH-SSO; all for other types)
- Column C = all clients regardless of engagement
- Row 11 veterans: age 18+ at [project start] or [report start date] (whichever greater), [veteran status] = yes
- Row 13 youth: per Youth Households definition (age 12-24, no member known 25+)
- Row 14 parenting youth: youth with child members (age < 18, [relationship to HoH] = 2) active in range
- Row 17: any adult stayer present when HoH stay is 365+ days, even if that adult hasn't been there that long

---

## Q2. Personally Identifiable Information (PII)

| Row | Element | B - DK/PNTA | C - Missing | D - Data Issues | E - Total | F - % |
|-----|---------|-------------|-------------|-----------------|-----------|-------|
| 2 | Name (3.01) | [8 or 9] | missing | [2] | unique | /VAL.B2 |
| 3 | SSN (3.02) | [8 or 9] | missing | [rule] | unique | /VAL.B2 |
| 4 | DOB (3.03) | [rule] | missing | [rule] | unique | /VAL.B2 |
| 5 | Race/Ethnicity (3.04) | [8 or 9] | missing | | unique | /VAL.B2 |
| 6 | Overall Score | | | | unique | /VAL.B2 |

**Column categories are mutually exclusive within each row - count first match.**

**SSN Data Issues (D3):** Last 4 digits must be present and != "0000". First 3 digits (if present) != "000", "666", or 900 series. Middle 2 (if present) != "00". All 9 (if present): no repetitive or sequential patterns. No non-numeric characters.

**DOB Data Issues (D4):** (DQ = 8/9/99 with DOB not blank) OR (DQ = 2) OR DOB before 1/1/1915, after [date created], or (for adults/HoH only) on/after [project start date].

**Race/Ethnicity DK/PNTA (B5):** Include records with 8 or 9 even if also has value 1-7.

**Row 6 Overall:** Unique count of clients with ANY issue in rows 2-5.

---

## Q3. Universal Data Elements

| Row | Element | B - DK/PNTA | C - Missing | D - Data Issues | E - Total | F - % |
|-----|---------|-------------|-------------|-----------------|-----------|-------|
| 2 | Veteran Status (3.07) | [8/9] | missing | veteran & age<18 | unique | /(VAL.B3+B4) |
| 3 | Project Start (3.10) | | | overlaps/impossible | unique | /VAL.B2 |
| 4 | Relationship to HoH (3.15) | | missing | [rule] | unique | /VAL.B2 |
| 5 | Enrollment CoC (3.16) | | missing | invalid code | unique | /(VAL.B15+B16) |
| 6 | Disabling Condition (3.08) | [8/9] | missing | incongruent | unique | /VAL.B2 |

**D3 (Project Start):** Overlapping stays in same project OR exit before start date.

**D4 (Relationship to HoH):** Value not 1-5, OR no HoH in household, OR multiple HoHs.

**D5 (Enrollment CoC):** CoC code doesn't match valid HUD-defined codes per project's 2.03.

**D6 (Disabling Condition):**
```
[disabling condition] = 0
and (
    [developmental disability] or [HIV/AIDS] = 1
    or
    ([physical disability], [chronic health condition], [mental health disorder],
     or [substance use disorder] = yes AND "substantially impairs" = 1)
)
```

---

## Q4. Income and Housing Data Quality

| Row | Element | B - DK/PNTA | C - Missing | D - Data Issues | E - Total | F - % |
|-----|---------|-------------|-------------|-----------------|-----------|-------|
| 2 | Destination (3.12) | [8/9] | [30] or missing | | unique | /VAL.B6 |
| 3 | Income at Start (4.02) | [8/9] | missing | inconsistent | unique | /(VAL.B3+B16) |
| 4 | Income at Annual | [8/9] | missing | inconsistent | unique | /VAL.B17 |
| 5 | Income at Exit (4.02) | [8/9] | missing | inconsistent | unique | /VAL.B8 |

Income sources: earned (4.02.3), unemployment (4.02.4), SSI (4.02.5), SSDI (4.02.6), VA disability (4.02.7), VA pension (4.02.8), private disability (4.02.9), workers comp (4.02.10), TANF (4.02.11), GA (4.02.12), SS retirement (4.02.13), pension (4.02.14), child support (4.02.15), alimony (4.02.16), other (4.02.17).

**D3/D4/D5 Data Issues:** [income from any source] = 0 but sources identified, OR = 1 but no sources.

**C3 Missing:** No record with [information date] = [project start date] and [data collection stage] = 1, OR [income from any source] = missing at stage 1.

**C4 Missing (Annual):** No record within 30 days of anniversary with stage 5, OR income missing at that record.

**C5 Missing (Exit):** No record with [information date] = [project exit date] and stage 3, OR missing.

---

## Q5. Chronic Homelessness

| Row | Entering project type | B - Total | C - Missing institution time | D - Missing housing time | E - Approx date missing | F - # times DK/PNTA/missing | G - # months DK/PNTA/missing | H - % unable |
|-----|----------------------|-----------|------------------------------|--------------------------|--------------------------|------------------------------|-------------------------------|-------------|
| 2 | ES-EE, ES-NbN, SH, SO | | (grayed) | (grayed) | | | | |
| 3 | TH | | | | | | | |
| 4 | PH (all) | | | | | | | |
| 5 | CE | | | | | | | |
| 6 | SSO, Day Shelter, HP | | | | | | | |
| 7 | Total | sum | | | | | | |

**Applies to:** Adults and HoHs with [project start date] >= 10/1/2016.

**C:** [type of residence] 200-299 AND [length of stay] = 8/9/missing.
**D:** [type of residence] 0-99 or 300-499 or missing AND [length of stay] = 8/9/missing.
**E/F/G (Rows 3-6):** Only clients expected to answer these fields based on prior living situation logic.
**H:** Unique count missing in C-G, divided by B.

---

## Q6. Timeliness

| Row | Time for Entry | B - Start Records | C - Exit Records |
|-----|---------------|-------------------|------------------|
| 2 | < 0 days | | |
| 3 | 0 days | | |
| 4 | 1-3 days | | |
| 5 | 4-6 days | | |
| 6 | 7-10 days | | |
| 7 | 11+ days | | |

**B:** Active clients started in range, days between [project start date] and [date created].
**C:** Leavers, days between [project exit date] and [date created].
**Row 2:** Dates entered before they occurred (only zeros if all data entered on/after date).

---

## Q7. Inactive Records: Street Outreach and Emergency Shelter

| Row | Element | B - # Records | C - # Inactive | D - % Inactive |
|-----|---------|---------------|----------------|----------------|
| 2 | Contact (Adults/HoH in SO or PATH-SSO) | | | C2/B2 |
| 3 | Bed-night (All in ES-NbN) | | | C3/B3 |

**Row 2:** Project type 4 (all funding) and type 6 if PATH-funded.
**Row 3:** Project type 1.

**B2:** Adults/HoH with [project start date] < ([report end date] - 90 days) and ([project exit date] is null or > [report end date]).
**B3:** All clients same criteria.
**C2:** Latest [current living situation] was > 90 days before [report end date].
**C3:** Latest [bed-night date] was > 90 days before [report end date].
