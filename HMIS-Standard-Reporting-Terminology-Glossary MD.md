# FY 2026 HMIS Standard Reporting Terminology Glossary

**A Reference Guide for Methods of Selecting Clients and Data Used Commonly in HMIS-Generated Reports**

U.S. Department of Housing and Urban Development

Aligns with FY 2026 HMIS Data Standards | Released October 2025 | For Reporting Beginning October 1, 2025

---

## Revision History

| Date | Version | Content | Revisions |
| --- | --- | --- | --- |
| October 2025 | V1.0 | Active Client Method 2: Active Clients by Date of Service | Added footnote clarifying the use of [date of service] as a generic variable in the pseudocode. Revised pseudocode to reflect requirement for enrollments to have one associated service record within the enrollment period. Added logic accounts for variable handling of [project exit date] by non-residential and Emergency Shelter - Night-by-Night project types |
| | | Gender | Retired section |
| | | Annual Assessment | Added clarifying language on instructions 9 and 10 for reporting on clients with missing data. |
| | | Missing Data | Added clarifying language that missing data includes missing data quality fields in addition to the data elements themselves. |
| | | Q2. Personally Identifiable Information (PII) | Retired Gender (Row 6) and updated last row to be numbered Row 6. Removed instructions related to reporting on Gender in Q2. |
| | | Q7. Inactive Records: Street Outreach and Emergency Shelter | Removed project type 1 from active/inactive consideration in row 2 of the table. Added project type 6 if PATH-funded to active/inactive consideration in row 2 of the table. |
| | | Appendix B: Federal Reports and Glossary Crosswalk | Retired Gender row. Added Handling Housing Move-in Dates row. Added missing references in CE APR column. Removed references to specific Active Client methods in HMIS CSV column. |

## Introduction

HUD's Office of Special Needs Assistance Programs (SNAPS), through the HMIS Data Lab, facilitated a group of Homeless Management Information System (HMIS) vendors, who collaboratively met over a five-month period in 2013, to draft this HMIS Standard Reporting Terminology Glossary (Glossary). This remarkable achievement of cooperation allowed vendors to put into words the logic and language required to produce reports required by HUD and the federal partners. The Glossary was originally created by HMIS vendors, for HMIS vendors.

In 2023, the HMIS Data Lab worked on behalf of SNAPS to facilitate a group of HMIS and comparable database vendors to comprehensively review and update the Glossary over the course of four months. This work was done to align with the FY 2024 data standards and to update guidance in accordance with current best practices.

This document is not intended to be a guidebook instructing communities what they must collect or need to do. Rather, the Glossary is designed to provide HMIS and comparable database software, and their programmers, a foundation upon which they can best program reports required by HUD and the federal partners.

The Glossary is the standard reporting document across different HMIS and comparable database implementations for HUD. This benefits HMIS and comparable database vendors, who can generate and reuse stored procedures or queries based on the Glossary guidance. This benefits the report authors by clearly defining and providing programming logic for common terms. Finally, by establishing the Glossary as the standard, HUD and the federal partners are able to utilize accepted methodologies that have been well vetted when creating reports they wish to have programmed in HMIS and comparable databases.

The Glossary serves as a reference to the programming specifications released by HUD and the federal partners for the vendors. Programmers across HMIS and comparable databases will be expected to use the logic, terminology, and instructions found within the Glossary, unless otherwise advised in the report specifications issued by HUD or the federal partners. When a programming specification references the Glossary, the notation uses "Glossary" and the section name (Active Client, Bed-Night, etc.).

- For example, when a report specification uses the programming logic found within the Glossary to determine which clients are leavers or stayers, the specification will use "Glossary - Leavers and Stayers" to indicate reliance upon the Glossary entry on that subject.

At a minimum, each entry within the Glossary will include the title of the entry, a table indicating HMIS Data Standards and Non-HMIS Data Standards Fields, a description of the entry, and a text box containing the agreed upon logic required to accurately report upon the data. Where further explanation is necessary, detailed instructions are provided to ensure a thorough understanding of the topics presented in this document. HUD expects that vendors will have fiscal year data standards updates available for testing in HMIS by communities at least one month prior to the changes taking effect.

## Definitions

Unless otherwise noted, this document was written using the language of the FY 2026 version of the HMIS Data Standards along with key terms that vendors normally use and understand. For the purposes of this document the following definitions apply:

- **Adult**: Any client aged 18 years or over.
- **Child**: Any client under the age of 18 years.
- **Household**: A household is defined as any person(s) served together and linked together in a project enrollment. A household could include a single person or multiple people.
- **Lodging**: A "lodging project" provides temporary overnight accommodations, such as emergency shelter.
- **Project**: A project is identified by the Continuum of Care (CoC) as part of its homeless response system, in which an individual client or family is enrolled. A project further defined as a "lodging project" provides overnight accommodations and meets the needs of people experiencing homelessness. A "services project" does not provide lodging and meets specific needs of people experiencing or at-risk of experiencing homelessness.
- **Program**: A program refers to the federal funding source used to fund a project. One project may have one funding source or multiple sources.
- **Report Date Range**: The start and end date of a specific reporting period. Because many reports can be executed for a date range other than one year, "report date range" is more flexible than the term "operating year," which is typically used for a HUD Annual Performance Report (APR). The terms [report start date] and [report end date] are used throughout this document to refer to the user-supplied dates for a specific instance of a report execution.
- **Residential**: A "residential project" provides overnight accommodations and includes projects that are meant to be long-term, such as permanent supportive housing.

## Active Clients

**HMIS Data Standards Fields Referenced (2.02, 3.10, 3.11, 3.20, 4.12, 4.14, W1, P1, R14, V2)**

- [project information] (2.02)
- [project start date] (3.10)
- [project exit date] (3.11)
- [housing move-in date] (3.20)
- [current living situation] (4.12)
- [bed-night date] (4.14)
- [services provided - date of service] (W1, P1, R14, V2)

"Active clients" refers to people who have received services from a specific project in a given date range, for inclusion into the universe of clients for a particular reporting question. "Received services" may refer to actually being housed in the case of a housing or entry exit emergency shelter project, in which case such "services" may be indicated by the client's project start and exit dates (Method 1 below).

In the case of specific services only or night-by-night emergency shelter projects, the existence of a specific type of service data including bed-nights, current living situations, or services dated within the report date range and attached to the client record indicates an active client (Method 2 below).

Specific HUD reports (e.g., the CoC APR or CoC CE-APR) will indicate the method of choosing clients for the report. The specifications in this document are intended to serve as a common reference point but specific report instructions can supersede these.

### Method 1: Active Clients by Start/Exit

The default method of determining an active client is based on the client's [project start date], [project exit date], and the [report start date] and [report end date]. The logic below selects active clients according to these parameters.

```
[project start date] <= [report end date]
and (
    [project exit date] is null or [project exit date] >= [report start date]
)
```

### Method 2: Active Clients by Date of Service

Some projects have less formal project exit dates; for example, a shelter which houses persons on a night-by-night basis or a street outreach project. These projects often enter clients upon first service but may not exit clients from the project or the project may exit them (manually or automatically) after a period of inactivity.

These projects should use other data in a client's record to determine who was served within a given date range. In the case of a services only project, this might be a form detailing what medical services were delivered on a particular day. In the case of night-by-night emergency shelters, this would be a "bed-night" form attached to a client's record or other indicator of the provision of a bed for the night. In the case of a street outreach project, this would be a current living situation form attached to a client's record or some other indicator of a contact. In any event, this form must have the date of service. For a client to be considered active, they must have a service between the [project start date] and the [project exit date].

In addition to the date of service, Method 2 should also include the [project exit date] as an indicator of an active client. For example, if a night-by-night emergency shelter correctly exits a client on the date after their last bed-night, and a particular [report start date] *begins* on that date after their last bed-night, then the client can correctly be reported as a leaver. Otherwise, because the exit date is not within the prior year's reporting range, the client will never be reported as a leaver in either reporting range.

- For night-by-night emergency shelters, the client's [project exit date] is recorded as the day after the last [bed-night date].
- For non-residential projects, the [project exit date] must represent the last day a contact was made or a service was provided.

This guidance is relevant for both auto-exit functionality and for manual data entry for project exits.

Projects using Method 2 must include Method 1 as a starting basis, then apply additional filtering based on the [project exit date] as well as the [services provided - date of service], [bed-night date], [current living situation information date] or any other dates that are consistently used by the given project to determine services provided, including those related to coordinated entry. When used in local reporting, any appropriate date/s may be used; when used in HUD reports, only the dates explicitly identified in the reporting specifications should be used. For consistency in reporting, these dates of service must also fall within the confines of the client's [project start date] and the [project exit date]. Each specific report will designate which services are applicable.

The logic below selects active clients according to the existence of services dated in the report range and attached to the client record. Comments in green are a summary of the code immediately below.

