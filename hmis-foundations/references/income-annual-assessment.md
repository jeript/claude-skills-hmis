# Determining Total and Earned Income

**HMIS Data Standards Fields:** 3.10, 3.11, 4.02

## Total Income Calculation

Process rules in order starting with #1. Stop when a match is found.

If HMIS auto-calculates [total income] from individual sources at data entry, use [total income] directly.

| Row | Total Monthly Income | Income from any source | At Least One Source Specified | Source Amounts >= $0 Entered? | [total income] |
|-----|---------------------|----------------------|------------------------------|-------------------------------|----------------|
| 1 | (any) AND auto-calculated | (any) | (any) | (any) | Use as calculated |
| 2 | > $0.00 | (any) | (any) | (any) | Use as entered |
| 3 | (any) | (any) | Yes | Yes | Sum individual source amounts |
| 4 | (any) | No | (any) | (any) | $0.00 |
| 5 | <= $0.00 (non-null) | Yes or NULL | (any) | (any) | $0.00 |
| 6 | (any) | DK or PNTA | (any) | (any) | null (report as "DK/PNTA") |
| 7 | (any) | (any) | (any) | (any) | null (report as "data not collected/missing") |

**Earned income** = dollar value in element 4.02.3.A. If 4.02.3 = yes (1) but no amount in 4.02.3.A, earned income = $0.

---

# Annual Assessment

Reports using Annual Assessment ([data collection stage] = 5) on stayers 365+ days require data from the specific annual assessment on the HoH's anniversary most relevant to the report date range.

## Selection Instructions

1. Use days between earliest `[project start date]` of the household's enrollment and `[report end date]` for length of stay.

2. If household has multiple HoHs active in range (first HoH exited, another became HoH), the later HoH's start date is back-dated to the first HoH's start date. Maintain anniversary timing on earliest start date.

3. Calculate HoH's **number of years** in project using the same algorithm as age calculation (using `[project start date]` and `[report end date]`). This is time-based, not service-based. NbN shelter clients with 1+ year enrollment require annual assessment regardless of bed-nights. Use "age" method due to leap years -- "365 days = 1 year" will eventually offset long-term stayer anniversaries.

4. If HoH years = 0: household does NOT yet require an annual assessment.

5. If HoH years > 0: add that number to the year of HoH's `[project start date]` = **[anniversary date]**.
   - Example: Report range 10/1/2022 - 9/30/2023, HoH start = 6/1/2021, years = 2, anniversary = 6/1/2023 (2021 + 2).

6. Use the **latest** annual assessment ([data collection stage] = 5) for each household member dated between:
   - a. 30 days **prior** to [anniversary date] (even if before [report start date])
   - b. and the **lesser** of (30 days after [anniversary date], [report end date])

7. If member's `[project start date]` > [anniversary date]: person not yet required to have annual assessment.

8. Exclude data with `[information date]` > `[report end date]`, even though legitimate annual assessment data may fall in this range for clients near end of report period.

9. Clients with no annual assessment in the relevant range (step 6) should be reported as "missing annual assessment" when that outcome is included in results. If not included, omit these clients.

10. Clients not yet required to have an annual assessment (steps 4 and 7) should be reported in appropriate row if one exists. If no row exists, completely omit them.
