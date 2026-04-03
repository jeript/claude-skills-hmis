# Appendix A: HMIS Imports and Exports

## Missing or Multiple Head of Household

Procedure for importing data with "broken" households. Follow sequence, stop when match found:

| Household Configuration | Set Head of Household to... |
|------------------------|----------------------------|
| 1 person | That person |
| Multiple with at least one adult | Oldest person aged 18+ as of [project start] |
| Multiple all age 17 or less, with one or more age 10 or less | Oldest person aged 11+ as of [project start] |
| Multiple all age 11 to 17 | Split into one household per person (each is HoH) |

## Combining Households - Matching Child HoHs with Adults

Report to identify child HoHs alongside adults previously present with the child:

1. Select all clients active in desired project(s) in date range (all enrollments, not just latest).
2. Determine age as of [project start date].
3. Identify clients age <= 17 who are HoH. This is the universe.
4. Scan child's prior enrollments for one where child wasn't HoH but was with an adult (age > 17).
5. If that adult is also in the same project with overlapping dates, report them.

---

# Appendix B: Federal Reports and Glossary Crosswalk

| Glossary Logic | CoC APR/ESG CAPER | CE APR | SPMs | LSA | CSV Specs | PATH Annual |
|---------------|-------------------|--------|------|-----|-----------|-------------|
| Active Clients | X | X | X | | X | |
| Active Clients - Method 1 | X | | X | | | |
| Active Clients - Method 2 | X | X | X | | | X |
| Active Clients - Method 3 | | | | | | |
| Active Clients - Method 4 | | | | | | |
| Active Clients - Method 5 | | | X | | | |
| Bed-night/LOS - Method 1 | X | | X | | | |
| Bed-night/LOS - Method 2 | X | | X | | | |
| Bed-night/LOS - Method 3 | X | | X | | | |
| Length of Stay in Project | X | | X | | | |
| Handling Housing Move-In Dates | X | | | | | |
| Disabling Conditions | X | | | | | |
| CH at Project Start | X | | | | | X |
| CH at Point in Time | | | | | | |
| Contact | X | | | | | |
| Age | X | X | X | | | X |
| Race and Ethnicity | X | | | | | |
| Date of Engagement | X | | | | | |
| Household Types | X | X | | | | |
| Unduplicated Household Counts | X | X | | | | |
| Unduplicated by Individual Attribute | X | X | | | | |
| Unduplicated Client Counts by HH Type | X | | | | | |
| Project Leavers | X | | X | | | |
| Project Stayers | X | | X | | | |
| Annual Assessment | X | | | | | |
| Total and Earned Income | X | | X | | | |
| HMIS Data Quality Report | X | X | | | | |