> Note: In the pseudocode below, [date of activity] is used as a generic variable for the date of event, whether a service, bed-night, current living situation, etc.

```
/* The enrollment must have at least one relevant record dated within the enrollment period */
[date of activity] >= [project start date]
and (
    [project exit date] is null
    or
    if
        [project type] = 1
        and
        [activity type] = bed-night
    then
        /* Bed-night activities dated on the enrollment exit date are NOT considered
           For Night-By-Night Emergency Shelter projects */
        [date of activity] < [project exit date]
    else
        /* Activities other than bed-nights dated on the enrollment exit date ARE considered
           for non-residential project types */
        [date of activity] <= [project exit date]
)
and (
    (
        /* The exit date is in the date range, regardless of any service records attached to that enrollment. */
        [project exit date] >= [report start date] and [project exit date] <= [report end date]
    )
    or (
        /* The client entered before the end of the report range and has not yet exited,
           or has exited in the future relative to the report range and there is a service in the report range. */
        [project start date] <= [report end date]
        and (
            [project exit date] is null
            or [project exit date] > [report end date]
        )
        and
        [date of activity] >= [report start date]
        and
        [date of activity] <= [report end date]
    )
)
```

### Method 3: Active Clients in Residence

Some reports may require that a client be in residence at a project to be active. This could apply to any type of lodging or residential project such as emergency shelter, transitional housing, or any kind of permanent housing.

```
[project start date] <= [report end date]
and (
    [project exit date] is null or [project exit date] > [report start date]
)
and (
    (   [project type] = 1
        and
        [date of bed-night] >= [report start date]
        and
        [date of bed-night] <= [report end date]
        and
        [date of bed-night] >= [project start date]
        and
        ( [date of bed-night] < [project exit date] or [project exit date] is null )
    )
    or (
        [project type] = 0, 2, 8
    )
    or (
        [project type] = 3, 9, 10, 13
        and
        [housing move-in date] <= [report end date]
        and
        [housing move-in date] >= [project start date]
        and
        ( [housing move-in date] < [project exit date] or [project exit date] is null )
    )
)
```

### Method 4: Active Clients by Post-Exit Services

Some reports may incorporate data recorded about clients *after* the client's [project exit date] (i.e., [data collection stage] = 6). In this case, the client may have already exited prior to the [report start date], so the determination is:

```
[data collection stage] = 6
and
[date of service] >= [report start date]
and
[date of service] <= [report end date]
```

### Method 5: 1+ Nights Active

Some reports require filtering active clients to only include those who were active at least one night in the report period. This is similar to Method 3, except that housing projects do not require a [housing move-in date] before the [report end date] to be included.

```
[project start date] <= [report end date]
and (
    [project exit date] is null or [project exit date] > [report start date]
)
and (
    (   [project type] = 1
        and
        [date of bed-night] >= [report start date]
        and
        [date of bed-night] <= [report end date]
        and
        [date of bed-night] >= [project start date]
        and
        ( [date of bed-night] < [project exit date] or [project exit date] is null )
    )
    or (
        [project type] = 0, 2, 3, 8, 9, 10, 13
    )
)
```

## Bed-Night and Length of Stay in Residence

**HMIS Data Standards Fields Referenced (2.02, 3.10, 3.11, 3.20, 4.14)**

- [project information] (2.02)
- [project start date] (3.10)
- [project exit date] (3.11)
- [housing move-in date] (3.20)
- [bed-night date] (4.14)

"Bed-night" refers to a unit of service where a client is residing overnight in any type of lodging or residential project (e.g., emergency shelter, transitional housing, or permanent housing). Counting bed-nights varies based on the [project type], as described below. Use the method below appropriate for the project type being reported on.

### Method 1: Using Start/Exit Dates

Use when ( [project type] = 0, 2, or 8 ).

```
Bed-nights = [minimum of ( [project exit date], [report end date] + 1) ]
             - [maximum of ( [project start date], [report start date] ) ]
```

