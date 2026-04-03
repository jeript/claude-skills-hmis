---
name: hmis-spm
description: >
  HUD System Performance Measures programming specifications. Use this skill when implementing
  SPM logic in R for: length of time homeless (Measure 1), returns to homelessness (Measure 2),
  number of persons experiencing homelessness (Measure 3), income growth (Measure 4),
  first-time homelessness (Measure 5), homeless prevention (Measure 6), or successful
  placement/retention (Measure 7). Always invoke hmis-foundations alongside this skill for
  shared building blocks (Active Clients, Age, Income, Leavers/Stayers, Housing Move-In Dates).
---

# System Performance Measures Programming Specifications (FY 2026)

Source: HUD FY 2026 | Released October 2025 | Effective October 1, 2025

## General Report Instructions

- Reporting period: Oct 1 - Sep 30 (but should work for any user-selected range)
- `[lookback stop date]` = `[report start date]` - 7 years
- Only include projects where `[continuum project]` (2.02.5) = 1 and `[continuum code]` (2.03.1) = CoC being reported
- Include projects that may have closed before the report range when scanning history
- Propagate `[enrollment CoC]`, `[destination]`, and `[housing move-in date]` from HoH to household members via `[household ID]` and `[relationship to HoH]`
- When `[enrollment CoC]` is null and project has only one CoC code, use that as the enrollment CoC
- Use Glossary "Handling Housing Move-In Dates" logic for move-in date inheritance

### System Stayers vs System Leavers

- **System stayers**: Persons active in one or more applicable project types as of `[report end date]`
- **System leavers**: Persons who exited from applicable project types during the report period AND are NOT active in any applicable project type as of `[report end date]`

### Identifying Clients Experiencing Literal Homelessness at Project Entry

```
[project type] = 0, 1, 4, 8
Or (
    [project type] = 2, 3, 9, 10, 13
    And (
        [living situation] in (100:199)
        Or ([living situation] in (200:299) And [stay < 90 days?] = 1 And [night before streets/ES/SH?] = 1)
        Or ([living situation] in (0:99 or 300:499) And [stay < 7 nights?] = 1 And [night before streets/ES/SH?] = 1)
    )
)
```

## Measure Summary

| Measure | What It Measures | Key Project Types | Reference |
|---------|-----------------|-------------------|-----------|
| 1a/1b | Length of time persons experience homelessness | 0,1,2,3,8,9,10,13 | `references/measure1-length-of-time.md` |
| 2a/2b | Returns to homelessness within 6/12/24 months | 0,1,2,3,4,8,9,10,13 | `references/measure2-returns.md` |
| 3 | Number of persons experiencing homelessness | 0,1,2,8 | `references/measure3-5-counts.md` |
| 4 | Employment and income growth (CoC-funded only) | 2,3,8,9,10,13 | `references/measure4-income.md` |
| 5 | First-time homelessness | 0,1,2,3,8,9,10,13 | `references/measure3-5-counts.md` |
| 6 | Homeless prevention (Category 3) | 2,3,4,8,9,10,13 | `references/measure6-7-placement.md` |
| 7 | Successful placement and retention | 0,1,2,3,4,8,9,10,13 | `references/measure6-7-placement.md` |

## Glossary Dependencies

This skill depends on `hmis-foundations` for:
- Active Clients Method 5 (1+ Nights Active) - used by Measures 1 and 3
- Active Clients Methods 1 & 2 - used by Measure 4
- Age determination
- Determining Total and Earned Income
- Length of Stay calculations
- Handling Housing Move-In Dates
- Leavers and Stayers

## References

- `references/measure1-length-of-time.md` - Full 9-step algorithm for Measures 1a and 1b
- `references/measure2-returns.md` - Returns to homelessness programming instructions
- `references/measure3-5-counts.md` - Persons experiencing homelessness and first-time homeless
- `references/measure4-income.md` - Income growth for stayers and leavers
- `references/measure6-7-placement.md` - Prevention, placement, and retention
- `references/exit-destinations.md` - Appendix A destination classification matrix
