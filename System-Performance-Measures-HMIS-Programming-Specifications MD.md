# System Performance Measures Programming Specifications V1.0

**U.S. Department of Housing and Urban Development**

ALIGNS WITH FY 2026 HMIS DATA STANDARDS | RELEASED OCTOBER 2025
FOR REPORTING BEGINNING OCTOBER 1, 2025

---

## Contents

- [Revision History](#revision-history)
- [Introduction](#introduction)
  - [Brief Background on Performance Measures](#brief-background-on-performance-measures)
  - [Documentation Notes](#documentation-notes)
  - [General Report Instructions](#general-report-instructions)
    - [Selecting Data for this Report](#selecting-data-for-this-report)
    - [Identifying Clients Experiencing Literal Homelessness at Project Entry](#identifying-clients-experiencing-literal-homelessness-at-project-entry)
- [Measure 1: Length of Time Persons Experience Homelessness](#measure-1-length-of-time-persons-experience-homelessness)
  - [Measure 1a](#measure-1a)
  - [Measure 1b](#measure-1b)
  - [Introduction](#measure-1-introduction)
  - [Reference Information](#measure-1-reference-information)
  - [Example](#measure-1-example)
  - [Additional test cases](#additional-test-cases)
- [Measure 2a and 2b: Returns to Homelessness](#measure-2a-and-2b-the-extent-to-which-persons-who-exit-homelessness-to-permanent-housing-destinations-return-to-homelessness-within-6-12-and-24-months)
- [Measure 3: Number of Persons Experiencing Homelessness](#measure-3-number-of-persons-experiencing-homelessness)
- [Measure 4: Employment and Income Growth](#measure-4-employment-and-income-growth-for-homeless-persons-in-coc-programfunded-projects)
- [Measure 5: Number of Persons who Become Homeless for the First Time](#measure-5-number-of-persons-who-become-homeless-for-the-first-time)
- [Measure 6: Homeless Prevention and Housing Placement (Category 3)](#measure-6-homeless-prevention-and-housing-placement-of-persons-defined-by-category-3-of-huds-homeless-definition-in-coc-program-funded-projects)
- [Measure 7: Successful Placement from Street Outreach and Retention of Permanent Housing](#measure-7-successful-placement-from-street-outreach-and-successful-placement-in-or-retention-of-permanent-housing)
- [Appendix A: Exit Destinations](#appendix-a-exit-destinations)

---

## Revision History

| Date | Version | Description |
|------|---------|-------------|
| October 2025 | 1.0 | Added references to the Handling Housing Move-In Dates section of the HMIS Standard Reporting Terminology Glossary where applicable. |

**Introduction**
- Added note linking to the "System Performance Measures: Data Submission Guide" document

**Documentation Notes**
- Added note regarding expected testing availability timeline

**Measure 1**
- Corrected row numbers on table shell
- Added note directing the reader to the example chart
- Clarified language in step 6b

**Measure 3**
- Glossary Reference changed from "Active Clients Methods 1 & 2, as appropriate by project type" to "Active Clients -- Method 5: 1+ Nights Active" to ensure Emergency Shelter - Night-by-Night enrollments only included when at least one night of residency is documented within the report period.

**Measure 4**
- Added "6 HUD: CoC -- Safe Haven" and "56 HUD: CoC Builds" to relevant [federal partner programs and components]

**Measure 7**
- Updated header in 7a1

**Appendix A: Exit Destinations**
- Updated description to include, "Undefined project types should use the 'HP & PH (all)' column when determining positive exit destinations."
- Updated column header "PH (all)" to "HP & PH (all)".

---

## Introduction

This *System Performance Measures Programming Specifications* document explains how to code the System Performance Measures report. HUD expects that vendors will have fiscal year data standards updates available for testing in HMIS by communities at least one month prior to the changes taking effect.

### Brief Background on Performance Measures

The McKinney-Vento Homeless Assistance Act was amended by the Homeless Emergency Assistance and Rapid Transition to Housing Act (HEARTH Act) in 2009. The act codified into law the Continuum of Care (CoC) planning process, a longstanding part of HUD's CoC application process to assist persons experiencing homelessness by providing greater coordination in responding to their needs. A critical aspect of the amended Act is a focus on viewing the local homeless response as a coordinated system of homeless assistance options as opposed to homeless assistance programs and funding sources that operate independently in a community. To facilitate this perspective, the Act now requires communities to measure their performance as a coordinated system, in addition to analyzing performance by specific projects or types. Therefore, the purpose of the System Performance Measures is to encourage CoCs, in coordination with Emergency Solutions Grant (ESG) Program recipients and all other homeless assistance entities in the community, to regularly measure their progress in meeting the needs of people experiencing homelessness in their community and to report this progress to HUD.

For further information regarding the System Performance Measures, please refer to the System Performance Measures: Data Submission Guide.

---

### Documentation Notes

Unless otherwise noted, these report programming instructions reference the FY 2026 HMIS Data Standards. HUD expects that vendors will have fiscal year updates available for testing by communities at least one month prior to the changes taking effect. The specifications provide guidance for programming each HMIS-generated question within the *System Performance Measures Programming Specifications*.

To accomplish this, the specifications for each question are broken up into the following components:

| Component | Explanation |
|-----------|-------------|
| **Question Name** | The full name of the question as it appears on the Report Document used to submit results. |
| **Report Table** | The full table from the System Performance Measure Table Shells, with color coding of cells to differentiate their intent. White fields (`--`): counts generated by HMIS. Grey fields (`---`): populated automatically by the reporting portal. Grey striped fields (`n`): generally not required from HMIS. |
| **Introduction** | Explains the intent of each question and highlights any items to be aware of when preparing the programming logic. |
| **Project Types** | Project types required to complete each question, translated from Report terms to HMIS Data Standards project types. |
| **HMIS Data Dictionary Fields** | Relevant data elements, fields, and response categories used to calculate a given measure or metric. |
| **Universe** | Defines the parameters of a given measure or metric by project or by client characteristic. |
| **HMIS Standard Reporting Terminology Glossary ("Glossary") Reference** | When appropriate, global methodology will be referenced to assist in programming using the most current version of the Glossary. |
| **Programming Instructions** | The steps to be taken to generate accurate Report counts including variables used, logic to select applicable client records, and detail for how to populate each count within the question. |

---

### General Report Instructions

#### Selecting Data for this Report

1. The reporting period is October 1 -- September 30. However, a CoC should be able to run the report for any period of time to review progress toward meeting the System Performance Measures.

2. The `[lookback stop date]` is the day seven years prior to the `[report start date]`. For instance, if this report is run for the period 10/1/2022 -- 9/30/2023, the `[lookback stop date]` would be 10/1/2015. Of the System Performance Measures, only Metric 4 includes data collected prior to seven years from the start of the reporting period.

3. HMIS will only be required to generate the report for one year at a time. HUD understands live data changes over time and will pre-populate prior year responses for comparisons. These cells are indicated with a gray background in the table shells.

4. Only include data from projects which are participating in the CoC for which the report is being run, defined as those projects where `[continuum project]` (element 2.02.5) = 1 and `[continuum code]` (element 2.03.1) = the CoC for which the report is being run.

5. Some sections of this report include data from projects which may not be active in the report date range (e.g., when scanning backwards in time to search for clients' history of homelessness). Be sure to include all relevant projects in the date ranges indicated in the instructions, and that such projects have the correct setting in `[continuum project]` and `[continuum code]`.

6. Some sections of this Report use the terms "system stayers" and "system leavers," building from the terms "project stayers" and "project leavers" in the HMIS Reporting Glossary.
   - **a.** System stayers are persons who were in one or more of the applicable project types listed in a specific measure as of the end of the reporting period.
   - **b.** System leavers are persons who are not system stayers and who exited from one or more of the applicable project types listed in a specific measure during the reporting period and were not enrolled in one of the applicable project types at the end of the reporting period.

7. Several Data Standards elements are required across this entire report and as such will not be listed at the start of each section in the reference table. These elements are:
   - **a.** `[Enrollment CoC]` (element 3.16) -- Used to filter clients such that only those physically present in the CoC appear in the report. Because this element is only recorded under the head of household's record, use `[household ID]` and `[relationship to head of household]` to propagate this data to other household members.
     - **i.** When `[enrollment CoC]` is null AND the associated project only has one `[continuum code]` (element 2.03.1) associated with it (i.e., the project operates in a single CoC), the `[continuum code]` of the project must be treated as the `[enrollment CoC]` for the head of household, including propagation to household members.
   - **b.** `[Personal ID]` (element 5.08) -- Used to count unique/distinct persons.
   - **c.** `[Enrollment ID]` (element 5.06) -- Used to link data together for a specific person/project stay.
   - **d.** The following elements are used in conjunction for propagating `[enrollment CoC]`, `[destination]`, and `[housing move-in date]` recorded under the head of household to other household members.
     - **i.** `[Household ID]` (element 5.09) -- Used to link household members who are together on a specific project stay.
     - **ii.** `[Relationship to head of household]` (element 3.15) -- Used to identify the head of household for a particular household enrollment. All household members "inherit" the `[enrollment CoC]` of the head of household.
     - **iii.** Note on `[housing move-in date]`: throughout this report, calculations are used that rely on each individual's `[housing move-in date]`. As `[housing move-in date]` is only required for the head of household, this data must be 'inherited' by other household members. Use the logic contained in the Handling Housing Move-In Dates section of the HMIS Standard Reporting Terminology Glossary.

---

#### Identifying Clients Experiencing Literal Homelessness at Project Entry

Certain measures specifically refer to those clients that were experiencing literal homelessness at the point of project entry. These clients should be identified using the following logic:

```
[project type] = 0, 1, 4, 8
Or (
    [project type] = 2, 3, 9, 10, 13
    And (
        [living situation] in (100:199)
        Or (
            [living situation] in (200:299)
            And [did you stay less than 90 days?] = 1
            And [on the night before did you stay on the streets, ES or SH] = 1
        )
        Or (
            [living situation] in (0:99 or 300:499)
            And [did you stay less than 7 nights?] = 1
            And [on the night before did you stay on the streets, ES or SH] = 1
        )
    )
)
```

---

## Measure 1: Length of Time Persons Experience Homelessness

### Measure 1a

| | O | A | B | C | D | E | F | G | H |
|---|---|---|---|---|---|---|---|---|---|
| **1** | | Previous FY Universe (Persons) | Current FY Universe (Persons) | Previous FY Average LOT Experiencing Homelessness | Current FY Average LOT Experiencing Homelessness | Difference | Previous FY Median LOT Experiencing Homelessness | Current FY Median LOT Experiencing Homelessness | Difference |
| **2** | Persons in ES-EE, ES-NbN, and SH | `---` | `--` | `---` | `--` | `---` | `---` | `--` | `---` |
| **3** | Persons in ES-EE, ES-NbN, SH, and TH | `---` | `--` | `---` | `--` | `---` | `---` | `--` | `---` |

### Measure 1b

| | O | A | B | C | D | E | F | G | H |
|---|---|---|---|---|---|---|---|---|---|
| **1** | | Previous FY Universe (Persons) | Current FY Universe (Persons) | Previous FY Average LOT Experiencing Homelessness | Current FY Average LOT Experiencing Homelessness | Difference | Previous FY Median LOT Experiencing Homelessness | Current FY Median LOT Experiencing Homelessness | Difference |
| **2** | Persons in ES-EE, ES-NbN, SH, and PH | `---` | `--` | `---` | `--` | `---` | `---` | `--` | `---` |
| **3** | Persons in ES-EE, ES-NbN, SH, TH, and PH | `---` | `--` | `---` | `--` | `---` | `---` | `--` | `---` |

### Measure 1 Introduction

The measures are the number of clients active in the report date range along with their average and median length of time experiencing homelessness across the relevant universe of projects. This includes time experiencing homelessness **during** the report date range as well as **prior** to the report start date.

**Measure 1a**
This measure uses each client's start, exit, and bed night dates strictly as entered in HMIS, going back no further than the `[lookback stop date]` or the client's `[date of birth]`, whichever is later.

**Measure 1b**
This measure includes data from each client's `[living situation]` (Data Standards element 3.917) response as well as time spent in permanent housing projects between `[project start date]` and `[housing move-in date]`. Measure 1b can include time experiencing homelessness prior to the `[lookback stop date]` under some circumstances but should never count a client's time experiencing homelessness before their `[date of birth]`.

Each of the two measures is divided into two rows as shown in the table above, each row being a different universe of clients as described in the detailed instructions below.

### Measure 1 Reference Information

**Relevant Data Standards Fields**

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 0, 1, 2, 3, 8, 9, 10, 13 |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |
| 3.917.3 | Prior Living Situation - Approximate date this episode of homelessness started | mm/dd/yyyy |
| 3.20 | Housing Move-In Date | mm/dd/yyyy |

**Universe:**

- **Measure 1a/Metric 1:** Emergency Shelter -- Entry Exit (Project Type 0), Emergency Shelter -- Night-by-Night (Project Type 1), and Safe Haven (Project Type 8) clients who are active in report date range.
- **Measure 1a/Metric 2:** Emergency Shelter -- Entry Exit (Project Type 0), Emergency Shelter -- Night-by-Night (Project Type 1), Safe Haven (Project Type 8), and Transitional Housing (Project Type 2) clients who are active in report date range.
- **Measure 1b/Metric 1:** Emergency Shelter -- Entry Exit (Project Type 0), Emergency Shelter -- Night-by-Night (Project Type 1), Safe Haven (Project Type 8), and Permanent Housing (Project Types 3, 9, 10, 13) clients who are active in report date range. For PH projects, only stays meeting the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria are included in time experiencing homelessness.
- **Measure 1b/Metric 2:** Emergency Shelter -- Entry Exit (Project Type 0), Emergency Shelter -- Night-by-Night (Project Type 1), Safe Haven (Project Type 8), Transitional Housing (Project Type 2), and Permanent Housing (Project Types 3, 9, 10, 13) clients who are active in report date range. For PH projects, only stays meeting the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria are included in time experiencing homelessness.

**HMIS Reporting Glossary Reference:** Active Clients -- Method 5: 1+ Nights Active

### Programming Instructions

There are two output tables required for this measure. Each of the two tables has two rows -- each with a different universe of clients and corresponding universe of data. Effectively, there is a single row of output which must be produced four different ways, each using a different universe of data, as shown below:

- **Measure 1a / Metric 1:** Persons in ES-EE, ES-NbN, and SH -- **do not include** data from element 3.917.
- **Measure 1a / Metric 2:** Persons in ES-EE, ES-NbN, SH, and TH -- **do not include** data from element 3.917.
- **Measure 1b / Metric 1:** Persons in ES-EE, ES-NbN, SH, and PH -- **include** data from element 3.917 and time between `[project start date]` and `[housing move-in date]`. Use housing move-in dates that are valid for each person as defined in the Handling Housing Move-In Dates section of the HMIS Standard Reporting Terminology Glossary.
- **Measure 1b / Metric 2:** Persons in ES-EE, ES-NbN, SH, TH, and PH -- **include** data from element 3.917 and time between `[project start date]` and `[housing move-in date]`. Use housing move-in dates that are valid for each person as defined in the Handling Housing Move-In Dates section of the HMIS Standard Reporting Terminology Glossary.

With this in mind, these instructions will not be repeated for each universe of clients. Additional steps for programming Measure 1b metrics are indicated below. When programming Measure 1a, skip these steps entirely.

Per the HMIS Data Standards, element 3.917 is only required to be collected on heads of household and adults. If the HMIS also collects this element on children and unknown-age household members, their data should be used in measure 1b. If the HMIS does not collect this element on *child* household members:

- The data from the head of household's response to 3.917 should be propagated to these children for the purposes of measure 1b.
- This applies to any household member whose age is <= 17 (calculated according to the HMIS Reporting Glossary), regardless of their relationship to the head of household, but not clients of unknown age.
- Only propagate the head of household's data to children with the same `[project start date]` as the head of household.

For both measures, do not include a client's time experiencing homelessness dated prior to their `[date of birth]`. Such data could be the result of bad data entry, or a child inheriting the head of household's responses to 3.917.

> **Measure 1b only:** Additional nights experiencing homelessness included in Measure 1b should only be included for clients meeting the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria. Instructions specific to Measure 1b will refer to this definition without repeating these instructions.

Unlike many other HMIS-generated reports, this report section uses data on clients from across multiple projects and project types combined together into a single working dataset for each client. This dataset of dates defines each client's time experiencing homelessness and is used to answer the questions for Measures 1a and 1b. The construction of each client's dataset requires multiple steps performed in sequence, detailed below.

**Neither this dataset nor the operations on it should be used to automatically alter original records in the HMIS during the execution of the report.**

**Step 1.** Select active clients across all projects of the relevant types in the CoC who have a bed night in the report range according to "Method 5: 1+ Nights Active" from the *HMIS Reporting Glossary*.

- **a.** Line 2 in Measure 1a and Measure 1b includes all clients active in Emergency Shelters -- Entry Exit ("ES-EE", project type 0), Emergency Shelters -- Night-by-Night ("ES-NbN", project type 1), and Safe Havens ("SH", project type 8).

- **b.** Line 3 in Measure 1a and Measure 1b includes all clients active in Emergency Shelters -- Entry Exit ("ES-EE", project type 0), Emergency Shelters -- Night-by-Night ("ES-NbN", project type 1), Safe Havens ("SH", project type 8), and Transitional Housing ("TH", project type 2).

- **c.** *Measure 1b:* In addition to the clients identified in a) and b) above, lines 2 and 3 in measure 1b include clients experiencing homelessness in a permanent housing project (project types 3, 9, 10, and 13) during the report year. These stays are defined as those active in any permanent housing project where all of the following are true:

  ```
  The stay meets the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria
  And (
      ( [project start date] >= [report start date] and [project start date] <= [report end date] )
      Or
      ( [housing move-in date] >= [report start date] and [housing move-in date] <= [report end date] )
      Or
      ( [housing move-in date] is null and [project exit date] >= [report start date]
        and [project exit date] <= [report end date] )
  )
  ```

- **d.** Preserve every relevant bed night which caused the client to be considered active in the date range. This dataset is the basis for additional calculations in these measures.
  - **i.** For ES-EE, SH, and TH projects, "bed night" means every separate date between the `[project start date]` up to and including the lesser of the (`[project exit date]` - 1) or `[report end date]`. The `[project exit date]` itself is not included because it does not represent a night spent in the project. If the client's `[project exit date]` is null or the `[project exit date]` is > the `[report end date]`, assume the client spent the night in the project on the `[report end date]`.
  - **ii.** For ES-NbN, "bed night" means the separate bed night records dated between the client's `[project start date]` and the lesser of the (`[project exit date]` - 1) or `[report end date]`. Bed night records dated on the client's exit date represent an error in data entry.
  - **iii.** *Measure 1b:* For PH projects where the stay meets the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria at project start (selected in step 1c above), this means every separate date between `[project start date]` up to but not including `[housing move-in date]`.
    - 1) If the `[housing move-in date]` is > `[report end date]`, include every date between `[project start date]` up to and including `[report end date]`.
    - 2) If the `[housing move-in date]` is null, include every date between `[project start date]` and the lesser of the (`[project exit date]` - 1) or `[report end date]`.

**Step 2.** Bed night dates selected in step 1 can be negated by overlapping HMIS records indicating more definitively that the client is in another type of housing "further along" in the housing process. For example, a client in emergency shelter may have actually moved into permanent housing before the `[project exit date]` from shelter. This HMIS record of permanent housing is considered more reliable than that of shelter. So, in this example the PH `[housing move-in date]` serves to truncate the client's time in shelter such that the client's `[project exit date]` from shelter is effectively changed to the `[housing move-in date]` at the PH project. Use the rules below to delete bed nights from the dataset constructed in step 1.

- **a.** For measures 1a.1 and 1b.1, time spent by clients housed in TH projects negates overlapping time spent in ES and SH projects.
  - **i.** This is because each client is expected to occupy no more than one bed per night. The HMIS record of TH stays is considered to be more reliable than that of ES or SH, so these bed nights are deduplicated to ensure that these bed nights are only counted in measures 1a.2 and 1b.2.
- **b.** *For measure 1b.1,* time spent by clients housed in TH projects negates overlapping time spent experiencing homelessness in a PH project (time after an enrollment meeting the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria but before a `[housing move-in date]`).
  - **i.** This is because clients occupying TH beds while enrolled in a PH project and searching for housing should only have those TH bed nights counted in measure 1b.2. This is a functional deduplication.
- **c.** For all measures, use clients' `[housing move-in date]` in PH projects (project types 3, 9, 10, 13) to negate overlapping time spent experiencing homelessness. Records where the `[housing move-in date]` is null (i.e., the client is not physically in permanent housing) or > the `[report end date]` should not negate the client's time experiencing homelessness.
  - **i.** This is because the HMIS record of a PH move-in date is considered more reliable than any other record type, and therefore these bed nights should be excluded from the client's homelessness history.
- **d.** After negating bed nights in the report date range, it is possible that some clients have now become irrelevant for the purposes of these measures because they have no relevant bed nights. Clients with zero bed nights in the report date range should be entirely deleted from the working dataset and all subsequent steps.

**Step 3.** Utilizing data selected in step 1 and modified in step 2, determine each client's latest homeless bed night which is >= `[report start date]` and <= `[report end date]`. This date becomes that particular client's `[client end date]`.

- **a.** This date should be no later than the end date of the report (`[client end date]` must be <= `[report end date]`), in the event a project stay extends past the `[report end date]`.
- **b.** For enrollments in entry exit emergency shelters, this date should be one day prior to the client's exit date, or the `[report end date]`, whichever is earlier. It cannot be the client's exit date since that date does not represent a bed night.
- **c.** For enrollments in night-by-night emergency shelters, this date must be based on recorded bed nights and not on the client's start or exit date.
- **d.** *Measure 1b:* Be sure not to include the `[housing move-in date]` itself, as this date does not represent a night experiencing homelessness.

**Step 4.** For each active client, create a `[client start date]` which is 365 days prior to the `[client end date]` going back no further than the `[lookback stop date]`.

- **a.** `[Client start date]` = `[client end date]` - 365 days.
- **b.** A `[client start date]` will usually be prior to the `[report start date]`.

**Step 5.** *Measure 1b:* For each relevant project stay the client's response to Data Standards element 3.917.3 -- Approximate date this episode of homelessness started -- also represents time the client has experienced homelessness. Note that this data does not affect each client's `[client start date]` which is based on the `[client end date]`. Include this data only for project stays that met the Identifying Clients Experiencing Literal Homelessness at Project Entry criteria at project start. Modify each client's dataset to include this time as follows:

- **a.** **For entry-exit based project stays**, if the `[project start date]` is >= `[lookback stop date]`, then every night from `[approximate date this episode of homelessness started]` up to and including `[project start date]` should also be considered nights experiencing homelessness, even if the response in `[approximate date this episode of homelessness started]` extends prior to `[lookback stop date]`. For example, a response in `[approximate date this episode of homelessness started]` of "2/14/2022" with a `[project start date]` of 5/15/2022 would cause every night from 2/14/2022 through and including 5/15/2022 to be included in the client's dataset of nights experiencing homelessness.

- **b.** **For night-by-night based shelter stays**, determine the client's `[earliest bed night]` dated >= `[project start date]` and <= `[project exit date]`. If `[earliest bed night]` >= `[lookback stop date]`, then every night from `[approximate date this episode of homelessness started]` up to and including `[earliest bed night]` should also be considered nights experiencing homelessness. For example, a response of "9/16/2022" with the client's earliest bed night of 11/15/2022 would effectively include bed nights for 9/16/2022, 9/17/2022, 9/18/2022... up to and including 11/15/2022. Naturally this does not mean the client was physically present at this specific shelter on these nights, but these dates are nonetheless included in the client's total time experiencing homelessness.

- **c.** **DO NOT ALTER ANY OF THE CLIENT'S ORIGINAL DATA IN THE HMIS** -- only the temporary dataset created when executing the report.

- **d.** In the event there is no response in element `[approximate date this episode of homelessness started]` or the response is not a usable date, make no change to the client's data in the temporary dataset.

**Step 6.** Using data from the relevant universe of projects for each line:

- **a.** Work *forwards* in time from `[client start date]` to `[client end date]` and add to that client's dataset all bed nights in the relevant universe of projects.
  - **i.** In this date range, the nights do not need to be contiguous in order to be included in the client's dataset.
  - **ii.** As with step 1, for entry exit projects, "bed night" means every separate date between the greater of `[project start date]` and `[client start date]`, up to and including the lesser of the (`[project exit date]` - 1) or `[client end date]`.
  - **iii.** *Measure 1b:* include additional nights experiencing homelessness based on the `[project start date]` going backwards in time as described in step 5a above.
  - **iv.** As with step 1, for night-by-night emergency shelters, "bed night" means the separate bed night records recorded between the greater of `[project start date]` and `[client start date]`, up to and including the lesser of the (`[project exit date]` - 1) or `[client end date]`.
  - **v.** *Measure 1b:* include additional nights experiencing homelessness based on the client's earliest bed night going backwards in time as described in step 5b above.
  - **vi.** Apply the same logic as described in step 2 above which may negate some nights that would otherwise be included. (see test Case 2a).

- **b.** Work *backwards* in time from `[client start date]` and add to that client's dataset all contiguous nights going backwards to either a) the `[lookback stop date]` or b) the period of at least one day when a client is not experiencing homelessness, whichever is reached first.
  - **i.** To be contiguous, a date must be no more than one day earlier than another date already in the client's dataset or the `[client start date]`.
  - **ii.** As with step 1, for entry exit projects, bed nights are nights the client actually spent in the program. The `[project exit date]` itself should not be used in determining contiguous nights. If the `[client start date]` occurs during a client's project stay, include the nights spent in the project backwards in time up to the `[project start date]`.
  - **iii.** *If including `[approximate date this episode of homelessness started]` data,* include additional nights experiencing homelessness based on the response to `[approximate date this episode of homelessness started]` up to and including the `[project start date]` as described in step 5a above. These nights are treated as contiguous with the `[project start date]`.
  - **iv.** For night-by-night shelters, use specific bed nights recorded.
  - **v.** *If including `[approximate date this episode of homelessness started]` data,* include additional nights experiencing homelessness as described in step 5b above.
  - **vi.** Apply the same logic as described in step 2 above which may negate some nights that would otherwise be included. This logic applies when including bed nights between the `[project start date]` and the `[project exit date]` as well as bed nights included because of data in element `[approximate date this episode of homelessness started]`.

- **c.** Remember to include data from projects of the relevant types which may have closed prior to the `[report start date]` but pertain to clients active during the date range. This applies both to the universe of projects directly reported in these measures as well as the universe of projects which can negate time reported in these measures (e.g., permanent housing).

**Step 7.** Now each client has a dataset of bed nights based on documented time in literally homeless projects (ES-EE, ES-NbN, and SH), and in the case of Measure 1b, additional time based on `[approximate date this episode of homelessness started]` plus time in PH between `[project start date]` and `[housing move-in date]`.

- **a.** The first set of time comes from the initial selection of clients in step 1. Dates in this range may or may not be contiguous to each other.
- **b.** The second set comes from the client's additional time experiencing homelessness constructed in step 6.
- **c.** It is possible a client's dataset of time experiencing homelessness will have overlapping dates indicating the client was experiencing homelessness in multiple projects simultaneously. For example, a client might be in both an entry exit and night-by-night shelter with overlapping nights.
- **d.** A client's dataset should *not* include time experiencing homelessness that is negated by the client's presence in a project presumed to have more accurate data. For example, a client's nights residing in TH overrule any nights indicated in an emergency shelter, and nights in TH can in turn be negated by a PH enrollment with a `[housing move-in date]`.

**Step 8.** Using each client's dataset of nights experiencing homelessness from steps 1 through 6, calculate the **distinct** number of dates experiencing homelessness for each client (i.e., count each date for a client only once even if the client was present in multiple projects on that date). This is the client's `[length of time homeless]`.

**Step 9.** For each of the four universes of data:

- **a.** Report the number of active clients (cells B2 and B3 in the table shell).
- **b.** Report the Current FY average LOT homeless (cells D2 and D3) by averaging the `[length of time homeless]` across the distinct number of clients active in the report date range. Round the number to 2 decimal places.
- **c.** Report the Current FY median LOT homeless (cells G2 and G3) by calculating the median of `[length of time homeless]` across the distinct number of clients active in the report date range. Round the number to 2 decimal places.

> **Average LOT Homeless:**
> The `[length of time homeless]` for each distinct `[personal ID]` in the current FY universe divided by the count of distinct `[personal ID]`s in the client universe.

> **Median LOT Homeless:**
> From a list of the `[length of time homeless]` for each distinct `[personal ID]` in the current universe sorted by `[length of time homeless]`:
> - For lists with an odd number of `[personal ID]`s, the `[length of time homeless]` value of the record in the list position equal to the count of distinct `[personal ID]`s divided by two, rounded up to the closest integer.
> - For lists with an even number of Personal IDs, the average of the two `[length of time homeless]` values in the list positions equal to: the count of `[personal ID]`s divided by two, and that value plus 1.

### Measure 1 Example

*(Refer to the example chart in the original PDF document for a visual timeline representation of a single client's HMIS data across multiple project stays, illustrating how Measures 1a and 1b are calculated differently.)*

Key observations from the example:

- The presence of a client in a permanent housing program negates nights recorded as experiencing homelessness as well as nights prepended based on the client's response to element `[approximate date this episode of homelessness started]`.
- Because of this negation, the `[client end date]` is two months prior to the end of the report date range, even though the client was recorded in shelter all the way through the `[report end date]`.
- The client's time in shelter stay 1 is not included unless element `[approximate date this episode of homelessness started]` data is included. Using this data makes shelter stay 1 contiguous with shelter stay 2.
- The client's residence in PH stay 2 effectively puts a stop looking backwards further than 7/2021. Because the client had moved into housing on this stay, it negates much of shelter stay 1 and introduces a break in homelessness.

### Additional test cases

The following test cases are not inclusive of all data possibilities but will help ensure correct report code.

**1. Any metric in Measure 1a**

- **a.** A client with shelter bed nights in the report date range, all of which are negated by that client's residence in permanent housing as indicated by `[housing move-in date]`. The client should be completely excluded from the report.
- **b.** A client with a `[project exit date]` in shelter which falls on the same date as that client's `[housing move-in date]` in PH. The client's shelter bed nights should be unaffected -- the `[project exit date]` never counts as a bed night.
- **c.** A client with a `[project exit date]` in shelter which falls one day after that client's `[housing move-in date]` into permanent housing. The `[project exit date]` from shelter is effectively back-dated one day such that the first day residing in PH does not count as a night experiencing homelessness.
- **d.** A client with a shelter `[project start date]` which falls in the report date range and one day prior to the client's `[project exit date]` from PH, with the client's `[housing move-in date]` set prior to that PH exit. The shelter `[project start date]` is effectively bumped forward one day to equal the permanent housing `[project exit date]`, reducing the client's count of nights experiencing homelessness by one.
- **e.** A client with a shelter `[project start date]` which falls in the report date range and also on the same day as the client's `[project exit date]` from permanent housing. The shelter `[project start date]` should be unaffected.
- **f.** A shelter stay where the `[project start date]` and `[project exit date]` are equal. This means the client did not spend a night experiencing homelessness at the shelter, so that date is not included in the client's dataset.

**2. Any metric in Measure 1b**

- **a.** A client whose `[project start date]` is 6/1/2022 and response to element `[approximate date this episode of homelessness started]` is 3/1/2022, effectively back-dating their `[project start date]` in shelter by 92 days. But 30 days before `[project start date]` the client has a `[project exit date]` from PH, with the client's `[housing move-in date]` set prior to that PH exit. The additional nights experiencing homelessness for that client is 30 instead of 90. This also creates a break in homelessness when working backwards to include contiguous bed nights.

---

## Measure 2a and 2b: The Extent to which Persons Who Exit Homelessness to Permanent Housing Destinations Return to Homelessness within 6, 12, and 24 months

| | A | B | C | D | E | F | G | H | I | J |
|---|---|---|---|---|---|---|---|---|---|---|
| **1** | | Total Number of Persons who Exited to a Permanent Housing Destination (2 Years Prior) | Number Returning to Homelessness in Less than 6 Months (0-180 days) | Percentage of Returns in Less than 6 Months (0-180 days) | Number Returning to Homelessness from 6 to 12 Months (181-365 days) | Percentage of Returns from 6 to 12 Months (181-365 days) | Number Returning to Homelessness from 13 to 24 Months (366-730 days) | Percentage of Returns from 13 to 24 Months (366-730 days) | Number of Returns in 2 Years | Percentage of Returns in 2 Years |
| **2** | Exit was from SO | `--` | `--` | =C2/B2*100 | `--` | =E2/B2*100 | `--` | =G2/B2*100 | =C2+E2+G2 | =I2/B2*100 |
| **3** | Exit was from ES | `--` | `--` | =C3/B3*100 | `--` | =E3/B3*100 | `--` | =G3/B3*100 | =C3+E3+G3 | =I3/B3*100 |
| **4** | Exit was from TH | `--` | `--` | =C4/B4*100 | `--` | =E4/B4*100 | `--` | =G4/B4*100 | =C4+E4+G4 | =I4/B4*100 |
| **5** | Exit was from SH | `--` | `--` | =C5/B5*100 | `--` | =E5/B5*100 | `--` | =G5/B5*100 | =C5+E5+G5 | =I5/B5*100 |
| **6** | Exit was from PH | `--` | `--` | =C6/B6*100 | `--` | =E6/B6*100 | `--` | =G6/B6*100 | =C6+E6+G6 | =I6/B6*100 |
| **7** | TOTAL Returns to Homelessness | =SUM(B2..B6) | =SUM(C2..C6) | =C7/B7*100 | =SUM(E2..E6) | =E7/B7*100 | =SUM(G2..G6) | =G7/B7*100 | =C7+E7+G7 | =I7/B7*100 |

### Measure 2 Introduction

This measure begins with clients who exited to a permanent housing destination in the date range two years prior to the report date range. Of those clients, the measure reports on how many of them returned to homelessness as indicated in HMIS for up to two years after their initial exit.

### Reference Information

**Relevant Data Standards Fields**

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 0, 1, 2, 3, 4, 8, 9, 10, 13 |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |
| 3.12 | Destination | Destinations in (400:499) |

**Universe:** Street Outreach (Project Type 4), Emergency Shelter -- Entry Exit (Project Type 0), Emergency Shelter -- Night-by-Night (Project Type 1), Transitional Housing (Project Type 2), Safe Haven (Project Type 8) and Permanent Housing (Project Types 3, 9, 10, and 13) clients who exited to permanent housing destinations 2 years prior to the report date range.

**HMIS Reporting Glossary Reference:** None

### Programming Instructions

These instructions define the universe of clients and data for this measure. The selection and filtering of data must be done in the sequence described below. Otherwise, data relevant for this measure might be excluded or irrelevant data might be included.

**1.** Select clients across all projects in the CoC of the relevant type (SO, ES-EE, ES-NbN, TH, SH, PH) with a project exit date 2 years prior to the report date range.

```
[project exit date] >= ( [report start date] - 730 days )
And
[project exit date] <= ( [report end date] - 730 days )
```

**2.** Of the universe of clients determined in Step 1, determine each client's earliest `[project exit date]` where the `[destination]` was permanent housing. If there are multiple exits to permanent housing on this same date, use the record with the lowest `[enrollment ID]`.

- **a.** Use `[destination]` recorded separately in each client's record.
- **b.** Note this may not necessarily be each client's earliest exit in the calculated date *without regard* to destination.
- **c.** Reference the destinations of the project exits against Appendix A. Include project exits with a permanent housing destination (values in 400-499) and exclude project exits with destinations not indicated as "permanent" (values in 0-399).
- **d.** The project exits to permanent housing become the universe of data for this measure. Filtering out exits with non-permanent destinations may naturally cause some clients to be completely excluded from the entire measure.

**3.** Using data from step 2, report the distinct number of clients who exited to permanent housing destinations according to the project type associated with the client's earliest applicable exit (cells B2-B6).

**4.** Using data from step 2, report the distinct number of clients who exited to permanent housing destinations without regard to the project type associated with the client's earliest applicable exit (cell B7).

**5.** Using data from step 2, scan forward in time beginning from each client's `[project exit date]` with a permanent housing destination to see if the client has a project start into a project indicating the client experienced homelessness again.

- **a.** Use the same universe of projects as for the initial selection of data in step 2.
- **b.** When scanning for the client's reappearance in a project, the `[project start date]` must meet the following criteria:
  - **i.** Belong to an enrollment in a street outreach, emergency shelter (either EE or NbN), transitional housing, or safe haven project
    OR
  - **ii.** Belong to an enrollment in any PH project that meets the following criteria, designed to prevent accidentally counting clients whose original project exit was intended to be a transfer to this PH project and clients who are transitioning between PH projects later on in their engagement with the system.
    - Is more than 14 days after the client's original `[project exit date]` from step 2
      AND
    - Is not contained within the date range (`[project start date]` + 1 day) through the earlier of (`[project exit date]` + 14 days) or (`[report end date]`) for *any* other PH enrollment for the same client. This date range is inclusive, meaning a qualifying reappearance cannot occur the day after any other PH enrollment or exactly 14 days after any other PH exit.

  For each client, work forwards in time beginning on the `[project exit date]` from step 2 and stop searching at the first `[project start date]` which is >= `[project exit date]` and <= `[report end date]` and meets the criteria described in 5b above.

**6.** Use the `[project start date]` found in step 5 to calculate the number of days between the client's `[project exit date]` from step 2 until the client was identified as experiencing homelessness again.

- **a.** Each client should be reported either zero (no match found) or one time across columns C, E and G in the same row the client was reported on in step 3. Clients should not be reported multiple times in the event the client returned to homelessness multiple times.
- **b.** Clients *without* a subsequent project start identifying them as experiencing homelessness are reported only in column B.
- **c.** For clients *with* a subsequent project start, also report the client in exactly one column -- C, E, or G -- according to the number of days elapsed since experiencing homelessness again.

**7.** Since each client may only be reported no more than once in columns C, E, or G, each cell in column I is simply a sum of cells in the same row.

**8.** Since each client may only be reported on one row (2, 3, 4, 5, or 6), cells B, C, E, and G in row 7 are simply a sum of the rows above.

**9.** Columns D, F, H, and J are the percentages of clients who exited to a permanent housing destination but later returned to homelessness. HMIS software should calculate these percentages to 2 decimal places.

---

## Measure 3: Number of Persons Experiencing Homelessness

### Metric 3.1 -- Change in PIT counts of sheltered and unsheltered persons experiencing homelessness

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY PIT Count | Current FY PIT Count | Difference |
| **2** | Universe: Total PIT Count of sheltered and unsheltered persons | `---` | `n` | `---` |
| **3** | Emergency Shelter Total | `---` | `n` | `---` |
| **4** | Safe Haven Total | `---` | `n` | `---` |
| **5** | Transitional Housing Total | `---` | `n` | `---` |
| **6** | Total Sheltered Count | `---` | `n` | `---` |
| **7** | Unsheltered Count | `---` | `n` | `---` |

### Metric 3.2 -- Change in annual counts of persons experiencing sheltered homelessness in HMIS

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Unduplicated Total sheltered persons | `--` | `--` | `--` |
| **3** | Emergency Shelter Total | `--` | `--` | `--` |
| **4** | Safe Haven Total | `--` | `--` | `--` |
| **5** | Transitional Housing Total | `--` | `--` | `--` |

### Measure 3 Introduction

This measure is divided in two tables:

1. **Metric 3.1** - Counts of clients using PIT count data. This data should be manually entered from the appropriate PIT count data previously submitted. Due to ever-changing data, it is often difficult or impossible to run the same query months later and return the same results. Thus, this metric is not intended to be programmed into the HMIS as part of the System Performance Measures report.

2. **Metric 3.2** - Counts of clients using HMIS data. Using HMIS data, determine the unduplicated counts of active clients for each of the project types throughout the reporting period: Emergency Shelter, Safe Haven, Transitional Housing, and Total unduplicated across all applicable project types.

### Reference Information

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 0, 1, 2, 8 |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |

**Universe:**
- Metric 3.1: Clients counted as sheltered and unsheltered in the PIT count conducted in report date range.
- Metric 3.2: Emergency Shelter -- Entry Exit (Project Type 0), Emergency Shelter -- Night-by-Night (Project Type 1), Safe Haven (Project Type 8), and Transitional Housing (Project Type 2) clients who are active in report date range.

**HMIS Reporting Glossary Reference:** Active Clients -- Method 5: 1+ Nights Active

### Programming Instructions

Only Metric 3.2 requires programming in HMIS.

1. Determine the unduplicated counts of active clients for each of the project types throughout the reporting period using the active clients methodology described in the HMIS Reporting Glossary.
   - **a.** Emergency Shelter (cell C3). Be sure to use the active client method appropriate for the project type.
   - **b.** Safe Haven (cell C4).
   - **c.** Transitional Housing (cell C5).
   - **d.** Total unduplicated across all applicable project types (cell C2).

---

## Measure 4: Employment and Income Growth for Homeless Persons in CoC Program-Funded Projects

### Metric 4.1 -- Change in earned income for adult system stayers during the reporting period

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Number of adults (system stayers) | `---` | `--` | `---` |
| **3** | Number of adults with increased earned income | `---` | `--` | `---` |
| **4** | Percentage of adults who increased earned income | `---` | =C3/C2*100.00 | `---` |

### Metric 4.2 -- Change in non-employment cash income for adult system stayers during the reporting period

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Number of adults (system stayers) | `---` | `--` | `---` |
| **3** | Number of adults with increased non-employment cash income | `---` | `--` | `---` |
| **4** | Percentage of adults who increased non-employment cash income | `---` | =C3/C2*100.00 | `---` |

### Metric 4.3 -- Change in total income for adult system stayers during the reporting period

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Number of adults (system stayers) | `---` | `--` | `---` |
| **3** | Number of adults with increased total income | `---` | `--` | `---` |
| **4** | Percentage of adults who increased total income | `---` | =C3/C2*100.00 | `---` |

### Metric 4.4 -- Change in earned income for adult system leavers

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Number of adults who exited (system leavers) | `---` | `--` | `---` |
| **3** | Number of adults who exited with increased earned income | `---` | `--` | `---` |
| **4** | Percentage of adults who increased earned income | `---` | =C3/C2*100.00 | `---` |

### Metric 4.5 -- Change in non-employment cash income for adult system leavers

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Number of adults who exited (system leavers) | `---` | `--` | `---` |
| **3** | Number of adults who exited with increased non-employment cash income | `---` | `--` | `---` |
| **4** | Percentage of adults who increased non-employment cash income | `---` | =C3/C2*100.00 | `---` |

### Metric 4.6 -- Change in total income for adult system leavers

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Number of adults who exited (system leavers) | `---` | `--` | `---` |
| **3** | Number of adults who exited with increased total income | `---` | `--` | `---` |
| **4** | Percentage of adults who increased total income | `---` | =C3/C2*100.00 | `---` |

### Measure 4 Introduction

This measure is divided into six tables as shown above. The project types reported in these metrics are the same for all metrics, but the type of income and universe of clients differs. Equally important, the projects reported on are limited to CoC-funded projects, and only adult clients are included.

**For system stayers (metrics 4.1, 4.2, and 4.3):**

1. A "system stayer" is an adult client active in any one or more of the relevant projects as of the `[report end date]`.
2. The client must have at least 365 days in latest stay to be included in this measure.
3. Use data from each system stayer's latest assessment up to or on the `[report end date]` and compare this data to the client's most recent assessment prior to that one. This may be either an annual assessment or project start data, whichever is later.

**For system leavers (metrics 4.4, 4.5, and 4.6):**

1. A "system leaver" is any adult client who has exited from one or more of the relevant projects between `[report start date]` and `[report end date]` and who is not active in any of the relevant projects as of the `[report end date]`. Use data from each system leaver's income assessment at project exit and compare this data to the client's income assessment at project start.

### Measure 4 Reference Information

**Relevant Data Standards Fields**

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 2, 3, 8, 9, 10, 13 |
| 2.06 | Federal Partner Funding Sources | Federal Partner Programs and Components, Grant Start Date, Grant End Date |
| 3.03 | Date of Birth | mm/dd/yyyy |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |
| 4.02 | Income and Sources | Earned Income and all other sources |

**Universe:** Include projects funded with specific HUD: CoC funding sources (see instructions below).

**HMIS Reporting Glossary Reference:** Active Clients, Methods 1 & 2, as appropriate by project type, Date of Birth / Age, Determining Total and Earned Income

### Measure 4 Programming Instructions

**1.** The selection of relevant projects is critical to this measure. Build the universe of relevant projects for this measure as follows:

```
Select projects where
[federal partner programs and components] is 2, 3, 4, 5, 6, 43, 44, 54, 55, 56
and
[grant start date] <= [report end date]
and
( [grant end date] is null or [grant end date] >= [report start date] )
and
[project type] is 2, 3, 8, 9, 10, or 13
```

**2.** For metrics 4.1, 4.2 and 4.3 (adult system stayers), determine the relevant project stay and Income and Sources records attached to that stay for each client.

- **a.** Select each client's project stays in which the client was active on the `[report end date]` in any of the relevant projects as determined in step 1. Since the universe of relevant projects may be large, it is not unusual for a client to be active in more than one project simultaneously.
  ```
  [project start date] <= [report end date]
  and
  ( [project exit date] is null or [project exit date] > [report end date] )
  ```
- **b.** For each client, remove any stays where the `[length of stay]` is < 365 days. Use the calculation of `[length of stay]` as described in the HMIS Reporting Glossary, including time in the project prior to the `[report start date]`.
- **c.** For each client, remove all but the stay with the latest `[project start date]`. If there are multiple project enrollments starting on the same date, use the record with the lowest `[enrollment ID]`.
- **d.** For each client, remove the stay if the client's age for that project stay (as calculated according to the HMIS Reporting Glossary) is less than 18.
- **e.** The application of these filters will result in a dataset of project stays with no more than one stay per client. It is expected that some clients initially selected in step a. may have been removed completely from the dataset and from the entire measure.
- **f.** For each client, determine the most recent Income and Sources record with a `[data collection stage]` of annual assessment (5) attached to the selected project stay where the annual assessment is within the expected timeframe for annual assessment completion. This becomes the client's *later* data point for comparing income. It is necessary to determine this data point before determining the earlier point of comparison.
  ```
  [information date] <= [report end date]
  and
  [data collection stage] = 5
  and
  [information date] is within 30 days before and after the month and day of the earliest
  [project start date] associated with the same [household ID]
  ```
- **g.** For each client, determine the second most recent Income and Sources annual assessment attached to the selected project stay. This is the annual assessment that preceded the *later* data point identified in step f and was within the expected timeframe for annual assessment completion. If the client has no valid annual assessment records prior to the later data point, use the client's Income and Sources at project start. This becomes the client's *earlier* data point for comparing income. Please note that for long-term permanent housing clients, the `[project start date]` may be before the `[lookback stop date]`. This is the only exception when data collected before the `[lookback stop date]` may be required. This is the most recent record meeting the following conditions:
  ```
  [information date] < [information date of annual assessment from step 2f]
  and
  ( [data collection stage] = 1
    or
    ( [data collection stage] = 5
      and
      [information date] is within 30 days before and after the month and day of
      the earliest [project start date] associated with the same [household ID]
    )
  )
  ```
- **h.** Clients who are completely missing their earlier data point (i.e., clients missing a record in "Income and Sources" at project start) are excluded entirely from the universe of clients. Report the total number of system stayers, excluding these clients, in cell C2.
- **i.** Clients who have been in the project 365 or more days but who are completely missing their *later* data point are included in the universe of clients (cell C2) but cannot be counted as having an increase in any type of income (cell C3).

**3.** For metrics 4.4, 4.5 and 4.6 (adult system leavers), determine the relevant project stay and Income and Sources records attached to that stay for each client.

- **a.** Select each client's project stays in which the client exited during the report date range in any of the relevant projects as determined in step 1. Since the universe of relevant projects may be large, it is not unusual for a client to have exited from more than one project in the date range. This filter will cause some clients who are leavers to be completely excluded from metrics 4.4, 4.5 and 4.6 because they are stayers in other projects, even if those stays are less than 365 days.
- **b.**
  ```
  [project exit date] >= [report start date]
  and
  [project exit date] <= [report end date]
  ```
- **c.** The client is not active on the `[report end date]` in any of the relevant projects (i.e., not identified as a "stayer" in step 2a above). For each client, remove all but the stay with the latest `[project start date]`.
- **d.** For each client, remove the stay if the client's age for that project stay (as calculated according to the HMIS Reporting Glossary) is less than 18.
- **e.** Similar to the filtering performed on system stayers, these filters will result in a dataset of project stays with no more than one stay per client.
- **f.** For each client, determine the client's income assessment record at project exit. This becomes the client's *later* data point for comparing income.
  ```
  [information date] = [project exit date]
  and
  [data collection stage] = 3
  ```
- **g.** For each client, determine the client's income assessment record at project start. This becomes the client's *earlier* data point for comparing income. Please note that for long-term permanent housing clients, the `[project start date]` may be before the `[lookback stop date]`. This is the only exception when data collected before the `[lookback stop date]` may be required.
  ```
  [information date] = [project start date]
  and
  [data collection stage] = 1
  ```
- **h.** Clients who are completely missing their Income and Sources at project start are excluded entirely from the universe of clients. Report the total number of system leavers, excluding these clients, in cell C2.
- **i.** Clients missing their Income and Sources at exit are included in the universe of clients (cell C2) but cannot be counted as having an increase in any type of income (cells C3 and C4).

**4.** Determine income dollar amounts attached to each data point.

- **a.** Once specific income records are selected for the two comparison points for each client, follow the "Determining Total and Earned Income" logic from the HMIS Reporting Glossary to calculate the client's `[effective total monthly income]` based on data in the record. This number is used directly in Metric 4.5 and 4.6 and is also used in calculating the client's non-employment income in Metrics 4.2 and 4.4.
- **b.** The `[earned income]` for each income record is simply the dollar value in element [4.02.3.A].
  - **i.** A "yes" or "no" in element [4.02.3] has no bearing on `[earned income]`; it is strictly based on the dollar amount in element [4.02.3.A].
  - **ii.** A value of blank, null, or less than zero in [4.02.3.A] means the client has $0 in `[earned income]`.
  - **iii.** A value > 0 in [4.02.3.A] means the client has that dollar amount in `[earned income]`.
- **c.** The `[non-employment cash income]` for each income record is simply the `[effective total monthly income]` minus `[earned income]`. This logic is identical to the calculation of "other income" in Q18 on the CoC APR/ESG CAPER.

**5.** For each metric, compare the earlier data point against the later data point using the relevant income dollar amount as determined in step 4.

- **a.** Any increase in the relevant dollar amount from earlier to later data points causes the client to be reported in cell C3.
- **b.** Clients who have one or both data points completely missing, or with a null `[effective total monthly income]`, cannot be reported as having an increase of any type of income.
- **c.** Metrics 4.1 and 4.4: Report clients who increased `[earned income]` from earlier to later data points.
- **d.** Metrics 4.2 and 4.5: Report clients who increased `[non-employment cash income]` from earlier to later data points.
- **e.** Metrics 4.3 and 4.6: Report clients who increased `[effective total monthly income]` from earlier to later data points.

**6.** Cell C4 = C3/C2 * 100.00 (a percentage to two decimal places).

---

## Measure 5: Number of Persons who Become Homeless for the First Time

### Metric 5.1 -- Change in the number of persons entering ES, SH, and TH projects with no prior enrollments in HMIS

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Person with entries into ES-EE, ES-NbN, SH, or TH during the reporting period. | `---` | `--` | `---` |
| **3** | Of persons above, count those who were in ES-EE, ES-NbN, SH, TH, or any PH within 24 months prior to their start during the reporting year. | `---` | `--` | `---` |
| **4** | Of persons above, count those who did not have entries in ES-EE, ES-NbN, SH, TH or PH in the previous 24 months. (i.e. number of persons experiencing homelessness for the first time) | `---` | =C2-C3 | `---` |

### Metric 5.2 -- Change in the number of persons entering ES, SH, TH, and PH projects with no prior enrollments in HMIS

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | Difference |
| **2** | Universe: Person with entries into ES-EE, ES-NbN, SH, TH or PH during the reporting period. | `---` | `--` | `---` |
| **3** | Of persons above, count those who were in ES-EE, ES-NbN, SH, TH, or any PH within 24 months prior to their start during the reporting year. | `---` | `--` | `---` |
| **4** | Of persons above, count those who did not have entries in ES-EE, ES-NbN, SH, TH or PH in the previous 24 months. (i.e. Number of persons experiencing homelessness for the first time.) | `---` | =C2-C3 | `---` |

### Measure 5 Introduction

This measure is divided in two tables:

1. **Metric 5.1** -- Clients entering in Emergency Shelter -- Entry Exit, Emergency Shelter -- Night-by-Night, Safe Haven, and Transitional Housing.
2. **Metric 5.2** -- Clients entering in Emergency Shelter -- Entry Exit, Emergency Shelter -- Night-by-Night, Safe Haven, Transitional Housing, and Permanent Housing.

For both measures, start with the client's earliest start date in any of the relevant project types during the report date range. Working backwards in time, determine if the client was active in any shelter (ES-EE, ES-NbN, SH, or TH) or housing project within 24 months prior to their earliest start date. If so, then the client is not newly homeless (cell C3). If not, then the client is newly homeless (cell C4).

### Measure 5 Reference Information

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 0, 1, 2, 3, 8, 9, 10, 13 |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |

**Universe:**
- Metric 5.1 -- Clients entering in ES-EE (0), ES-NbN (1), SH (8), and TH (2).
- Metric 5.2 -- Clients entering in ES-EE (0), ES-NbN (1), SH (8), TH (2), and PH (3, 9, 10, 13).

**HMIS Reporting Glossary Reference:** None

### Measure 5 Programming Instructions

There are two output tables required for this measure, each with a different universe of clients. The programming methodologies are identical except for the addition of PH projects into the initial universe of clients for Metric 5.2.

**1.** Select clients entering any of the applicable project types in the report date range.

```
[project start date] >= [report start date] and [project start date] <= [report end date]
```

**2.** Report the total distinct number of clients in cell C2.

**3.** Of the project stay records selected in step 1, get the earliest `[project start date]` for each client. This becomes the `[client start date]`.

```
[client start date] >= [report start date] and [client start date] <= [report end date]
```

**4.** Working backwards in time using data from ES-EE, ES-NbN, SH, TH *and PH* projects, determine if the client was active in any project on or prior to the `[client start date]`. Look backwards up to (`[project start date]` - 730 days) or the `[lookback stop date]`, whichever is later.

- **a.** In the case of metric 5.1, the projects scanned for client presence is different from the projects used in the initial selection of data in step 1. For metric 5.2, the projects scanned for client presence is the same.
- **b.** Search for project stays where:
  ```
  [project start date] < [client start date]
  and [project exit date] is null or [project exit date] >= greater of
      ( [lookback stop date] and ( [client start date] - 730 days ) )
  ```
- **c.** If a match is found, report the client in cell C3. Report the client no more than once regardless of how many prior project stays were found for the client.

**5.** Because each client may be counted no more than once in cells C2 and C3, cell C4 is a simple formula indicated in the table shell above.

---

## Measure 6: Homeless Prevention and Housing Placement of Persons Defined by Category 3 of HUD's Homeless Definition in CoC Program-funded Projects

### Metrics 6a.1 and 6b.1 -- Returns to ES, SH, TH, and PH projects after exits to permanent housing destinations within 6 and 12 months (and 24 months in a separate calculation)

*(Same table structure as Measure 2, but rows 2 (SO) and 3 (ES) are grayed out. Only rows 4 (TH), 5 (SH), 6 (PH), and 7 (TOTAL) are applicable.)*

### Metric 6c.1 -- Change in exits to permanent housing destinations

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | % Difference |
| **2** | Universe: Cat. 3 Persons in SH, TH and PH-RRH who exited, plus persons in other PH projects who exited without moving into housing | `---` | `n` | `---` |
| **3** | Of the persons above, those who exited to permanent destinations | `---` | `n` | `---` |
| **4** | % Successful exits | `---` | =C3/C2*100.00 | `---` |

### Metric 6c.2 -- Change in exit to or retention of permanent housing

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | % Difference |
| **2** | Universe: Cat. 3 Persons in all PH projects except PH-RRH who exited after moving into housing, or who moved into housing and remained in the PH project | `---` | `n` | `---` |
| **3** | Of persons above, count those who remained in PH-PSH projects and those who exited to permanent housing destinations | `---` | `n` | `---` |
| **4** | % Successful exits/retention | `---` | =C3/C2*100.00 | `---` |

### Measure 6 Introduction

- **Metrics 6a.1 and 6b.1** mirror Measure 2 but with a universe of Category 3 persons.
- **Metric 6c.1** mirrors Measure 7b.1 but with a universe of Category 3 SH, TH, PH-RRH, and PH (without a housing move-in date) system leavers in the current reporting year.
- **Metric 6c.2** mirrors Measure 7b.2 but with a universe of Category 3 PH-PSH system stayers and leavers in the current reporting year, with a housing move-in date.

### Measure 6 Reference Information

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 2, 3, 4, 8, 9, 10, 13 |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |
| 3.12 | Destination | Destinations in (400:499) |
| n/a | System-specific tag for identifying projects serving Category 3 homeless | Dependent on specific HMIS product. No current HMIS Data Standards indicator. |

**Universe:** All metrics are limited to all clients in projects serving Category 3 homeless, in addition to the filters below.

- **Metrics 6a.1 and 6b.1:** Transitional Housing (Project Type 2), Safe Haven (Project Type 8) and PH-PSH and PH-RRH (Project Types 3 and 13) clients who exited to permanent housing destinations 2 years prior to the report date range.
- **Metric 6c.1:** Safe Haven (8), Transitional Housing (2), PH-RRH (13), and PH-PSH (3, without a housing move-in date) clients who exited during the report range.
- **Metric 6c.2:** PH-PSH (Project Type 3, with a housing move-in date) clients who are active in the report range.

**HMIS Reporting Glossary Reference:** None

### Measure 6 Programming Instructions

Re-use the same programming instructions from Measures 2 and 7 as described above. The universe of relevant projects varies for this measure as this measure is required only for CoC-program-funded projects in communities approved by HUD to serve persons under Category 3 of HUD's definition of homelessness.*

> *CoC-program-funded projects can only serve persons under Category 3 of HUD's definition of homelessness if they have been identified by HUD as a high-performing community. HUD has not designated any high performing communities as of July 2023; therefore, no CoC-program-funded projects, to date, have been approved to serve persons under Category 3 and no CoC is required to report on this metric. HMIS vendors not actively contracted with any high-performing communities are not required to program this measure.

---

## Measure 7: Successful Placement from Street Outreach and Successful Placement in or Retention of Permanent Housing

### Metric 7a.1 -- Change in exits to permanent housing destinations

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | % Difference |
| **2** | Universe: Persons who exit Street Outreach | `---` | `--` | `---` |
| **3** | Of persons above, those who exited to specific homeless, temporary, and institutional destinations | `---` | `--` | `---` |
| **4** | Of the persons above, those who exited to permanent housing destinations | `---` | `--` | `---` |
| **5** | % Successful exits | `---` | =(C3+C4)/C2*100.00 | `---` |

### Metric 7b.1 -- Change in exits to permanent housing destinations

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | % Difference |
| **2** | Universe: Persons in ES-EE, ES-NbN, SH, TH, and PH-RRH who exited, plus persons in other PH projects who exited without moving into housing | `---` | `--` | `---` |
| **3** | Of the persons above, those who exited to permanent housing destinations | `---` | `--` | `---` |
| **4** | % Successful exits | `---` | =C3/C2*100.00 | `---` |

### Metric 7b.2 -- Change in exit to or retention of permanent housing

| | A | B | C | D |
|---|---|---|---|---|
| **1** | | Previous FY | Current FY | % Difference |
| **2** | Universe: Persons in all PH projects except PH-RRH who exited after moving into housing, or who moved into housing and remained in the PH project | `---` | `--` | `---` |
| **3** | Of persons above, those who remained in applicable PH projects and those who exited to permanent housing destinations | `---` | `--` | `---` |
| **4** | % Successful exits/retention | `---` | =C3/C2*100.00 | `---` |

### Measure 7 Introduction

This measure is divided in three tables:

1. **Metric 7a.1** -- Counts leavers who exited Street Outreach (SO) during the report date range and how many of those exited to an acceptable destination.
2. **Metric 7b.1** -- Counts leavers who exited ES-EE, ES-NbN, SH, TH, PH-RRH, and PH (for any non-RRH PH type, must be without moving into housing) during the report range and how many of those exited to permanent housing destinations.
3. **Metric 7b.2** -- Counts stayers and leavers with a housing move-in date (as defined by the Handling Housing Move-In Dates section of the HMIS Standard Reporting Terminology Glossary) in all PH projects except PH-RRH and how many of those were stayers or leavers who exited to permanent housing destinations.

### Measure 7 Reference Information

| Field No | Field Name | Relevant Data |
|----------|-----------|---------------|
| 2.02.6 | Project Type | 0, 1, 2, 3, 4, 8, 9, 10, 13 |
| 3.10 | Project Start Date | mm/dd/yyyy |
| 3.11 | Project Exit Date | mm/dd/yyyy |
| 3.12 | Destination | Selected destinations as described in Appendix A |
| 3.20 | Housing Move-In Date | mm/dd/yyyy |

**Universe:**
- Metric 7a.1: Street Outreach (Project Type 4) clients who exited during the report range.
- Metric 7b.1: ES-EE (0), ES-NbN (1), SH (8), TH (2), and PH-RRH (13) clients who exited during the report range, plus other PH (project types 3, 9, 10) clients who exited without moving into housing.
- Metric 7b.2: PH-PSH (3), PH-Housing Only (9), and PH-Housing Services Only (10) clients who are active in the report range with a housing move-in date.

**HMIS Reporting Glossary Reference:** None

### Measure 7 Programming Instructions

There are three output tables for this measure -- each with a different universe of clients and corresponding universe of data. The instructions will refer to the project type-destination matrix from Appendix A, which classifies destinations as either "acceptable" (included in cell C3 and the numerator of cell C4 for each metric) or as potentially causing a client to be excluded entirely from the measure, depending on the exiting project type.

#### Metric 7a.1

**1.** Select leavers across all SO projects in the report date range. A "leaver" in this metric means the client must have exited an SO project in the report date range and was not active in that or any other SO project as of the `[report end date]`.

**2.** Of the project exits selected in step 1, determine the latest project exit for each client.

**3.** Reference the destinations of the project exits against Appendix A (row headers) and the "SO" column. Destinations indicated with an X cause leavers with those destinations to be completely excluded from the entire measure (all of column C).

**4.** Of the remaining leavers, report the distinct number of clients in cell C2.

**5.** Of the remaining leavers, report the distinct number of clients whose destination is "homeless, temporary or institutional" as indicated with a checkmark in Appendix A in cell C3.

**6.** Of the remaining leavers, report the distinct number of clients whose destination is "permanent" as indicated with a checkmark in Appendix A (values in 400:499) in cell C4.

**7.** Because each client is reported only once in cell C2 and no more than once in cells C3 and C4, cell C5 is a simple formula indicated in the table shell. The HMIS should generate this number to 2 decimal places.

#### Metric 7b.1

**1.** Select leavers across all ES-EE, ES-NbN, SH, TH, PH-RRH, and PH projects in the report date range. A "leaver" in this metric means the client must have exited from a project of one of the given types in the report date range and was not active in that or any other project among the given types as of the `[report end date]`.

**2.** Of the project exits selected in step 1, determine the latest project exit for each client. If there are multiple project exits with the same date, use the record with the lowest `[enrollment ID]`.

**3.** If the latest exit was from a non-RRH PH project (types 3, 9 and 10) where the `[housing move-in date]` is <= `[report end date]`, exclude the client completely from this measure (the client will be reported in measure 7b.2). If the latest exit was from project types 3, 9 and 10 and there is no `[housing move-in date]` for that stay, the client is included in this measure.

**4.** Reference the destinations of the project exits against Appendix A (row headers) using the project type from which the exit occurred (column headers). Destinations indicated with an X cause leavers with those destinations to be completely excluded from the entire measure (all of column C).

**5.** Of the remaining leavers, report the distinct number of clients in cell C2.

**6.** Of the remaining leavers, report the distinct number of clients whose destination is "permanent" as indicated with a checkmark in Appendix A (values in 400:499) in cell C3.

**7.** Because each client is reported only once in cell C2 and no more than once in cell C3, cell C4 is a simple formula indicated in the table shell. The HMIS should generate these numbers to 2 decimal places.

#### Metric 7b.2

**1.** Select stayers and leavers across selected PH projects (types 3, 9 and 10). A "leaver" in this metric means the client must have exited from a project of one of the given types in the report date range and was not active in that or any other project among the given types as of the `[report end date]`.

**2.** Data from PH-RRH projects is completely excluded from this metric.

**3.** Of the stayers selected in step 1, if the stay with the latest project start date has no `[housing move-in date]`, or the `[housing move-in date]` is > `[report end date]`, exclude the client completely from this measure.

**4.** Of the leavers selected in step 1, determine the latest project exit for each client. If there is no `[housing move-in date]` for that stay, the client is completely excluded from this measure (the client will be reported in 7b.1).

**5.** Reference the destinations of the project exits against Appendix A (row headers) and the "HP & PH (all)" column. Destinations indicated with an X cause leavers with those destinations to be completely excluded from the entire measure (all of column C).

**6.** Of the selected clients, report the distinct number of stayers and leavers in cell C2.

**7.** Of the selected clients, report the distinct number of leavers whose destination is "permanent" as indicated with a checkmark in Appendix A (values in 400:499) + the distinct number of stayers in cell C3.

**8.** Because each client is reported only once in cell C2 and no more than once in cell C3, cell C4 is a simple formula indicated in the table shell. The HMIS should generate these numbers to 2 decimal places.

---

## Appendix A: Exit Destinations

Destinations indicated with an **X** cause leavers with those destinations to be completely excluded from the entire measure universe. Clients whose destination is indicated with a **checkmark** will be included in the measure universe. Undefined project types should use the "HP & PH (all)" column when determining positive exit destinations.

### Homeless Situations (100-199)

| Code | Exit Destination | SO | ES-EE | ES-NbN | TH | HP & PH (all) | SH | SSO |
|------|-----------------|:--:|:-----:|:------:|:--:|:-------------:|:--:|:---:|
| 101 | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter | checkmark | | | | | | |
| 116 | Place not meant for habitation | | | | | | | |
| 118 | Safe Haven | checkmark | | | | | | |

### Institutional Situations (200-299)

| Code | Exit Destination | SO | ES-EE | ES-NbN | TH | HP & PH (all) | SH | SSO |
|------|-----------------|:--:|:-----:|:------:|:--:|:-------------:|:--:|:---:|
| 206 | Hospital or other residential non-psychiatric medical facility | X | X | X | X | X | X | X |
| 215 | Foster care home or foster care group home | checkmark | X | X | X | X | X | X |
| 207 | Jail, prison, or juvenile detention facility | | | | | | | |
| 204 | Psychiatric hospital or other psychiatric facility | checkmark | | | | | | |
| 205 | Substance abuse treatment facility or detox center | checkmark | | | | | | |
| 225 | Long-term care facility or nursing home | checkmark | X | X | X | X | X | X |

### Temporary Housing Situations (300-399)

| Code | Exit Destination | SO | ES-EE | ES-NbN | TH | HP & PH (all) | SH | SSO |
|------|-----------------|:--:|:-----:|:------:|:--:|:-------------:|:--:|:---:|
| 329 | Residential project or halfway house with no homeless criteria | X | | | | | | |
| 314 | Hotel or motel paid for without emergency shelter voucher | checkmark | | | | | | |
| 312 | Staying or living with family, temporary tenure | checkmark | | | | | | |
| 313 | Staying or living with friends, temporary tenure | checkmark | | | | | | |
| 302 | Transitional housing for homeless persons (including homeless youth) | checkmark | | | | | | |
| 327 | Moved from one HOPWA funded project to HOPWA TH | checkmark | | | | | | |
| 332 | Host Home (non-crisis) | checkmark | | | | | | |

### Permanent Housing Situations (400-499)

| Code | Exit Destination | SO | ES-EE | ES-NbN | TH | HP & PH (all) | SH | SSO |
|------|-----------------|:--:|:-----:|:------:|:--:|:-------------:|:--:|:---:|
| 426 | Moved from one HOPWA funded project to HOPWA PH | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |
| 411 | Owned by client, no ongoing housing subsidy | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |
| 421 | Owned by client, with ongoing housing subsidy | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |
| 410 | Rental by client, no ongoing housing subsidy | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |
| 435 | Rental by client, with housing subsidy | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |
| 422 | Staying or living with family, permanent tenure | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |
| 423 | Staying or living with friends, permanent tenure | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark | checkmark |

### Other (1-99)

| Code | Exit Destination | SO | ES-EE | ES-NbN | TH | HP & PH (all) | SH | SSO |
|------|-----------------|:--:|:-----:|:------:|:--:|:-------------:|:--:|:---:|
| 24 | Deceased | X | X | X | X | X | X | X |
| 8 | Client doesn't know | | | | | | | |
| 9 | Client prefers not to answer | | | | | | | |
| 99 | Data not collected | | | | | | | |
| 30 | No exit interview completed | | | | | | | |
| 17 | Other | | | | | | | |

---

*This material is based upon work supported, in whole or in part, by Federal award number H-21-NP-VA-001 awarded to ICF by the U.S. Department of Housing and Urban Development for NHDAP-funded TA. The substance and findings of the work are dedicated to the public. Neither the United States Government, nor any of its employees, makes any warranty, express or implied, or assumes any legal liability or responsibility for the accuracy, completeness, or usefulness of any information, apparatus, product, or process disclosed, or represents that its use would not infringe privately-owned rights. Reference herein to any individuals, agencies, companies, products, process, services, service by trade name, trademark, manufacturer, or otherwise does not constitute or imply an endorsement, recommendation, or favoring by the author(s), contributor(s), the U.S. Government or any agency thereof. Opinions contained herein are those of the author(s) and do not necessarily reflect the official position of, or a position that is endorsed by, HUD or any Federal agency.*