Remove [report start date] from above formula if the count of bed-nights extends prior to the report date range (i.e., determining Length of Stay from the beginning of the client's stay in the project).

### Method 2: Using Bed-night Dates

Use when ( [project type] = 1 ).

```
[bed-night date] must be:
>= [project start date]
and < [project exit date] or [project exit date] is null
and >= [report start date]
and <= [report end date]
```

An individual person's bed-nights should be a unique count of the relevant dates. If a client has more than one bed-night recorded on the same date, that date is only counted once. Note that while the [project exit date] is used for determining active clients, it shouldn't be counted as a bed-night.

Remove (and >= [report start date]) from above formula if the count of bed-nights extends prior to the report date range (i.e., when determining Length of Stay).

### Method 3: Using Housing Move-In Date for PH Projects

Use when ( [project type] = 3, 9, 10, 13 ).

```
Bed-nights = [minimum of ( [project exit date], [report end date] + 1) ]
             - [maximum of ( [housing move-in date], [report start date] ) ]
```

Remove [report start date] from above formula if the count of bed-nights extends prior to the report date range (i.e., determining Length of Stay from the beginning of the client's stay in the project).

## Length of Stay in Project

Some reports need to know the length of time a client was in a lodging or residential project separate from the bed-nights the client had in that project. Use the table below in conjunction with the Bed-night and Length of Stay in Residence calculation to determine Length of Stay in Project.

| Project Type | Bed-night and Length of Stay Method |
| --- | --- |
| ( [project type] = 0, 2, 4, 6, 7, 8, 11, 12, 14) | Method 1 |
| ( [project type] = 1 ) | Method 2 |
| ( [project type] = 3, 9, 10, 13 ) | Method 1 or 3, depending on report question |

## Handling Housing Move-In Dates

In many reports, calculations are used that rely on each individual's [housing move-in date]. As [housing move-in date] is only required for the head of household, this data must be 'inherited' by other household members.

- [Housing move-in dates] must occur within the enrollment. Individuals with [housing move-in dates] prior to their [project start dates] or after their [project end dates] should have the [housing move-in dates] disregarded entirely. Additionally, reports should not include data from after the [report end date], so [housing move-in dates] after the [report end date] should also be discarded. These [housing move-in dates] are treated as null for the purposes of reporting.
- When a household member was already in the household when they became housed (individual's [project start date] <= head of household's [housing move-in date]), the head of household's [housing move-in date] should be used as the individual's [housing move-in date]. If the household member exited before the household moved into housing, they do not inherit this [housing move-in date].
- When a household member joins the household after they are already housed (individual's [project start date] > head of household's [housing move-in date]), the individual's [project start date] should be used as the individual's [housing move-in date].

## Chronic Homelessness Status

**HMIS Data Standards Fields Referenced (2.02, 3.08, 3.10, 3.917, 4.12, 4.05, 4.06, 4.07, 4.08, 4.09, 4.10)**

- [project information] (2.02)
- [project start date] (3.10)
- [prior living situation] (3.917)
- [disabling condition] (3.08)
- [current living situation] (4.12)
- [physical disability] (4.05)
- [developmental disability] (4.06)
- [chronic health condition] (4.07)
- [HIV/AIDS] (4.08)
- [mental health disorder] (4.09)
- [substance use disorder] (4.10)

### Overview

The HMIS Data Standards specify that data entry in [prior living situation] requires some type of dependent fields such that fields used in determining chronic homelessness (CH) are only answerable under certain conditions. The fields must be examined in a specific sequence to know whether a client definitely meets CH status, definitely does *not* meet CH status, or if the CH status is don't know/prefers not to answer or unknown due to incomplete data.

### Disabling Condition

The Data Standards allow systems to auto populate the disabling condition field with "Yes" when a client answers "Yes" (Dependent Field A = "Yes") to one of the disability criteria data elements: Physical Disability, Chronic Health Condition, Mental Health Disorder, and/or Substance Use Disorder (4.05, 4.07, 4.09, 4.10), or if Developmental disability (4.06) or HIV/AIDS (4.08) = "Yes" (Field 2 = "Yes"). Reporting should always count these clients as having a disabling condition. Though the programming instructions below only directly reference [disabling condition], it is expected that this field is consistent with the auto-population option in the HMIS. If there is incongruency between [disabling condition] and responses to the disability criteria data elements, a "Yes" answer for any of these should count clients as having a disabling condition. For projects or systems where auto-population is *not* used or if it is unknown whether auto-population is used, tests for each of the separate Dependent Field A for 4.05, 4.07, 4.09 and 4.10, as well as Field 2 for 4.06 and 4.08, must occur within the programming logic of each relevant question.

> Defining Chronically Homeless Final Rule: https://www.hudexchange.info/resource/4847/hearth-defining-chronically-homeless-final-rule/

### CH at Project Start

All adults and heads of household have a CH status at project start using their own data from that entry ([data collection stage] = 1). For an adult or head of a household, use the table below to determine that person's CH status at project start. In PH projects, even though a client's CH status may technically have changed between [project start date] and [housing move-in-date], HUD has determined that [project start date] should be used for this purpose. Process data using each row from top to bottom, and within each row from left to right. Depending on the data, processing may stop on a particular row even though not all fields have been analyzed.

#### CH at Project Start Because of Other Household Members

The members of a household present at project start for the household as a whole (i.e., the earliest [project start date] of anyone in the household on a specific stay) can cause other household members present at start to be considered chronically homeless AND cause the household as a whole to be considered chronically homeless. The CH status of the household cannot change by the addition of household members after the household start date. If the household member that qualified the household as chronically homeless at project start leaves the household, the household maintains its CH status for the time that the household member was part of the household but does not retain it once the qualifying household member exits.

*In cases where the head of household as well as all other adult household members have an indeterminate CH status (don't know, prefers not to answer, missing), any child household members should carry the same CH status as the head of household.*

Note that reporting on clients' CH-at-start status in a specific report date range may require the examination of data on clients who were in the household but left prior to the report date range.

#### CH at Project Start Flowchart

| Row | Data Standards Field | Field Value / Decision | Field Value / Decision | Field Value / Decision | Field Value / Decision |
| --- | --- | --- | --- | --- | --- |
| 1 | [disabling condition] (3.08) OR any of the special needs fields (4.05 - 4.10) with a data collection stage of 1 | If any of these elements = 1 (yes), CONTINUE processing using 3.917A (line 3) or B (line 8) as appropriate. | If [disabling condition] (3.08) = 0 (no), then CH = NO. STOP processing. | If [disabling condition] (3.08) = 8 or 9 then CH = DK/PNTA. STOP processing | If [disabling condition] (3.08) = 99 or is null then CH = missing. STOP processing |
| 2 | 3.917A | | | | |
| 3 | [project type] (2.02.6) | If 0, 1, 4, or 8, CONTINUE processing on line 4. | | | |
| 4 | [approximate date started] (3.917.3) | If <= [project start date] (3.10) - 365 days, CH = YES. STOP processing. | If missing or less than 365 days before [project start date], CONTINUE processing on line 5. | | |
| 5 | [...number of times the client has been on the streets, in es, or sh...] (3.917.4) | If four or more times, CONTINUE processing on line 6. | If 1, 2, or 3 times, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing | If 99 or null then CH = missing. STOP processing |
| 6 | [total number of months homeless...] (3.917.5) | If >= 12, CH = YES. STOP processing. | If 1 to 11 months, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing | If 99 or null then CH = missing. STOP processing |
| 7 | 3.917B | | | | |
| 8 | 3.917B: Homeless Situation: | | | | |
| 9 | [prior living situation] (3.917.1) | If in 100:199, CONTINUE processing on line 10. | | | If null then CH = missing. STOP processing |
| 10 | [approximate date started] (3.917.3) | If <= [project start date] (3.10) - 365 days, CH = YES. STOP processing. | If missing or less than 365 days before [project start date], CONTINUE processing on line 11. | | |
| 11 | [...number of times the client has been on the streets, in es, or sh...] (3.917.4) | If four or more times, CONTINUE processing on line 12. | If 1, 2, or 3 times, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 12 | [total number of months homeless...] (3.917.5) | If >= 12, CH = YES. STOP processing. | If 1 to 11 months, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 13 | 3.917B: Institutional Situation: | | | | |
| 14 | [prior living situation] (3.917.1) | If in 200:299, CONTINUE processing on line 15. | | | If null then CH = missing. STOP processing |
| 15 | [did you stay less than 90 days?] (3.917.2A) | If 1 (yes), CONTINUE processing on line 16. | If 0 (no), CH = NO. STOP processing. | (DK/PNTA not in Data Dictionary) | If null then CH = missing. STOP processing. |
| 16 | [on the night before did you stay on the streets, ES or SH] (3.917.2C) | If 1 (yes), CONTINUE processing on line 17. | If 0 (no), CH = NO. STOP processing. | (DK/PNTA not in Data Dictionary) | If null then CH = missing. STOP processing. |
| 17 | [approximate date started] (3.917.3) | If <= [project start date] (3.10) - 365 days, CH = YES. STOP processing. | If missing or less than 365 days before [project start date], CONTINUE processing on line 18. | | |
| 18 | [...number of times the client has been on the streets, in es, or sh...] (3.917.4) | If four or more times, CONTINUE processing on line 19. | If 1, 2, or 3 times, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 19 | [total number of months homeless...] (3.917.5) | If >= 12, CH = YES. STOP processing. | If 1 to 11 months, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 20 | 3.917B: Temporary, Permanent, and other Situations: | | | | |
| 21 | [prior living situation] (3.917.1) | If in 0:99 or in 300:499, CONTINUE processing on line 22. | | | If null then CH = missing. STOP processing |
| 22 | [did you stay less than 7 nights?] (3.917.2A) | If 1 (yes), CONTINUE processing on line 23. | If 0 (no), CH = NO. STOP processing. | DK/PNTA not in Data Dictionary | If null then CH = missing. STOP processing. |
| 23 | [on the night before did you stay on the streets, ES or SH] (3.917.2C) | If 1 (yes), CONTINUE processing on line 24. | If 0 (no), CH = NO. STOP processing. | DK/PNTA not in Data Dictionary | If null then CH = missing. STOP processing. |
| 24 | [approximate date started] (3.917.3) | If <= [project start date] (3.10) - 365 days, CH = YES. STOP processing. | If missing or less than 365 days before [project start date], CONTINUE processing on line 25. | | |
| 25 | [...number of times the client has been on the streets, in es, or sh...] (3.917.4) | If four or more times, CONTINUE processing on line 26. | If 1, 2, or 3 times, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 26 | [total number of months homeless...] (3.917.5) | If >= 12, CH = YES. STOP processing. | If 1 to 11 months, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |

### CH at a Point in Time

Households in street outreach, shelters, and safe havens ([project type] = 0, 1, 4, or 8) may also have a "point-in-time" CH status designed to include time spent from [project start date] up to a [point-in-time date] as time spent experiencing homelessness. Clients in projects *other than* street outreach, shelters, and safe havens may only have a CH status at project start and cannot age into CH by virtue of being in any of those projects. Reporting on point-in-time CH for these other project types simply uses the client's CH status at project start.

Multi-person households may be considered chronically homeless as of the [point-in-time date] if at least one adult or minor head of household is considered chronically homeless as of the [point-in-time date], according to the following logic.

Each report using CH status at a point-in-time must specify the [point-in-time date] of the measurement. This may be a fixed date for all clients reported, or it may be a date relative to each client's record (e.g., [project exit date]). For each different data element in the calculation, use only the latest available data with an [information date] <= [point-in-time date] and <= [project exit date].

To include time spent in a project towards a client's total time spent experiencing homelessness, it is first necessary to determine the number of months the client was experiencing homelessness immediately prior to starting in the project:

```
[months homeless prior to start] = the number of months covered between
    [approximate date started] and [project start date]
```

Use the "one day in a month counts the whole month" strategy when counting months. In other words, any portion of a month covered by this date range causes the entire month to be included. Set [months homeless prior to start] = 1 even if there is no data in [approximate date started]. See examples below.

#### Entry Exit Emergency Shelters

Calculate a client's [months in project] by looking at the months covered in whole or in part from [project start date] up to and including the lesser of [point-in-time date] or the client's [project exit date]. Count the entire month even if the client was present only for one day of that month. Subtract 1 from this number if the [project start date] does not fall on the first of the month. This is required so as not to count that particular month twice, since that month is already covered in [months homeless prior to start].

#### Night-by-Night Emergency Shelters

Use the individual bed-night dates to indicate in which months the client was experiencing homelessness.

```
Bed-night [information date] >= [project start date]
and [information date] < [project exit date]
and [information date] <= [point-in-time date]
and [information date] > month indicated in [project start date]
```

#### Street Outreach Projects

Use the [current living situation] (4.12) where the client was on the streets, in shelter, or safe haven to indicate in which months the client was experiencing homelessness. Because the last criteria - the contact location - dates of engagement do not count as a client contact for this purpose.

```
Current Living Situation [information date] >= [project start date]
and [information date] < [project exit date]
and [information date] <= [point-in-time date]
and [information date] > month indicated in [project start date]
and [location of contact] = 116, 101, 118 (Place not meant for habitation, Emergency Shelter, Safe Haven)
```

#### [Months in project] Examples

In a project using [project start date] and [project exit date], a client comes in January 31, 2023, and leaves March 2, 2023. The client answered "4/30/2022" for the approximate date this episode of homelessness began. The [months homeless prior to start] = 10 (April 2022 through January 2023). The [months in project] = 2 (February and March - January is excluded since it was already counted).

In a project using a night-by-night method, a client has a [project start date] of January 31, 2023, the client's first bed-night attached to that project stay is also 1/31/2023 with a second bed-night on 3/1/2023. He also answered "4/30/2022" for the [approximate date started]. The [months homeless prior to start] = 10, and [months in project] = 1 (January is excluded, no bed-night in February, and one bed-night in March).

#### CH at Point-in-Time Flowchart

| Row | Data Standards Field / Variable | Field Value / Decision | Field Value / Decision | Field Value / Decision | Field Value / Decision |
| --- | --- | --- | --- | --- | --- |
| 1 | [disabling condition] (3.08) OR any of the special needs fields (4.05 - 4.10) with an [information date] on or before the [point-in-time date] | If any of these elements = 1 (yes), CONTINUE processing on line 2. | If [disabling condition] (3.08) = 0 (no), then CH = NO. STOP processing. | If [disabling condition] (3.08) = 8 or 9 then CH = DK/PNTA. STOP processing | If [disabling condition] (3.08) = 99 or is null then CH = missing. STOP processing |
| 2 | [months homeless prior to start] + [months in project] | If >= 12, CH = YES. STOP processing. | If < 12, CONTINUE processing on line 3. | | |
| 3 | [...number of times the client has been on the streets, in es, or sh...] (3.917.4) | If four or more times, CONTINUE processing on line 4. | If 1, 2, or 3 times, CH = NO. STOP processing. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 4 | [total number of months homeless...] (3.917.5) | If >= 12, CH = YES. STOP processing. | If 1 to 11 months, CONTINUE processing on line 5. | If 8 or 9 then CH = DK/PNTA. STOP processing. | If 99 or null then CH = missing. STOP processing. |
| 5 | [total number of months homeless...] (3.917.5) + [months in project] | If >= 12, CH = YES. STOP processing. | If < 12, CH = NO. STOP processing. | | |

## Contact

**HMIS Data Standards Fields Referenced (3.10, 3.11, 4.12)**

- [project start date] (3.10)
- [project exit date] (3.11)
- [current living situation] (4.12)

An interaction between a street outreach worker (or other project type requiring a contact) and a client is recorded in the [current living situation]. Each time the outreach worker contacts a client, a record of that contact is documented using the [current living situation] element in HMIS.

A client may have more than one contact on a given date. Each contact documented by the [current living situation] should be included in the count when counting contacts within a given date range unless instructed differently in specific report instructions.

```
[project start date] <= [report end date]
and
([project exit date] is null or [project exit date] >= [report start date] )
and
(
    [date of current living situation] >= [report start date]
    and [date of current living situation] <= [report end date]
    and [date of current living situation] >= [project start date]
    and ( [date of current living situation] <= [project exit date] or [project exit date] is null)
)
```

A given report may specify that the client's contact dates recorded in [current living situation] fall between the client's project start and exit dates. If so, the italicized lines above also apply. If no such specification exists, ignore the italicized lines.

## Age

**HMIS Data Standards Fields Referenced (3.03, 3.10)**

- [date of birth] (3.03)
- [date of birth data quality] (3.03)
- [project start date] (3.10)

A client's age is defined as of [project start date] or [report start date], whichever is greater. If the client is already in the project as of the [report start date], use the client's age as of [report start date]. If the client started in the project after the [report start date], use the client's age as of [project start date].

If a report includes data from multiple project stays for the same client, the client's age for the report should be as of the latest [project start date] or [report start date], whichever is greater.

```
If [project start date] <= [report start date] Then
    Age = [report start date] - [date of birth]
Else
    Age = [project start date] - [date of birth]
```

The [date of birth data quality] field should be used to determine a client's age category in the event [date of birth] is blank or a system default.

### Youth Households

The determination of a youth household requires knowing who else is present with a client in the household at a project for a specific report date range. Using age as determined above, identify households where the age is known to be >= 12 and <= 24 for at least one household member and no member is known to be 25 or older. These are youth households. In these households, all clients >= 12 and <= 24 are considered to be "youth". Note that clients in the household with an unknown age do not impact the determination of "youth."

## Date of Engagement

**HMIS Data Standards Fields Referenced (3.10, 3.11, 4.13)**

- [project start date] (3.10)
- [project exit date] (3.11)
- [date of engagement] (4.13)

[Date of engagement] is the date on which an interactive client relationship results in a deliberate client assessment or beginning of a case plan. It is when the engagement date is recorded that data quality is accounted for in a given client record and project enrollment. Engagement date may be the same date as [project start date] or a [current living situation] date.

Projects should only be able to record one date of engagement for each client per project enrollment.

To generate a count of clients with a date of engagement in a given report date range:

```
[project start date] <= [report end date]
and ([project exit date] is null or [project exit date] >= [report start date])
and [date of engagement] >= [report start date]
and [date of engagement] <= [report end date]
and [date of engagement] >= [project start date]
and ([date of engagement] <= [project exit date] or [project exit date] is null)
```

## Date of Enrollment

**HMIS Data Standards Fields Referenced (3.10, 3.11, P3)**

- [project start date] (3.10)
- [project exit date] (3.11)
- [PATH status] (P3)

"Date of Enrollment" is the date on which a client is enrolled into a PATH-funded project, usually indicated by the client signing an enrollment form. Date of Enrollment may be the same date as [project start date], [current living situation] date, or [date of engagement]. Date of Enrollment is strictly a PATH program element.

PATH projects should only be able to record one date of enrollment for each client per project stay.

Using [PATH status], a client is enrolled in PATH if the following is true:

```
[date of status determination] is not null
and
[client became enrolled in PATH] = Yes
```

If the client became enrolled in PATH, [date of status determination] is the [date of enrollment].

The Data Standards indicate the date of status determination is collected once at or before project exit.

To generate a count of clients who are enrolled in a given report date range:

```
[project start date] <= [report end date]
and [project exit date] is null or [project exit date] >= [report start date]
and [date of enrollment] >= [report start date]
and [date of enrollment] <= [report end date]
and [date of enrollment] >= [project start date]
and ( [date of enrollment] <= [project exit date] or [project exit date] is null)
```

## Household Types

**HMIS Data Standards Fields Referenced (5.09)**

- [household ID] (5.09)

**Non-HMIS Data Standards Fields Referenced**

- [global variable: age]

"Household Types" are commonly utilized in reporting to provide meaningful information about the types of household configurations that are experiencing homelessness or accessing homelessness prevention services. Households are defined as a single individual or group of persons who either currently live together in one dwelling unit or would live together in one dwelling unit were they able to maintain suitable housing accommodations. As such, a [household ID] should be assigned to an individual or group of persons upon each [project start date]. While individuals may legitimately be added or removed from the household over time due to changes in familial makeup, the [household ID] will remain constant for that project stay.

A household type may be determined to be one of the following four (4) types:

- Household without Children
- Household with Children and Adults
- Household with Only Children
- Unknown Household Type

To determine a household type, reporting logic should utilize information from all active clients during the reporting period that share the same [household ID]. This should be done before filtering a report for the most recent enrollments. Reporting logic should utilize each client's age for the reporting period (see Global Variable: Age) to classify each client as an Adult (18 and over), a Child (under the age of 18), or Unknown Age (clients with an unspecified birth date).

The following logic should be applied in order:

- If ever in the reporting period there is at least one active child and at least one active adult in the household, the household and all individuals should be categorized as "Household with Children and Adults".
- If ever in the reporting period there is at least one active adult, zero active children and zero active Unknown Age clients, the household and all individuals should be categorized as "Household without Children".
- If ever in the reporting period there is at least one active child, zero active adults and zero active Unknown Age clients, the household and all individuals should be categorized as "Household with Only Children".
- If ever in the reporting period none of the previous statements apply, then the household and all individuals should be categorized as an "Unknown Household Type".

| Household Type | # of Adults | # of Children | # of Persons of Unknown Age |
| --- | --- | --- | --- |
| 1. With children and adults | 1 or more | 1 or more | any |
| 2. Without children | 1 or more | 0 | 0 |
| 3. With only children | 0 | 1 or more | 0 |
| 4. Unknown household type | any not covered above | | 1 or more |

## Unduplicated Household Counts and Unduplicated Client Counts by Household Type

**HMIS Data Standards Fields Referenced (5.08, 5.09, 3.15)**

- [personal ID] (5.08)
- [household ID] (5.09)
- [relationship to head of household] (3.15)

For many reports, especially for longitudinal research, it is common to provide information on an unduplicated number of households and/or a count of clients by household attributes.

### Unduplicated Household Counts

Unduplicated household counts should be determined by performing a distinct count of [personal IDs] of all heads of households (people who have [relationship to head of household] = Self) in the report range.

In the event that your system identifies people in the date range with no head of household, a flag to the system user may be in order (i.e., the head of household may have left the household and a new head of household may not have been assigned).

### Unduplicated Household Counts by Individual Attribute

Some reports will report on unduplicated households broken out by attributes that can be collected for each household member such as destination or housing status. When this occurs, report the information recorded for the [personal ID] of the head of household (people who have [relationship to head of household] = Self) for the most recent head of household for that household.

### Unduplicated Client Counts by Household Type

To provide a breakout of the number of clients by household type, reports should perform a distinct count of clients by their associated household type. Because it is possible that an active client may have been associated with more than one household during the reporting period, the sum of unduplicated clients by household type may exceed the total number of unduplicated clients.

## Project Leavers and Stayers

**HMIS Data Standards Fields Referenced (3.10, 3.11)**

- [project start date] (3.10)
- [project exit date] (3.11)

The method of determining a leaver or stayer is based on the client's last project enrollment during the reporting period for the project(s) being reported on. Note that a particular HMIS report may specify which enrollment data to use across the entire report, which in turn affects the determination of leavers and stayers. The HMIS report may also provide more specific instruction on the determination of leavers and stayers. Those report instructions should override these.

### Project Leavers

Leavers are persons who exited the project and are no longer enrolled in the project as of the last day of the reporting period.

```
[project exit date] >= [report start date]
and [project exit date] <= [report end date]
```

### Project Stayers

Stayers are persons who are active in the project on the last day of the report date range. A stayer's [project exit date] is blank or populated with a date after the [report end date]. This would include a person who exited the project and re-started in the project before the [report end date]. If on the last day of the reporting period, the client does not have a [project exit date], or the [project exit date] is after the end of the reporting period, the client is considered a stayer.

```
[project start date] <= [report end date]
and
( [project exit date] is null or [project exit date] > [report end date] )
```

## Determining Total and Earned Income

**HMIS Data Standards Fields Referenced (3.10, 3.11, 4.02)**

- [project start date] (3.10)
- [project exit date] (3.11)
- [total income] (4.02.18)

Use the chart below to calculate the total income for a specific income record. Process the rules in order starting with #1 and stop processing when a match for the data is found.

If the HMIS is known to auto-calculate [total income] based on the dollar amounts entered in the separate income source fields (earned income, unemployment insurance, etc.) at time of data entry, then it is sufficient to use [total income] directly as it is stored in the database.

| Row | Total Monthly Income | Income from any source | At Least One Individual Source Specified | Individual Source Amounts >= 0.00 Entered? | [total income] |
| --- | --- | --- | --- | --- | --- |
| 1 | (any) And [total income] is auto-calculated at data entry | (any) | (any) | (any) | Use [total income] as calculated |
| 2 | > $0.00 | (any) | (any) | (any) | Use [total income] as entered |
| 3 | (any) | (any) | Yes | Yes | Sum amounts for individual sources to get total monthly income |
| 4 | (any) | No | (any) | (any) | $0.00 |
| 5 | <= $0.00 (non-null) | Yes or NULL | (any) | (any) | $0.00 |
| 6 | (any) | Don't Know or Prefers Not to Answer | (any) | (any) | null (report client as "don't know / prefers not to answer") |
| 7 | (any) | (any) | (any) | (any) | null (report client as "data not collected / missing information") |

[Earned income] is simply the dollar value entered in element 4.02.3.A. If element 4.02.3 ("earned income") indicates yes (1), but no dollar amount is entered in 4.02.3.A, [earned income] is $0.

## Annual Assessment

Reports utilizing Annual Assessment ([data collection stage] = 5) data on stayers in the project 365 days or more require data from the *specific* Annual Assessment on the head of household's anniversary most relevant to the [report date range]. The instructions below describe how to select this exact record for each client.

1. Use the days between the earliest [project start date] of the household's project enrollment and the [report end date] when determining length of stay for this purpose.

2. In the event a household has more than one head of household active in the report range, (i.e., if the first HoH exited and another household member became the HoH), the later HoH's [project start date] will be back-dated to the first HoH's [project start date] and the first HoH's [relationship to head of household] will be updated to something other than "Self". This will maintain determining the Annual Assessment timing on the earliest [project start date] for any given household.

3. Calculate the head of household's number of years in the project. This can be done using the same algorithm as for calculating a client's age as of a certain date. Use the client's [project start date] and the [report end date] as the two dates of comparison. This calculation is time-based, not service-based, so a client with a [project start date] that is active for a year or longer in a night-by-night emergency shelter would require an Annual Assessment, regardless of how many bed-night dates were recorded. It is important to use the "age" method of determining client anniversaries due to leap years; using "one year = 365 days" will eventually incorrectly offset the calculated anniversaries of long-term stayers.

4. If the HoH's number of years in the project is 0, the household is not yet required to have an annual assessment.

5. If the HoH's number of years in the project is more than 0, add that number to the year of the HoH's [project start date]. This becomes the household's relevant anniversary date for the purposes of the report. For example, using a report date range of 10/1/2022 - 9/30/2023, a HoH with a [project start date] of 6/1/2021 will have been in the project 2 years as of 9/30/2023 and so will have an [anniversary date] of 6/1/2023. (i.e., 2021 + 2 = 2023).

6. Use the latest annual assessment ([data collection stage] = 5) for each client in the household dated on or between:
   a. 30 days prior to the [anniversary date] (even if this date falls before the [report start date])
   b. and the lesser of (30 days after the [anniversary date], [report end date])

7. If the household member's [project start date] is > [anniversary date] (i.e., the person entered the household after the annual assessment may have been collected), that person is not yet required to have an annual assessment.

8. Exclude any data with an [information date] > [report end date], even though it is legitimate for a client's relevant annual assessment data to fall in this date range for clients whose anniversaries are near to the end of the [report date range].

9. Clients with no annual assessment data in the relevant date range as indicated in step 6 should be reported as "missing annual assessment" when this outcome is included in the results table for the question. If this outcome is not included in the results table, these clients should be omitted from that particular question.

10. Clients who aren't required to have an annual assessment yet as determined in steps 4 and 7 should be reported in the appropriate row of the results table. If the results table has no row for these clients, they should be completely omitted from that particular question.

## HMIS Data Quality Report

### Purpose

The purpose of the HMIS Data Quality Report is to support HMIS Leads/System Administrators and HMIS end users in identifying and addressing data quality issues in the system. Programming specifications are provided for this report as a part of the Glossary. Vendors are encouraged to program a printable report from the HMIS or comparable database and then use a single or multiple table shells in other reporting applications without reprogramming. It is expected that all or parts of this report will be used in the CoC annual grant application (to discount system performance measures accordingly); Annual Performance Reports (APRs) for CoC; and Consolidated Annual Performance Evaluation Reports (CAPERs) for ESG. Placing the code in the Glossary allows other federal partner programs to also adopt these tables or methods for their reporting purposes.

### Report Date Range

The user must be able to enter a start and end date for the report. The report must be able to be generated for any period of time the user selects (from one week to multiple years).

### Output

The report must be able to be filtered for one, some, or all projects to which the user running the report has HMIS access. Programmers must assume that the reports will be run by project level staff and by single project, companion projects, and by a system administrator on multiple projects of the same project type (e.g., all transitional housing projects in a community), or the entire CoC (for adjunct information for grant applications or system performance measurement).

Each section of the report must have a details mode output for users to identify the specific records included in the section which are generating errors.

### Missing Data

Each section refers to "information missing" for various elements. "Missing" is defined to mean data where the data element field itself has a value of 99 ("data not collected"), is null, or is blank; any associated data quality data element field has a value of 99 ("data not collected"); or where the entire form or table record on which that field resides is completely absent. For example: "Total Monthly Income" should be collected at project start for many projects and is stored in a table with other income information. If a client should have income information collected but does not have a record in this table where [information date] = [project start date] and [data collection stage] = 1, then "Total Monthly Income" is missing because the table record is entirely absent.

### Project Stays to Include

This report should use each relevant client's *latest project stay only*. This allows counts and percentages in these Data Quality sections to match other numbers in reports such as the APR and CAPER.

For project stays in [project type] = 4 and for PATH-funded project stays in [project type] = 6, only count clients that have an [engagement date] prior to the [report end date]. Street outreach and PATH-funded supportive services stays where the client is not engaged should be completely removed from the universe of data (i.e., apply this filter before determining each client's latest stay, with the exception of Q1).

Q1 includes the filtered set of only engaged clients as described, **and** the latest project stays of all possible clients according to each row category. See Q1 below for additional instructions.

## Programming Instructions

In general, any record with a value of Client doesn't know, Client prefers not to answer, or where the information is missing (as described above) is included in the error count for the relevant field. For fields with data logic count criteria, a description is provided under each table below. If there is more than one error for a particular element, the record should only be counted one time.

Q1 provides a validation table for the report. Cells in each of the tables refer back to Q1 for validation and for calculating percentages. (See references to "VAL.B1", "VAL.B2", etc. throughout the tables below).

### Q1. Report Validation Table

| Row | A - Category | B - Count of Clients for DQ | C - Count of Clients |
| --- | --- | --- | --- |
| 2 | Total number of persons served | | |
| 3 | Number of adults (age 18 or over) | | |
| 4 | Number of children (under age 18) | | |
| 5 | Number of persons with unknown age | | |
| 6 | Number of leavers | | |
| 7 | Number of adult leavers | | |
| 8 | Number of adult and head of household leavers | | |
| 9 | Number of stayers | | |
| 10 | Number of adult stayers | | |
| 11 | Number of veterans | | |
| 12 | Number of chronically homeless persons | | |
| 13 | Number of youth under age 25 | | |
| 14 | Number of parenting youth under age 25 with children | | |
| 15 | Number of adult heads of household | | |
| 16 | Number of child and unknown-age heads of household | | |
| 17 | Heads of households and adult stayers in the project 365 days or more | | |

**Universe:** All active clients

**HMIS Reporting Glossary Reference:** Active Clients; Date of Birth / Age; Project Leaver; Project Stayer; Chronically Homeless at project start.

**Rules**

Not all numbers from this table are used in these Data Quality tables, but this table is standardized across this and other reports.

- Column B contains the universe of clients specific to the Data Quality questions:
  - For Street Outreach projects ([project type] = 4) and PATH-funded Supportive Services projects ([project type] = 6), only clients who are engaged as described in Project Stays to Include.
  - For all other projects, all possible clients according to each row category.
- Column C includes data from all relevant clients without regard to project type or engagement status. This column represents the general universe of clients when the Data Quality report is run in the context of other HMIS reports such as the APR or CAPER.
- The totals in column C will match column B for non-street outreach and non-PATH-funded supportive services projects, but two separately-reported columns are necessary to support calculations and validations consistently in subsequent Data Quality questions which will refer to column B.
- For row 11, a veteran:
  - Must be age 18 or older at time of [project start] or [report start date] - whichever is greater.
  - Must indicate 'yes' for [veteran status].
- Number of youth under age 25 (Row 13): For the purpose of this report, consistent with the CoC APR, refer to "Youth Households" above.
- Number of parenting youth under age 25 with children (row 14) = refers to the definition of "youth" as described above, further limited to those with child household members (age < 18 and [relationship to head of household] = 2) also active in the report date range.
- Heads of households and adult stayers in the project 365 days or more (Row 17) should include any adult stayer present when the head of household's stay is 365 days or more, even if that adult has not been in the household that long.

### Q2. Personally Identifiable Information (PII)

**Purpose:** Complete PII is critical to a system's ability to deduplicate and merge client records. Data issues look at any record where information is not present because the client didn't know the response, preferred not to provide a response, the information was missing, or where the response is not consistent with protocols established for the data quality of the element.

| Row | A - Data Element | B - Client Doesn't Know/Prefers Not to Answer | C - Information Missing | D - Data Issues | E - Total | F - % of Issue Rate |
| --- | --- | --- | --- | --- | --- | --- |
| 2 | Name (3.01) | =[8 or 9] | =missing | =[2] | | =[total]/VAL.B2 |
| 3 | Social Security Number (3.02) | =[8 or 9] | =missing | =[rule] | | =[total]/VAL.B2 |
| 4 | Date of Birth (3.03) | =[rule] | =missing | =[rule] | | =[total]/VAL.B2 |
| 5 | Race and Ethnicity (3.04) | =[8 or 9] | =missing | | | =[total]/VAL.B2 |
| 6 | Overall Score | | | | | =[total]/VAL.B2 |

**HMIS Reporting Glossary Reference:** Active Clients.

**Rules**

- Within each row, the column categories are mutually exclusive; records that meet more than one of the criteria described below should be counted in the column for the first match.
- Column B Row 2 - count of clients where [name data quality] = 8 or 9.
- Column C Row 2 - count of clients where [first name] OR [last name] is missing or [name data quality] = 99.
- Column D Row 2 - [name data quality] = 2
- Column B Row 3 - count of clients where [SSN data quality] = 8 or 9.
- Column C Row 3 - count of clients where [social security number] is missing (i.e., the entire field is null) or [SSN data quality] = 99.
- Column D Row 3 - count of clients where [social security number] does not have the last four digits present (but does include data for other digits) or otherwise does not conform to Social Security Administration rules for a valid SSN shown below.
  - For all SSNs:
    - Cannot contain a non-numeric character (excludes any vendor-designated placeholder characters).
    - The third group / last four digits must be present and cannot be "0000".
  - When the first three digits are present:
    - First three digits cannot be "000," "666," or in the 900 series
  - When the fourth and fifth digits are present:
    - The second group / 4th and 5th digits cannot be "00".
  - When all nine digits are present:
    - There cannot be repetitive (e.g., "333333333") or sequential (e.g., "345678901" "987654321") numbers for all 9 digits.

> Note: Beginning with the FY 2024 HMIS Data Standards, HUD is requiring that only the last four digits of a client's Social Security Number (SSN) (data element 3.02) be collected and entered into HMIS. Federal partners participating in HMIS have defined their own SSN data collection requirements. CoCs may choose whether to continue to collect the full nine-digit SSN. A partial SSN will not result in a data issue for data quality reporting purposes when the data is submitted to HUD, as long as the partial SSN follows the guidelines outlined in this document.

- Column B Row 4 - count of clients where ([DOB data quality] = 8 or 9) and [date of birth] is blank.
- Column C Row 4 - count of clients where [date of birth] is missing.
- Column D Row 4 - count of clients where any of the following are true:
  - ([DOB data quality] = 8, 9, or 99) and [date of birth] is not blank
  - [DOB data quality] = 2
  - [date of birth] is any one of the values listed below:
    - Prior to 1/1/1915.
    - After the [date created] for the record.
    - For heads of household and adults only: Equal to or after the [project start date]. This test purposely excludes child household members including those who may be newborns.
- Column B Row 5 - count of clients where [race and ethnicity] = 8 or 9. For [race and ethnicity], include records with an 8 or 9 indicated even if there is also a value of 1, 2, 3, 4, 5, 6, or 7 in the same field.
- Column C Row 5 - count of clients where [race and ethnicity] is missing.
- Column E Rows 2 through 5 - [total] = the unique count of clients reported in columns B, C, or D (i.e., report each record only once per person if the field fails any one of the data quality checks).
- Column E Row 6 - [total] = the unique count of clients reported in columns B, C, or D / rows 2 through 5. Again, report each record only once per person even if there are multiple data quality issues in multiple fields.
- Column F - Divide the [total] by the total number of people indicated in the validations table.

### Q3. Universal Data Elements

**Purpose:** These are elements common to all client records and used for HMIS reporting. Errors look at any record where information is not present because the client didn't know the response, preferred not to provide a response, the information was missing, or where the response is not consistent with protocols established for the data quality of the element.

| Row | A - Data Element | B - Client Doesn't Know/Prefers Not to Answer | C - Information Missing | D - Data Issues | E - Total | F - % of Issue Rate |
| --- | --- | --- | --- | --- | --- | --- |
| 2 | Veteran Status (3.07) | =[8 or 9] | =missing | =[rule] | | =E2/(VAL.B3+VAL.B4) |
| 3 | Project Start Date (3.10) | | | =[rule] | | =E3/VAL.B2 |
| 4 | Relationship to Head of Household (3.15) | | =missing | =[rule] | | =E4/VAL.B2 |
| 5 | Enrollment CoC (3.16) | | =missing | =[rule] | | =E5/(VAL.B15+VAL.B16) |
| 6 | Disabling Condition (3.08) | =[8 or 9] | =missing | =[rule] | | =E6/VAL.B2 |

**HMIS Reporting Glossary Reference:** Active Clients.

Special Needs = [physical disability] (4.05), [developmental disability] (4.06), [chronic health condition] (4.07), [HIV/AIDS] (4.08), [mental health disorder] (4.09), [substance use disorder] (4.10)

**Rules**

- Column B Row 2 - count of adults where [veteran status] = 8 or 9.
- Column C Row 2 - count of adults where [veteran status] is missing.
- Column D Row 2 - count of clients where [veteran status] = 1 and [age] < 18
- Column D Row 3 - count of clients where:
  - [project start date] < [project exit date] for an earlier project start in the same project. This detects overlapping project stays by the same client in the same project OR
  - [project start date] > [project exit date] for this particular project stay. This detects logically impossible enrollments where the client seems to have exited before being enrolled.
- Column C Row 4 - count of all clients where [relationship to head of household] is missing.
- Column D Row 4 - count of all clients where any one of the following are true:
  - [Relationship to head of household] has a value that is not between 1 and 5.
  - There is no household member for the group of clients with the same [household ID] where the [relationship to head of household] = Self (1) (i.e., report every household member without an identified head of household for the [household ID]). OR
  - More than one client for the [household ID] has a [relationship to head of household] = Self (i.e., report every household member in households where multiple heads of household exist).
- Column C Row 5 - count of heads of household where there is no record of [enrollment CoC] for the project start with a [data collection stage] of project start (1).
- Column D Row 5 - count of heads of household where the [continuum code] for the enrollment CoC record does not match a valid HUD-defined CoC code, based on the project's Continuum of Care Information (data element 2.03).
- Column B Row 6 - count of clients where [disabling condition] = 8 or 9.
- Column C Row 6 - count of clients where [disabling condition] = missing.
- Column D Row 6 - count of clients where:

```
(   [disabling condition] = 0
    and
    (   [developmental disability] and/or [HIV/AIDS] response = 1 (yes)
        or
        ([physical disability], [chronic health condition], [mental health disorder],
         or [substance use disorder] = yes
            and where "substantially impairs ability to live independently" = 1 (yes)
        )
    )
)
```

- Column E Rows 2 through 6 - [total] = the unique count of clients reported in columns B, C, or D (i.e., report each record only once per person if the field fails any one of the data quality checks).

### Q4. Income and Housing Data Quality

**Purpose:** These elements are critical for measuring housing and income performance at the project and continuum level. Issues flag any record where information is not present because the client didn't know the response, refused to provide a response or the information was missing or where the response of client has income "yes" or "no" at a data collection stage is inconsistent with the income source information.

| Row | A - Data Element | B - Client Doesn't Know/Prefers Not to Answer | C - Information Missing | D - Data Issues | E - Total | F - % of Issue Rate |
| --- | --- | --- | --- | --- | --- | --- |
| 2 | Destination (3.12) | =[8 or 9] | =missing or [rule] | | | =E2/VAL.B6 |
| 3 | Income and Sources (4.02) at Start | =[8 or 9] | =missing | =[rule] | | =E3/(VAL.B3+VAL.B16) |
| 4 | Income and Sources (4.02) at Annual Assessment | =[8 or 9] | =missing | =[rule] | | =E4/VAL.B17 |
| 5 | Income and Sources (4.02) at Exit | =[8 or 9] | =missing | =[rule] | | =E5/VAL.B8 |

**HMIS Reporting Glossary Reference:** Active Clients, Leavers, Annual Assessment.

Income sources = [earned income] (4.02.3), [unemployment insurance] (4.02.4), [SSI] (4.02.5), [SSDI] (4.02.6), [VA service-connected disability compensation] (4.02.7), [VA non-service-connected disability pension] (4.02.8), [private disability insurance] (4.02.9), [worker's compensation] (4.02.10), [temporary assistance for needy families (TANF)] (4.02.11), [general assistance (GA)] (4.02.12), [retirement income from social security] (4.02.13), [pension or retirement income from a former job] (4.02.14), [child support] (4.02.15), [alimony and other spousal support] (4.02.16), [other source] (4.02.17).

**Rules**

1. Column B Row 2 - count the number of leavers where [destination] = 8 or 9.
2. Column C Row 2 - count the number of leavers where [destination] = 30 or missing.
3. Column B Row 3 - count the number of adults and heads of household active in the report date range where [income from any source] = 8 or 9.
4. Column C Row 3 - count the number of adults and heads of household active in the report date range where any one of the following are true:
   a. [income and sources] at start is completely missing
   b. There is no record of [income and sources] with an [information date] equal to [project start date] and a [data collection stage] of project start (1).
   c. [data collection stage] for [income and sources] = 1 AND [income from any source] = missing.
5. Column D Row 3 - count the number of adults and heads of household active in the report date range where any one of the following are true:
   a. [data collection stage] for [income and sources] = 1 AND [income from any source] = 0 AND there are identified income sources.
   b. [data collection stage] for [income and sources] = 1 AND [income from any source] = 1 AND there are no identified income sources.
6. Column B Row 4 - count the number of adults and heads of household stayers active in the report period range who are expected to have an annual assessment as described under Annual Assessment, AND where [income and sources] = 8 or 9.
7. Column C Row 4 - count the number of adults and heads of household stayers active in the report date range who are expected to have an annual assessment as described under Annual Assessment, AND where any one of the following are true:
   a. There is no record of [income and sources] with an [information date] within 30 days of the anniversary date and a [data collection stage] of annual assessment (5).
   b. [information date] is within 30 days of the anniversary date AND [data collection stage] for [income and sources] = 5 AND [income from any source] = missing.
8. Column D Row 4 - count the number of adults and heads of household stayers active in the report date range who are expected to have an annual assessment as described under Annual Assessment, AND where any one of the following are true:
   a. [information date] is within 30 days of the anniversary date AND [data collection stage] for [income and sources] = 5 AND [income from any source] = 0 AND there are identified income sources.
   b. [information date] is within 30 days of the anniversary date AND [data collection stage] for [income and sources] = 5 AND [income from any source] = 1 AND there are no identified income sources.
9. Column B Row 5 - count the number of adult and head of household leavers where [income and sources] = 8 or 9.
10. Column C Row 5 - count number of adult and head of household leavers where any of the following are true:
    a. There is no record of [income and sources] with an [information date] equal to [project exit date] and a [data collection stage] of project exit (3).
    b. [data collection stage] for [income and sources] = 3 AND [income from any source] = missing.
11. Column D Row 5 - count the number of adult and head of household leavers where any one of the following are true about the [income and sources] record with an [information date] equal to [project exit date]:
    a. [income from any source] = 0 AND there are identified income sources.
    b. [income from any source] = 1 AND there are no identified income sources.
12. Column E Rows 2 through 5 - [total] = the unique count of clients reported in columns B, C, or D (i.e., report each record only once per person if the field fails any one of the data quality checks).

### Q5. Chronic Homelessness

The fields in elements 3.917 A and 3.917 B Prior Living Situation are the building blocks of determining if someone has been homeless enough time to be reported as chronically homeless. If data is missing in any field in [prior living situation], the HMIS is not able to accurately report chronic homelessness.

| Row | A - Entering into project type | B - Count of total records | C - Missing time in institution (3.917.2) | D - Missing time in housing (3.917.2) | E - Approximate date this episode started (3.917.3) Missing | F - Number of times (3.917.4) DK/PNTA/missing | G - Number of months (3.917.5) DK/PNTA/missing | H - % of records unable to calculate |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 | ES-EE, ES-NbN, SH, Street Outreach | | (grayed) | (grayed) | | | | |
| 3 | TH | | | | | | | |
| 4 | PH (all) | | | | | | | |
| 5 | CE | | | | | | | |
| 6 | SSO, Day Shelter, HP | | | | | | | |
| 7 | Total | =B2+B3+B4+B5+B6 | (grayed) | (grayed) | (grayed) | (grayed) | (grayed) | |

**HMIS Reporting Glossary Reference:** Active Clients; Chronic Homelessness at project start.

**Rules**

- This question applies to adults and heads of household active in the date range who started in the project any time after 10/1/2016, which was when element 3.917 was restructured to improve data entry. Apply an extra filter of [project start date] >= 10/1/2016 to all records for this question.
- Row 2 reports on adults and heads of household active in Street Outreach, Emergency Shelter, or Safe Haven ([project type] = 0, 1, 4, 8).
- Row 3 reports on adults and heads of household active in Transitional Housing ([project type] = 2).
- Row 4 reports on adults and heads of household active in all Permanent Housing types ([project type] = 3, 9, 10, 13).
- Row 5 reports on adults and heads of household active in Coordinated Entry projects ([project type] = 14)
- Row 6 reports on adults and heads of household active in Services Only, Day Shelter, and Homelessness Prevention projects ([project type] = 6, 11, 12)
- Column B: Count the total number of adults and heads of household.
- Column C: Count the number of adults and heads of household entering from institution who are missing their [length of stay]:
  - [type of residence] in 200-299 AND
  - [length of stay in prior living situation] = 8, 9, missing.
- Column D: Count the number of adults and heads of household entering from housing and other situations who are missing their [length of stay]:
  - [type of residence] in 0-99 or 300-499 or missing AND
  - [length of stay in prior living situation] = 8, 9, missing.
- Columns E, F and G report only on adults and heads of household expected to have answers in fields 3.917.3, .4, and .5, respectively.
  - Row 2 - all active adults and heads of household.
  - Rows 3 through 6 - active adults and heads of household where one of the following is true:
    - [type of residence] in 100-199
    - ([type of residence] in 200-299) AND ([length of stay in prior living situation] = 10, 11, 2, or 3) AND ([on the night before did you stay on streets, ES, or SH] = 1).
    - ([type of residence] in 0-99 or 300-499 or missing) AND ([length of stay in prior living situation] = 10, 11) AND ([on the night before did you stay on streets, ES, or SH] = 1).
- Column E: Count the number of adults and heads of household with missing response in [approximate date started] (3.917.3).
- Column F: Count the number of adults and heads of household with responses 8, 9, or missing in [number of times...] (3.917.4).
- Column G: Count the number of adults and heads of household with responses 8, 9, or missing in [number of months...] (3.917.5).
- Column H: Count the unique number of adults and heads of household missing one or more responses in columns C through G and divide by the total records in column B.

### Q6. Timeliness

Timely data entry is critical to ensuring data accuracy and completeness. This section identifies how quickly project starts and project exits are entered into the HMIS after they occur.

| Row | A - Time for Record Entry | B - Number of Project Start Records | C - Number of Project Exit Records |
| --- | --- | --- | --- |
| 2 | < 0 days | | |
| 3 | 0 days | | |
| 4 | 1-3 days | | |
| 5 | 4-6 days | | |
| 6 | 7-10 days | | |
| 7 | 11+ days | | |

**HMIS Reporting Glossary Reference:** Active Clients, Leavers.

**Rules**

- Column B - count the number of active clients who started in the report date range (i.e., where [project start date] >= [report start date] and [project start date] <= [report end date]), where the number of days between [project start date] and [date created] is within the timeframe identified in Column A.
- Column C - count the number of leavers where the number of days between [project exit date] and [date created] is within the timeframe identified in Column A.
- Row 2 contains [project start dates] and [project exit dates] effective after the [date created]. This row will only contain zeros if all data was entered on or after the date of occurrence.

### Q7. Inactive Records: Street Outreach and Emergency Shelter

Data quality includes maintaining accuracy in the number of active records in a system. For projects where clients often leave or disappear without an exit (street outreach and night-by-night shelters), the records often remain open and hamper the project and community's ability to generate accurate performance measurement. This section sets a 90-day limit on inactive records and reports how many records within the report range are inactive (i.e., should have been exited but were not) based on contact with the client for outreach or bed-nights for shelter. Column B - # of Records - contains active according to start and exit dates *regardless of project type*.

| Row | A - Data Element | B - # of Records | C - # of Inactive Records | D - % of Inactive Records |
| --- | --- | --- | --- | --- |
| 2 | Contact (Adults and Heads of Household in Street Outreach or PATH-funded SSO) | | | =C2/B2 |
| 3 | Bed-night (All clients in ES - NbN) | | | =C3/B3 |

**Rules**

- Row 2 reports on adults and heads of household active in project type 4 (for all funding sources) and project type 6 if PATH-funded.
- Row 3 reports on clients active in project type 1.
- Column B Row 2 - adults and heads of household with [project start date] < ([report end date] - 90 days) and ([project exit date] is null or [project exit date] > [report end date]).
- Column B Row 3 - all clients with [project start date] < ([report end date] - 90 days) and ([project exit date] is null or [project exit date] > [report end date]).
- Column C Row 2 - count the number of adults and heads of household where the latest [current living situation] was more than 90 days prior to the [report end date].
- Column C Row 3 - count the number of clients where the latest [bed-night date] was more than 90 days prior to the [report end date].

## Appendix A: HMIS Imports and Exports

This section contains recommended methods to aid in the export or import of HMIS data in cases where the data in question does not perfectly align to HMIS Data Standards and the official HMIS CSV specifications. These methods may work as-is or may be modified based on the data in question.

### Missing or Multiple Head of Household

The procedure below can facilitate the importing of data with "broken" households, or bulk-updating of data within HMIS, with either no head of household identified or multiple heads of household.

The procedure is a best effort to ensure that everyone present together in a household at a particular project has a household configuration with one and only one head of household ([relationship to head of household] = 1) for a given [household ID]).

Follow the sequence below and stop when a match is found.

| Household Configuration | Set Head of Household to... |
| --- | --- |
| 1 person in household | That person |
| Multiple people with at least one adult | The oldest person aged 18 or greater as of [project start] |
| Multiple people all age 17 or less, with one or more children aged 10 or less | The oldest person aged 11 or greater as of [project start] |
| Multiple people all age 11 to 17 | Split the household into one household per person (i.e., they are each a head of household) |

### Combining Households - Matching Child HoHs with Adults

The simple report and procedure below can help identify child heads of household in projects which do not normally have them, alongside adults previously present with the child in the HMIS who is also at the same project. This may be the result of users improperly identifying households during data entry or some error during the export or import of HMIS data. This information can be used to merge the two separate households into one (however that is done in HMIS), with the adult as the head of household. The report can be used as-is or modified as needed based on specific HMIS database characteristics.

**Sample Report Output**

| Row | A - Project name | B - Child name | C - Age at entry | D - Project dates | E - Previously at project name | F - Previous project start date | G - Adult present with child | H - Adult currently present at same project |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 | Project ABC | Atom Ant | 5 | 1/10/2022 - present | Project ZBQ | 6/1/2021 | Suzie Ant | 1/10/2022 - present |
| 3 | Project ABC | Davi Quark | 7 | 3/1/2022 - 3/15/2022 | Project ZBQ | 9/2/2021 | Roger Quark | 2/15/2022 - 3/15/2022 |

**HMIS Reporting Glossary Reference:** Active Clients

**Programming instructions**

1. Select all clients active in the desired project(s) in a given date range. Because the goal of this report is to aid users or HMIS System Administrators to correct data, it's necessary to select *all* enrollments active in the report date range - not just the latest one for each client.
2. Determine each client's age as of [project start date]. Note this is slightly different than determining the client's age for general reporting purposes.
3. Identify the clients whose age is <= 17 as of [project start date] who are the head of household ([relationship to head of household] = 1). This is the universe of clients for this report. Output their data in columns A through D. Note this could result in the same client being listed more than once if more than one enrollment matches the report criteria.
4. For each row, scan that child's prior project enrollments for one where that child wasn't the head of household but instead was with an adult (age at [project start date] > 17). The report is most useful if it includes all project stays across the entire HMIS to maximize the likelihood of detecting a relevant adult.
5. Output enrollment information in columns E through G.
6. Using the adult record found in step 4, if that adult is also present in the same project as column A (the one where the child HoH is) with dates overlapping the child's, output the adult's [project start date] in that project in column H.
7. Using the data discovered, users or administrators can match up children with a likely head of household at the same project.

## Appendix B: Federal Reports and Glossary Crosswalk

| Glossary Logic | CoC APR/ESG CAPER | CE APR | SPMs | LSA | CSV Specs | PATH Annual Report |
| --- | --- | --- | --- | --- | --- | --- |
| Active Clients | X | X | X | | X | |
| Active Clients - Method 1 | X | | X | | | |
| Active Clients - Method 2 | X | X | X | | | X |
| Active Clients - Method 3 | | | | | | |
| Active Clients - Method 4 | | | | | | |
| Active Clients - Method 5 | | | X | | | |
| Bed-night and Length of Stay in Residence - Method 1 | X | | X | | | |
| Bed-night and Length of Stay in Residence - Method 2 | X | | X | | | |
| Bed-night and Length of Stay in Residence - Method 3 | X | | X | | | |
| Length of Stay in Project | X | | X | | | |
| Handling Housing Move-In Dates | X | | | | | |
| Disabling Conditions | X | | | | | |
| Chronic Homelessness at Project Start | X | | | | | X |
| Chronic Homelessness at a Point in Time | | | | | | |
| Contact | X | | | | | |
| Age | X | X | X | | | X |
| Race and Ethnicity | X | | | | | |
| Date of Engagement | X | | | | | |
| Household Types | X | X | | | | |
| Unduplicated Household Counts | X | X | | | | |
| Unduplicated Households Counts by Individual Attribute | X | X | | | | |
| Unduplicated Client Counts by Household Type | X | | | | | |
| Project Leavers | X | | X | | | |
| Project Stayers | X | | X | | | |
| Annual Assessment | X | | | | | |
| Determining Total and Earned Income | X | | X | | | |
| HMIS Data Quality Report | X | X | | | | |

---

*This material is based upon work supported, in whole or in part, by Federal award number H-20-NP-VA-001 awarded to ICF by the U.S. Department of Housing and Urban Development for NHDAP-related technical assistance. The substance and findings of the work are dedicated to the public. Neither the United States Government, nor any of its employees, makes any warranty, express or implied, or assumes any legal liability or responsibility for the accuracy, completeness, or usefulness of any information, apparatus, product, or process disclosed, or represents that its use would not infringe privately-owned rights. Reference herein to any individuals, agencies, companies, products, process, services, service by trade name, trademark, manufacturer, or otherwise does not constitute or imply an endorsement, recommendation, or favoring by the author(s), contributor(s), the U.S. Government or any agency thereof. Opinions contained herein are those of the author(s) and do not necessarily reflect the official position of, or a position that is endorsed by, HUD or any Federal agency.*
