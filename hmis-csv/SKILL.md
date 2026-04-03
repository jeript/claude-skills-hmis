---
name: hmis-csv
description: >
  HMIS CSV Format Specifications - data schema reference for all HMIS CSV files.
  Use this skill when working with HMIS CSV data in R, when you need to know CSV field names,
  data types, file relationships, or join keys. Use when reading/importing HMIS data exports,
  building data pipelines, or mapping data element numbers to CSV column names. This skill
  covers all HMIS CSV files: Export, Organization, Project, Funder, Client, Enrollment, Exit,
  IncomeBenefits, HealthAndDV, Disabilities, Services, CurrentLivingSituation, and more.
---

# HMIS CSV Format Specifications (FY 2026)

Source: HUD FY 2026 | Released October 2025 | Effective October 1, 2025

## File Overview and Relationships

```
Export.csv (1 record per export)
  └── Organization.csv (OrganizationID)
        └── Project.csv (ProjectID → OrganizationID)
              ├── Funder.csv (ProjectID)
              ├── ProjectCoC.csv (ProjectID)
              ├── Inventory.csv (ProjectID)
              ├── Affiliation.csv (ProjectID)
              ├── HMISParticipation.csv (ProjectID)
              └── CEParticipation.csv (ProjectID)

Client.csv (PersonalID - unique per person)
  └── Enrollment.csv (EnrollmentID → PersonalID, ProjectID, HouseholdID)
        ├── Exit.csv (EnrollmentID)
        ├── IncomeBenefits.csv (EnrollmentID, DataCollectionStage)
        ├── HealthAndDV.csv (EnrollmentID, DataCollectionStage)
        ├── EmploymentEducation.csv (EnrollmentID, DataCollectionStage)
        ├── Disabilities.csv (EnrollmentID, DataCollectionStage)
        ├── Services.csv (EnrollmentID)
        ├── CurrentLivingSituation.csv (EnrollmentID)
        ├── Assessment.csv (EnrollmentID)
        ├── Event.csv (EnrollmentID)
        └── YouthEducationStatus.csv (EnrollmentID)
```

## Key Files for HMIS Reporting

### Client.csv
**Key:** PersonalID (S32)
| DE# | CSV Name | Type | Description |
|-----|----------|------|-------------|
| 3.01.1 | FirstName | S50 | |
| 3.01.3 | LastName | S50 | |
| 3.02.1 | SSN | S9 | String, double-quoted for leading zeros |
| 3.03.1 | DOB | D | Date of birth |
| 3.03.2 | DOBDataQuality | I | List 3.03.2 |
| 4.21 | Sex | I | List 4.21 |
| 3.04.1 | AmIndAKNative, Asian, BlackAfAmerican, HispanicLatinao, MidEastNAfrican, NativeHIPacific, White | I | Each 0/1 |
| 3.04.1 | RaceNone | I | Only if all race = 0 |
| 3.07.1 | VeteranStatus | I | List 1.8 (No/Yes/DK/PNTA/Missing) |

### Enrollment.csv
**Key:** EnrollmentID (S32) → PersonalID, ProjectID, HouseholdID
| DE# | CSV Name | Type | Description |
|-----|----------|------|-------------|
| 3.10.1 | EntryDate | D | Project start date |
| 5.09.1 | HouseholdID | S32 | Links household members |
| 3.15.1 | RelationshipToHoH | I | 1=Self(HoH), 2-5=other |
| 3.16.1 | EnrollmentCoC | S6 | e.g., "XX-501" |
| 3.917.1 | LivingSituation | I | Prior living situation |
| 3.917.2 | LengthOfStay | I | Length of stay in prior |
| 3.917.2A/2B | LOSUnderThreshold | I | <90 days or <7 nights |
| 3.917.2C | PreviousStreetESSH | I | Night before on streets? |
| 3.917.3 | DateToStreetESSH | D | Approximate date started |
| 3.917.4 | TimesHomelessPastThreeYears | I | |
| 3.917.5 | MonthsHomelessPastThreeYears | I | |
| 3.08 | DisablingCondition | I | |
| 4.13.1 | DateOfEngagement | D | |
| 3.20.1 | MoveInDate | D | Housing move-in date |

### Exit.csv
**Key:** ExitID → EnrollmentID, PersonalID
| DE# | CSV Name | Type | Description |
|-----|----------|------|-------------|
| 3.11.1 | ExitDate | D | Project exit date |
| 3.12.1 | Destination | I | List 3.12.1 |
| 3.12.A | DestinationSubsidyType | I | If Destination=435 |

### IncomeBenefits.csv
**Key:** IncomeBenefitsID → EnrollmentID, PersonalID
- Has DataCollectionStage: 1=start, 2=update, 3=exit, 5=annual
- InformationDate: date of the assessment
| DE# | CSV Name | Type | Description |
|-----|----------|------|-------------|
| 4.02.1 | IncomeFromAnySource | I | 0=No, 1=Yes, 8/9=DK/PNTA |
| 4.02.2 | TotalMonthlyIncome | M | Dollar amount |
| 4.02.3 | EarnedAmount | M | Earned income amount |
| 4.02.4-17 | Individual sources | I+M | Each has Yes/No + Amount |

### Project.csv
**Key:** ProjectID → OrganizationID
| DE# | CSV Name | Type | Description |
|-----|----------|------|-------------|
| 2.02.6 | ProjectType | I | 0=ES-EE, 1=ES-NbN, 2=TH, 3=PH-PSH, 4=SO, 6=SSO, 8=SH, 9=PH-HO, 10=PH-HSO, 11=Day Shelter, 12=HP, 13=PH-RRH, 14=CE |
| 2.02.5 | ContinuumProject | I | 1=Yes |

### Funder.csv
| DE# | CSV Name | Type | Description |
|-----|----------|------|-------------|
| 2.06.1 | Funder | I | Federal partner funding source code |
| 2.06.2 | GrantID | S100 | |
| 2.06.3 | StartDate | D | Grant start |
| 2.06.4 | EndDate | D | Grant end |

## Data Types

| Type | Format |
|------|--------|
| D | YYYY-MM-DD |
| T | YYYY-MM-DD hh:mm:ss |
| I | Non-negative integer |
| M | Decimal with 2 places (may be negative) |
| M+ | Non-negative decimal with 2 places |
| S# | String, max # characters, double-quoted |

## Common List Values

**List 1.7 (No/Yes):** 0=No, 1=Yes
**List 1.8 (No/Yes/DK/PNTA/Missing):** 0=No, 1=Yes, 8=Client doesn't know, 9=Client prefers not to answer, 99=Data not collected
**DataCollectionStage (5.03):** 1=Project entry, 2=Update, 3=Project exit, 5=Annual assessment, 6=Post-exit

## Project Types (2.02.6)

| Code | Type | Abbreviation |
|------|------|-------------|
| 0 | Emergency Shelter - Entry Exit | ES-EE |
| 1 | Emergency Shelter - Night-by-Night | ES-NbN |
| 2 | Transitional Housing | TH |
| 3 | PH - Permanent Supportive Housing | PH-PSH |
| 4 | Street Outreach | SO |
| 6 | Services Only | SSO |
| 8 | Safe Haven | SH |
| 9 | PH - Housing Only | PH-HO |
| 10 | PH - Housing with Services | PH-HSO |
| 11 | Day Shelter | DS |
| 12 | Homelessness Prevention | HP |
| 13 | PH - Rapid Re-Housing | PH-RRH |
| 14 | Coordinated Entry | CE |

## R Helper Functions

The project includes `00_helper_functions.R` with lookup functions that translate HMIS numeric codes to human-readable labels. These use `dplyr::case_when()` and are available for use in R code:

| Function | Maps | Example |
|----------|------|---------|
| `living_situation(code)` | 3.12.1 destination/living situation codes | `101` → "Emergency shelter..." |
| `extended_living_situation(code)` | Groups into: Homeless, Institutional, Temporary, Permanent, Other | |
| `rental_subsidy_types(code)` | 3.12.A subsidy types | `431` → "RRH or equivalent" |
| `project_type(code)` | 2.02.6 project types (full name) | `3` → "Permanent Supportive Housing" |
| `project_type_ext(code)` | 2.02.6 grouped (ES combined, PH combined) | |
| `project_type_abb(code)` | 2.02.6 abbreviated | `3` → "PSH" |
| `rel_to_hoh(code)` | 3.15.1 relationship to HoH | `1` → "HoH" |
| `disability_type(code)` | Disability element types (4.05-4.10) | |
| `household_type(code)` | Household type codes | |
| `los_type(code)` | 3.917.2 length of stay in prior situation | |
| `timeshomeless_type(code)` | 3.917.4 times homeless past 3 years | |
| `monthshomeless_type(code)` | 3.917.5 months homeless past 3 years | |
| `event_type(code)` | CE event types | |
| `result_type(code)` | CE referral result types | |
| `funding_type(code)` | 2.06.1 federal funding sources | |
| `enhanced_yes_no_translator(code)` | 1.8 No/Yes/DK/PNTA/Missing | |

Source: `C:\Users\Jeri\Documents\R\HMIS-Skills\00_helper_functions.R`

## Full Specification

For complete field definitions for all CSV files (Disabilities.csv, HealthAndDV.csv, Services.csv, CurrentLivingSituation.csv, Assessment.csv, Event.csv, YouthEducationStatus.csv, etc.) and full list values (Appendix B), read the source document at:
`C:\Users\Jeri\Documents\R\HMIS-Skills\HMIS-CSV-Format-Specifications_2026 MD.md`
