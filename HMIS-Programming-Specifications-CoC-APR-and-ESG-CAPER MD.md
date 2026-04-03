# HUD: CoC APR and ESG CAPER - HMIS Programming Specifications

**HMIS Programming Specifications V1.0**

U.S. Department of Housing and Urban Development

Aligns with FY 2026 HMIS Data Standards | Released October 2025

For Reporting Beginning October 1, 2025

---


## Revision History

Date Version Description
For APRs and CAPERs submitted on or after 10/1/2025
October 2025 V1.0 Introduction
- Added note regarding expected testing availability timeline
Q6a
- Removed row referencing gender
Q6f
- Removed NbN shelters from row 2 to reflect that Contact (Current
Living Situation) is no longer monitored for the Emergency Shelter –
Night-by-Night project type within the referenced HMIS Glossary
Data Quality Report table (Q7)
- Added PATH-funded SSO to row 2 to reflect that Contact (Current
Living Situation) is monitored, identical to Street Outreach, within the
referenced HMIS Glossary Data Quality Report table (Q7)
Q10a
- Removed question
Q10d
- Removed question
Q16
- Added language related to rounding for income
Q22e
- Corrected typo in programming instruction 2c, which now refers to
the correct row number for “Data not collected.”
Q24c
- Removed question
Q24d
- Removed question
Q24e
- Added question
Q25c
- Removed question
Q26c
- Removed question
Q27c
- Removed question
Label for Hispanic/Latina/o/e

|  | Date |  |  | Version |  |  | Description |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | For APRs and CAPERs submitted on or after 10/1/2025 |  |  |  |  |  |  |  |
| October 2025 |  |  | V1.0 |  |  | Introduction | Introduction |  |
|  |  |  |  |  |  | • Added note regarding expected testing availability timeline |  |  |
|  |  |  |  |  |  |  | Q6a |  |
|  |  |  |  |  |  | • Removed row referencing gender |  |  |
|  |  |  |  |  |  |  | Q6f |  |
|  |  |  |  |  |  | • Removed NbN shelters from row 2 to reflect that Contact (Current Living Situation) is no longer monitored for the Emergency Shelter – Night-by-Night project type within the referenced HMIS Glossary Data Quality Report table (Q7) • Added PATH-funded SSO to row 2 to reflect that Contact (Current Living Situation) is monitored, identical to Street Outreach, within the referenced HMIS Glossary Data Quality Report table (Q7) |  |  |
|  |  |  |  |  |  |  | Q10a |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Q10d |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Q16 |  |
|  |  |  |  |  |  |  | • Added language related to rounding for income |  |
|  |  |  |  |  |  |  | Q22e |  |
|  |  |  |  |  |  | • Corrected typo in programming instruction 2c, which now refers to the correct row number for “Data not collected.” |  |  |
|  |  |  |  |  |  |  | Q24c |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Q24d |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Q24e |  |
|  |  |  |  |  |  | • Added question |  |  |
|  |  |  |  |  |  |  | Q25c |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Q26c |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Q27c |  |
|  |  |  |  |  |  | • Removed question |  |  |
|  |  |  |  |  |  |  | Label for Hispanic/Latina/o/e |  |

- Updated throughout to Hispanic/Latina/o

## Introduction

This HUD HMIS Programming Specification document details the business rules required for the HUD
Continuum of Care (CoC) Annual Performance Report (APR) and Emergency Solutions Grants (ESG)
Consolidated Annual Performance and Evaluation Report (CAPER) to be submitted in the Sage HMIS
Reporting Repository (Sage). These programming specifications are applicable to all project types except
Coordinated Entry projects (element 2.02.6 = 14). APRs for Coordinated Entry projects must be generated
using the HMIS Programming Specifications for Coordinated Entry APR (CE APR). HUD expects that
vendors will have fiscal year data standards updates released for testing by communities at least one
month prior to the changes taking effect.
The programming specifications contained in this document cover all questions for the CoC APR and ESG
CAPER where the information needed to answer the question is required/expected to be extracted from
an HMIS or comparable database system. Please see the following section for a table of questions that
apply to the APR, CAPER, or both reports. These specifications were developed utilizing the HUD Data
Standards as found in the current version of the FY 2026 HMIS Data Dictionary. Wherever possible, these
specifications also refer to the FY 2026 HMIS Standard Reporting Terminology Glossary (HMIS Reporting
Glossary), which outlines programming rules developed for and with HMIS and comparable database
vendors to facilitate streamlined programming and comparable reporting across systems.

### Exporting Report Results to CSV

The CoC APR and ESG CAPER will be submitted to HUD in Sage via CSV export of aggregate results in the
manner described below.
1. Both the APR and CAPER must be programmed to allow for an export of all HMIS-generated tables in
standard CSV format.
2. Each question in the report must generate one CSV file and must be named the same as the question
table number, e.g., “Q6b.csv”. Sage is designed to recognize only these exact file names but are case-
insensitive so that “Q6b.csv”, “q6b.CSV”, “Q6B.CSV” are all valid.
3. The APR consists of 67 separate tables for a total of 67 CSV output files. The CAPER consists of 41
separate tables for a total of 40 CSV output files. Note that not every question/file will generate data
for every project type or may have a total of zero applicable client records. However, all output files
are required even if the number of clients reported is zero.
4. The structure of each file must match the layout in the programming specifications table shell for that
question in terms of the quantity and sequence of lettered columns and numbered rows, excluding
columns Y and Z (Y and Z are only present to aid in programming and not part of the report output to
screen or CSV). Sage is designed to read data from the output tables according to cell position, not
row and column headers, so the position of each number output in the files is critical.
5. Column and row headers must be exported for every table shell which has them, but these headers
are ignored when exported. There always must be a placeholder for each cell that is a header in the
CSV file (see first row of example below) to maintain the overall structure of the file.
6. All grayed-out cells are those which logically should not contain any data (see cells C2 through C4 and
E5 through E10). The CSV must contain either 0 (zero) or (blank) with a comma for all grayed-out cells.
(For assistive technology, this will be indicated as ---)
7. Use double quotes to surround ALL text in column and row headers in order to ignore commas which
are sometimes present in that text.
8. Double quotes are optional surrounding numbers.
9. Table cells that contain percentages should output those as decimal numbers without multiplying by
100 and carry at least 4 places to the right of the decimal. For example, if 7 out of 9 clients exited to
positive housing in Q23, the output should be 0.7778 or .7778.
10. Table cells that contain averages should contain decimal numbers with at least 2 places to the right of
the decimal if the output is money. If the output is any other type of average such as number of days, it
may contain an integer or a decimal number with up to 4 places to the right of the decimal.
11. When output from an HMIS, the entire set of files (67 for the APR, 40 for the CAPER) should be
compressed into a .zip file.
The examples below show the format for an example question (Q11: Age) with sample data in the table
shell as indicated in the programming specifications followed by the layout of that same table in CSV
format.
Q11 table shell
Without With Children With Only Unknown Household
Total Children and Adults Children Type
Under 5 0 0 0 0 0
5-12 0 0 0 0 0
13-17 0 0 0 0 0
18-24 1 1 0 0 0
25-34 3 3 0 0 0
35-44 3 3 0 0 0
45-54 13 13 0 0 0
55-64 6 6 0 0 0

|  |  |  | Total |  | Without |  |  | With Children |  |  | With Only |  |  | Unknown Household |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  | Children |  |  | and Adults |  |  | Children |  |  | Type |  |
|  | Under 5 |  | 0 | 0 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 5-12 |  | 0 | 0 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 13-17 |  | 0 | 0 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 18-24 |  | 1 | 1 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 25-34 |  | 3 | 3 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 35-44 |  | 3 | 3 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 45-54 |  | 13 | 13 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | 55-64 |  | 6 | 6 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |

Without With Children With Only Unknown Household
Total Children and Adults Children Type
65+ 2 2 0 0 0
Client Doesn’t Know/
Prefers Not to Answer 0 0 0 0 0
Data Not Collected 0 0 0 0 0
Total 28 28 0 0 0
Q11.csv

|  |  |  | Total |  | Without |  |  | With Children |  |  | With Only |  |  | Unknown Household |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  | Children |  |  | and Adults |  |  | Children |  |  | Type |  |
|  | 65+ |  | 2 | 2 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | Client Doesn’t Know/ |  | 0 | 0 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Data Not Collected |  | 0 | 0 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |
|  | Total |  | 28 | 28 |  |  | 0 |  |  | 0 |  |  | 0 |  |  |


### Table of Questions

CoC ESG
Number Question APR CAPER


History of Domestic Violence, Sexual Assault, Dating Violence, Stalking, or Human ✗ ✗
Q14a
Trafficking
Most recent experience of domestic violence, sexual assault, dating violence, stalking, ✗ ✗
Q14b
or human trafficking


Client Cash Income Category - Earned/Other Income Category - by Start and Annual ✗
Q18
Assessment/Exit Status


| Number | Question |  | CoC |  |  | ESG |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  | APR |  |  | CAPER |  |
| Q4a | Project Identifiers in HMIS | ✗ |  |  | ✗ |  |  |
| Q5a | Report Validations Table | ✗ |  |  | ✗ |  |  |
| Q6a | Data Quality: Personally Identifiable Information | ✗ |  |  | ✗ |  |  |
| Q6b | Data Quality: Universal Data Elements | ✗ |  |  | ✗ |  |  |
| Q6c | Data Quality: Income and Housing Data Quality | ✗ |  |  | ✗ |  |  |
| Q6d | Data Quality: Chronic Homelessness | ✗ |  |  | ✗ |  |  |
| Q6e | Data Quality: Timeliness | ✗ |  |  | ✗ |  |  |
| Q6f | Data Quality: Inactive Records: Street Outreach and Emergency Shelter | ✗ |  |  | ✗ |  |  |
| Q7a | Number of Persons Served | ✗ |  |  | ✗ |  |  |
| Q7b | Point-in-Time Count of Persons on the Last Wednesday | ✗ |  |  | ✗ |  |  |
| Q8a | Number of Households Served | ✗ |  |  | ✗ |  |  |
| Q8b | Point-in-Time Count of Households on the Last Wednesday | ✗ |  |  | ✗ |  |  |
| Q9a | Number of Persons Contacted | ✗ |  |  | ✗ |  |  |
| Q9b | Number of Persons Newly Engaged | ✗ |  |  | ✗ |  |  |
| Q11 | Age | ✗ |  |  | ✗ |  |  |
| Q12 | Race and Ethnicity | ✗ |  |  | ✗ |  |  |
| Q13a1 | Physical and Mental Health Conditions at Start | ✗ |  |  | ✗ |  |  |
| Q13b1 | Physical and Mental Health Conditions at Exit | ✗ |  |  | ✗ |  |  |
| Q13c1 | Physical and Mental Health Conditions for Stayers | ✗ |  |  | ✗ |  |  |
| Q13a2 | Number of Conditions at Start | ✗ |  |  |  |  |  |
| Q13b2 | Number of Conditions at Exit | ✗ |  |  |  |  |  |
| Q13c2 | Number of Conditions for Stayers | ✗ |  |  |  |  |  |
| Q14a | History of Domestic Violence, Sexual Assault, Dating Violence, Stalking, or Human Trafficking | ✗ |  |  | ✗ |  |  |
| Q14b | Most recent experience of domestic violence, sexual assault, dating violence, stalking, or human trafficking | ✗ |  |  | ✗ |  |  |
| Q15 | Living Situation | ✗ |  |  | ✗ |  |  |
| Q16 | Cash Income – Ranges | ✗ |  |  | ✗ |  |  |
| Q17 | Cash Income - Sources | ✗ |  |  | ✗ |  |  |
| Q18 | Client Cash Income Category - Earned/Other Income Category - by Start and Annual Assessment/Exit Status | ✗ |  |  |  |  |  |
| Q19a1 | Client Cash Income Change - Income Source - by Start and Latest Status | ✗ |  |  |  |  |  |
| Q19a2 | Client Cash Income Change - Income Source - by Start and Exit | ✗ |  |  |  |  |  |
| Q19b | Disabling Conditions and Income for Adults at Exit | ✗ |  |  | ✗ |  |  |
| Q20a | Type of Non-Cash Benefit Sources | ✗ |  |  | ✗ |  |  |
| Q20b | Number of Non-Cash Benefit Sources | ✗ |  |  |  |  |  |
| Q21 | Health Insurance | ✗ |  |  | ✗ |  |  |

CoC ESG
Number Question APR CAPER


Length of Time between Project Start Date and Housing Move-In Date by Race and ✗ ✗
Q22f
Ethnicity
Length of Time Prior to Housing by Race and Ethnicity – based on 3.917 Date ✗ ✗
Q22g
Homelessness Started


Exit Destination - Subsidy Type of Persons Exiting to Rental by Client With An ✗ ✗
Q23d
Ongoing Subsidy


Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy – ✗
Q25j
Veterans


Exit Destination – Subsidy Type of Persons Exiting to Rental by Client With An ✗
Q27f2
Ongoing Subsidy – Youth


Client Cash Income Category - Earned/Other Income Category - by Start and Annual ✗
Q27h
Assessment/Exit Status - Youth


| Number | Question |  | CoC |  |  | ESG |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  | APR |  |  | CAPER |  |
| Q22a1 | Length of Participation – CoC Projects | ✗ |  |  |  |  |  |
| Q22a2 | Length of Participation – ESG Projects |  |  |  | ✗ |  |  |
| Q22b | Average and Median Length of Participation in Days | ✗ |  |  |  |  |  |
| Q22c | Length of Time between Project Start Date and Housing Move-in Date | ✗ |  |  | ✗ |  |  |
| Q22d | Length of Participation by Household Type |  |  |  | ✗ |  |  |
| Q22e | Length of Time Prior to Housing – Based on 3.917 Date Homelessness Started | ✗ |  |  | ✗ |  |  |
| Q22f | Length of Time between Project Start Date and Housing Move-In Date by Race and Ethnicity | ✗ |  |  | ✗ |  |  |
| Q22g | Length of Time Prior to Housing by Race and Ethnicity – based on 3.917 Date Homelessness Started | ✗ |  |  | ✗ |  |  |
| Q23c | Exit Destination | ✗ |  |  | ✗ |  |  |
| Q23d | Exit Destination - Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy | ✗ |  |  | ✗ |  |  |
| Q23e | Exit Destination Type by Race and Ethnicity | ✗ |  |  | ✗ |  |  |
| Q24a | Homelessness Prevention Housing Assessment at Exit |  |  |  | ✗ |  |  |
| Q24b | Moving On Assistance Provided to Households in PSH | ✗ |  |  |  |  |  |
| Q24e | Sex | ✗ |  |  | ✗ |  |  |
| Q25a | Number of Veterans | ✗ |  |  | ✗ |  |  |
| Q25b | Number of Veteran Households | ✗ |  |  |  |  |  |
| Q25d | Age – Veterans | ✗ |  |  |  |  |  |
| Q25i | Exit Destination – Veterans | ✗ |  |  |  |  |  |
| Q25j | Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy – Veterans | ✗ |  |  |  |  |  |
| Q26a | Number of Households w/at least one or more Chronically Homeless person | ✗ |  |  |  |  |  |
| Q26b | Number of Chronically Homeless Persons by Household | ✗ |  |  | ✗ |  |  |
| Q26d | Age of Chronically Homeless Persons | ✗ |  |  |  |  |  |
| Q26e | Physical and Mental Health Conditions - Chronically Homeless Persons | ✗ |  |  |  |  |  |
| Q27a | Age of Youth | ✗ |  |  |  |  |  |
| Q27b | Parenting Youth | ✗ |  |  |  |  |  |
| Q27d | Living Situation – Youth | ✗ |  |  |  |  |  |
| Q27e | Length of Participation – Youth | ✗ |  |  |  |  |  |
| Q27f1 | Exit Destination – Youth | ✗ |  |  |  |  |  |
| Q27f2 | Exit Destination – Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy – Youth | ✗ |  |  |  |  |  |
| Q27g | Cash Income – Sources - Youth | ✗ |  |  |  |  |  |
| Q27h | Client Cash Income Category - Earned/Other Income Category - by Start and Annual Assessment/Exit Status - Youth | ✗ |  |  |  |  |  |
| Q27i | Disabling Conditions and Income for Youth at Exit | ✗ |  |  |  |  |  |
| Q27j | Average and Median Length of Participation in Days - Youth | ✗ |  |  |  |  |  |

CoC ESG
Number Question APR CAPER


## Fundamentals


### Program and Project Type Applicability

The CoC APR is utilized for projects with one or more Funding Source responses (element 2.06) with a
HUD: CoC prefix, in addition to HUD: Pay for Success (35), HUD: Unsheltered Special NOFO (54), HUD: Rural
Special NOFO (55), and HUD: CoC Builds (56). The ESG CAPER is utilized for projects with one or more
Funding Source responses (element 2.06) with a HUD: ESG prefix, including ESG-RUSH (53). For a full list
of current Federal Partner funding sources using HMIS to collect and report data, please see the FY 2026
HMIS Data Dictionary Project Descriptor Element – Federal Funding Sources (element 2.06). Additionally,
it is expected that the CoC APR and ESG CAPER can be run on any project in the HMIS for local review
and analysis outside of funding requirements.
Each question on the APR/CAPER identifies the HMIS project type that will be required to respond to the
question. For projects funded with HUD: Pay for Success, regardless of the Project Type identified, the
APR should generate data for all questions, including those associated with 3.20 Housing Move-In Date.
This means that any project with HUD: Pay for Success as a funding source should collect and enter data
for 3.20 Housing Move-In Date. The HMIS-generated report may leave all cells blank or zero for questions
that do not apply to a given project type.

### Report Programming Basics

This report generally uses Active Client - Method 1 from the HMIS Reporting Glossary to determine which
clients to include in the reporting universe for [project types] 0 and 2 through 14, except where noted on
specific questions. Emergency Shelter – Night-by-Night ([project type] = 1) projects use Active Client –
Method 2.
The CoC APRs/ESG CAPERs should only pull data explicitly entered by and attached to each client’s latest
project stay for the particular project being reported on. In the event a client was active in more than one
project stay in the report date range, all data for the report should come from the client’s latest project
stay according to [project start date] unless otherwise noted (e.g., Q7b and Q8b).
Some questions are further limited to “stayers” and “leavers”. Refer to the HMIS Reporting Glossary for
instructions in determining these client universes.

| Number | Question |  | CoC |  |  | ESG |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  | APR |  |  | CAPER |  |
| Q27k | Length of Time between Project Start Date and Housing Move-in Date - Youth | ✗ |  |  |  |  |  |
| Q27l | Length of Time Prior to Housing - based on 3.917 Date Homelessness Started - Youth | ✗ |  |  |  |  |  |
| Q27m | Education Status – Youth | ✗ |  |  |  |  |  |

Several Data Elements are required across this entire report and as such will not be listed in the reference
information for each individual question. These elements are:
1. [Project ID] (element 2.02) – Used to select clients and data for the report.
2. [Personal ID] (element 5.08) – Used to identify/count unique/distinct persons.
3. [Enrollment ID] (element 5.06) – Used to link data together for a specific person/project stay.
4. [Household ID] (element 5.09) – Used to link household members who are together on a specific
project stay.
5. [Relationship to Head of Household] (element 3.15) – Used to relate household members who are
together on a specific project stay. Also used in determining “parenting youth” for Q28b.
6. [Date of Birth] (element 3.03) – Used to identify age of persons and determine household type.
7. [Data collection stage] (element 5.03) – Used to retrieve data attached to a specific event during the
client’s project stay. Some questions report on data specifically dated at project start ([collection
stage] = 1), annual assessment ([collection stage] = 5), latest available ([collection stage] = 1, 2, or 5), or
project exit ([collection stage] = 3). The data collection stage will be explicitly listed for such
questions.

### Determining Age

Per the HMIS Reporting Glossary, Age is a global variable determined from a client’s [date of birth] (3.03).
These reporting specifications comply with the methods of determining Age per the HMIS Reporting
Glossary. In the event a client has more than one active project stay in the report date range, a client’s
age for every section of the report is as of the latest [project start date] or [report start date], whichever
comes later.
Determining Each Client’s Household Type and Counting Distinct Households
This report uses the following methods from the HMIS Reporting Glossary:
1. Unduplicated Client Counts by Household Type
2. Unduplicated Household Counts by Individual Attribute
3. Unduplicated Household Counts
The relevant method utilized will be detailed in the reference information for each question in these
specifications as applicable. Because this report uses data from each client’s latest project stay, each
client may have only one household type as determined by the household composition on that latest
stay. This includes the Head of Household, which is used for determining counts of households according
to household type.
Youth households are defined as households where all persons in the household with a known age are 24
or younger (age >= 0 and <= 24). The household may include persons in the household with unknown ages
as long as all known ages are between 0 and 24. If no household member’s age is known, the household is
not counted as a youth household.

### Client Types

This report references the following age-related variables in several tables, and as such these will not be
repeated in the reference information for each individual question:
Youth = any client in a youth household (defined above) age >= 12 and <= 24.
Child = any client age < 18. The [relationship to head of household] (element 3.15) does not matter unless
a specific reporting question also includes this element.
Adults = any client age >= 18.
Heads of Household = any client where [relationship to head of household] = “self” (1), including
unaccompanied minors correctly marked
as the HoH.

### Determining Length of Stay (LOS)

This report includes questions regarding persons’ total length of participation in a given project. This
report uses the Length of Stay method defined in the HMIS Reporting Glossary to make these
calculations. There are three Length of Stay methods defined in the HMIS Reporting Glossary; the method
used should be determined by the project type associated with the enrollment.
Determining a Client’s Relevant Annual Assessment
Several questions in this report utilize Annual Assessment ([data collection stage] = 5) data on stayers
where the head of household is in the project 365 days or more. Furthermore, this report requires data
from the specific Annual Assessment on the client’s anniversary most relevant to the [report date range].
The instructions for determining a client’s relevant annual assessment can be found in the HMIS Reporting
Glossary. Report questions utilizing Annual Assessment data will not repeat these instructions.

### Count Disabling Conditions

Per the HMIS Reporting Glossary, the specific conditions of a client may be reported in one of two ways:
simply as having a Special Need (elements 4.05-4.10) or as having a Disabling Condition (element 3.08).
This report utilizes both methods and identifies which is appropriate for applicable questions.

### Counting Chronically Homeless (CH)

Please see the HMIS Reporting Glossary for the latest algorithm for determining chronic homelessness
status at project start using Prior Living Situation (element 3.917).
Reporting Counts of Clients by Element by Household Type
Many questions report on distinct counts of clients, split out by each client’s household type and one or
more other client characteristic.
The programming for these questions is similar, except for which client characteristic(s) is used to report
clients on different rows.
When the client characteristic refers to a single data element, the table shells have an additional column
(Z) indicating which response option to the data element places a client into that row. This column should
not be output by the HMIS; it is only used to aid in programming.
As with most questions on this report, each client in the universe for that question should be counted
exactly once according to element and household type, then again in the total column and row.
Because of the relative simplicity of programming these table shells, the instructions on these questions
will be minimal.
Unknown Data Standards
Without With Children With Only Household Response
Total Children and Adults Children Type Options
Yes 1
No 0
Client Doesn’t
Know/Prefers Not 8 or 9
to Answer

|  |  |  | Total | Without Children | With Children and Adults | With Only Children |  | Unknown |  |  | Data Standards |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  | Household |  |  | Response |  |
|  |  |  |  |  |  |  |  | Type |  |  | Options |  |
|  | Yes |  |  |  |  |  |  |  |  |  | 1 |  |
|  | No |  |  |  |  |  |  |  |  |  | 0 |  |
|  | Client Doesn’t |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | Know/Prefers Not |  |  |  |  |  |  |  |  |  |  |  |
|  | to Answer |  |  |  |  |  |  |  |  |  |  |  |


| Without |
| --- |
| Children |


| With Children |
| --- |
| and Adults |


| With Only |
| --- |
| Children |

Unknown Data Standards
Without With Children With Only Household Response
Total Children and Adults Children Type Options
Data Not Collected 99
Total

|  |  |  | Total | Without Children | With Children and Adults | With Only Children |  | Unknown |  |  | Data Standards |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  | Household |  |  | Response |  |
|  |  |  |  |  |  |  |  | Type |  |  | Options |  |
|  | Data Not Collected |  |  |  |  |  |  |  |  |  | 99 |  |
|  | Total |  |  |  |  |  |  |  |  |  |  |  |


| Without |
| --- |
| Children |


| With Children |
| --- |
| and Adults |


| With Only |
| --- |
| Children |


## Report Details

(Questions 1-3 are NOT generated from HMIS data, and thus are not detailed in these specifications)

### Q4: HMIS Information


### Q4a: Project Identifiers in HMIS


*Report Relevance: CoC APR and ESG CAPER*

*Changes from APR FY 2024: None*

A B C D E F G H I J K L M N O P Q
Coordinated Affiliated HMIS Software
1 HMIS Project Victim Report Report Total Total
Organization Organization Project Project RRH Entry with a CoC Name and
Project IDs of Geocode Service Start End Active Active
Name ID Name ID Subtype Access Residential Number Version
Type affiliations Provider Date Date Clients Households
Point Project Number
2
Field No Other Relevant Data Standards Required Relevant Data
2.01.2 Organization Name text
2.01.1 Organization ID unique identifier
2.02.2 Project Name text
2.02.1 Project ID unique identifier
2.02.6 HMIS Project Type All projects
2.02.6A RRH Subtype If 2.02.6 = 13 then 1 or 2

|  |  |  | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Organization Name | Organization ID | Project Name | Project ID | HMIS Project Type | RRH Subtype | Coordinated Entry Access Point | Affiliated with a Residential Project | Project IDs of affiliations | CoC Number | Geocode | Victim Service Provider | HMIS Software Name and Version Number | Report Start Date | Report End Date | Total Active Clients | Total Active Households |
|  | 2 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| Field No | Other Relevant Data Standards Required | Relevant Data |
| --- | --- | --- |
| 2.01.2 | Organization Name | text |
| 2.01.1 | Organization ID | unique identifier |
| 2.02.2 | Project Name | text |
| 2.02.1 | Project ID | unique identifier |
| 2.02.6 | HMIS Project Type | All projects |
| 2.02.6A | RRH Subtype | If 2.02.6 = 13 then 1 or 2 |

Field No Other Relevant Data Standards Required Relevant Data
Value of 2.09.1 as of [report end date] or the [CE Participation Status End
2.09.1 Coordinated Entry Access Point Date] if [report start date] <= [CE Participation Status End Date] < [report
end date] AND [CE Participation Status End Date] = [operating end date]
Is the Services Only (HMIS Project Type 6 or 13
2.02.6B (If 2.02.6 =6 or (13 and 2.02.6A = 1)), then 0 or 1
subtype 1) affiliated with a residential project?
Identify the Project IDs of the housing projects this
2.02.6C (If 2.02.6B = 1, then) unique identifier(s)
project is affiliated with
2.03.1 CoC Number
2.03.2 Geocode
2.01.3 Victim Service Provider
Universe: NA

> HMIS Reporting Glossary Reference: None


| Field No | Other Relevant Data Standards Required | Relevant Data |
| --- | --- | --- |
| 2.09.1 | Coordinated Entry Access Point | Value of 2.09.1 as of [report end date] or the [CE Participation Status End Date] if [report start date] <= [CE Participation Status End Date] < [report end date] AND [CE Participation Status End Date] = [operating end date] |
| 2.02.6B | Is the Services Only (HMIS Project Type 6 or 13 subtype 1) affiliated with a residential project? | (If 2.02.6 =6 or (13 and 2.02.6A = 1)), then 0 or 1 |
| 2.02.6C | Identify the Project IDs of the housing projects this project is affiliated with | (If 2.02.6B = 1, then) unique identifier(s) |
| 2.03.1 | CoC Number |  |
| 2.03.2 | Geocode |  |
| 2.01.3 | Victim Service Provider |  |

Programming Instructions:
1. Q4a provides descriptor information on the project that is associated with the APR being submitted,
as well as data on projects with which it is affiliated, if any. The information must be generated by the
HMIS as it will be utilized in national deduplication efforts and validation for submissions.
2. Report each project included in the APR/CAPER run on a separate line beginning on line 2.
3. Columns A through L should draw from project descriptor data elements in the HMIS.
4. Column G should show the response to 2.09.1 effective as of the project’s [operating end date] if
[operating end date] >= [report start date] and [operating end date] < [report end date], else as of
[report end date]. This element is a transactional data element, and only the most recent value for the
report period is displayed.
5. Columns I, J, and K may have multiple values for a single project. Supply multiple values as a comma-
separated list.
6. Column M should contain the general product name of the HMIS and the version number, and be
automatically supplied by the system. This value is simply repeated for each project (each line) of
output.
7. Columns N and O should contain the start and end dates which the user supplied in order to execute
the report. These dates are simply repeated for each project (each line) of output.
8. Column P should be a simple count of the total active clients in the project for that row. For reports
run on a single project resulting in a single row in Q4, this total will be the same as cell C2 in Q5. For
reports run on multiple projects resulting in multiple rows in Q4, the total of all the rows should match
Q5.C2.
9. Similarly, column Q should be a simple count of total active households in the project for that row. As
with column N, the total of all rows in this column should equal Q5 cells C15 + C16.
10. When generating the CSV version of this table, be sure to wrap the data in all text columns in double
quotes. Certain columns such as organization name may naturally contain a comma, and other
columns such as CoC number may contain multiple values in a comma-separated list. Double quotes
will ensure the data will be grouped and parsed in the correct columns.

### Q5: Report Validations


### Q5a: Report Validations Table


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C
Category Count of Clients for DQ Count of Clients
1
2 Total number of persons served
3 Number of adults (age 18 or over)
4 Number of children (under age 18)
5 Number of persons with unknown age
6 Number of leavers
7 Number of adult leavers
8 Number of adult and head of household leavers
9 Number of stayers
10 Number of adult stayers
11 Number of veterans
12 Number of chronically homeless persons
13 Number of youth under age 25
14 Number of parenting youth under age 25 with children
15 Number of adult heads of household
Number of child and unknown-age heads of
16
household
Heads of households and adult stayers in the project
17
365 days or more

> HMIS Reporting Glossary Reference: Data Quality Q1.


### Q6: Data Quality


*Report Relevance: CoC APR and ESG CAPER*

*Changes from APR FY 2024: Removed NbN shelters from, and added PATH-funded SSO to, row 2 of Q6f.*

Removed row referencing Gender from Q6a

|  |  |  |  | A |  |  | B |  |  | C |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Category |  |  | Count of Clients for DQ |  |  | Count of Clients |  |  |
|  | 2 |  | Total number of persons served |  |  |  |  |  |  |  |  |
|  | 3 |  | Number of adults (age 18 or over) |  |  |  |  |  |  |  |  |
|  | 4 |  | Number of children (under age 18) |  |  |  |  |  |  |  |  |
|  | 5 |  | Number of persons with unknown age |  |  |  |  |  |  |  |  |
|  | 6 |  | Number of leavers |  |  |  |  |  |  |  |  |
|  | 7 |  | Number of adult leavers |  |  |  |  |  |  |  |  |
|  | 8 |  | Number of adult and head of household leavers |  |  |  |  |  |  |  |  |
|  | 9 |  | Number of stayers |  |  |  |  |  |  |  |  |
|  | 10 |  | Number of adult stayers |  |  |  |  |  |  |  |  |
|  | 11 |  | Number of veterans |  |  |  |  |  |  |  |  |
|  | 12 |  | Number of chronically homeless persons |  |  |  |  |  |  |  |  |
|  | 13 |  | Number of youth under age 25 |  |  |  |  |  |  |  |  |
|  | 14 |  | Number of parenting youth under age 25 with children |  |  |  |  |  |  |  |  |
|  | 15 |  | Number of adult heads of household |  |  |  |  |  |  |  |  |
| 16 |  |  | Number of child and unknown-age heads of household |  |  |  |  |  |  |  |  |
| 17 |  |  | Heads of households and adult stayers in the project 365 days or more |  |  |  |  |  |  |  |  |


### Q6a: Data Quality: Personally Identifiable Information

A B C D E F
Client Doesn’t Know/ % of Issue
1
Data Element Prefers Not to Answer Information Missing Data Issues Total Rate
2 Name (3.01)
Social Security Number
3
(3.02)
4 Date of Birth (3.03)
5 Race/Ethnicity (3.04) ---
6 Overall Score --- --- ---

> HMIS Reporting Glossary Reference: Data Quality Q2.


### Q6b: Data Quality: Universal Data Elements

A B C D E F
Client Doesn’t
1 Know/Prefers Not to % of Issue
Data Element Answer Information Missing Data Issues Total Rate
2 Veteran Status (3.07)
3 Project Start Date (3.10)
Relationship to Head of
4
Household (3.15)
5 Enrollment CoC (3.16)
6 Disabling Condition (3.08)

> HMIS Reporting Glossary Reference: Data Quality Q3.


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Data Element |  |  | Client Doesn’t Know/ Prefers Not to Answer |  |  | Information Missing |  |  | Data Issues |  |  | Total |  |  | % of Issue Rate |  |  |
|  | 2 |  | Name (3.01) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  | Social Security Number (3.02) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Date of Birth (3.03) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Race/Ethnicity (3.04) |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |
|  | 6 |  | Overall Score |  |  |  | --- |  |  | --- |  |  | --- |  |  |  |  |  |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Data Element |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  | Information Missing |  |  | Data Issues |  |  | Total |  |  | % of Issue Rate |  |  |
|  | 2 |  | Veteran Status (3.07) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Project Start Date (3.10) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 |  |  | Relationship to Head of Household (3.15) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Enrollment CoC (3.16) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Disabling Condition (3.08) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


### Q6c: Data Quality: Income and Housing Data Quality

A B C D E F
Client Doesn’t
1 Know/Prefers Not to % of Issue
Data Element Answer Information Missing Data Issues Total Rate
2 Destination (3.12)
Income and Sources (4.02) at
3
Start
Income and Sources (4.02) at
4
Annual Assessment
Income and Sources (4.02) at
5
Exit

> HMIS Reporting Glossary Reference: Data Quality Q4.


### Q6d: Data Quality: Chronic Homelessness

A B C D E F G H
Number of
Approximate date Number of times months % of
1 Count of Missing time Missing time this episode started (3.917.4) (3.917.5) records
Entering into total in institution in housing (3.917.3) DK/PNTA/ DK/PNTA/ unable to
project type records (3.917.2) (3.917.2) Missing missing missing calculate
ES-EE, ES-NbN, --- ---
2 SH, Street
Outreach
TH
3
4 PH (all)

|  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  | Data Element |  | Client Doesn’t Know/Prefers Not to Answer |  |  | Information Missing |  |  | Data Issues |  |  | Total |  |  | % of Issue Rate |  |  |
|  | 2 | Destination (3.12) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  | Income and Sources (4.02) at Start |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 |  | Income and Sources (4.02) at Annual Assessment |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 5 |  | Income and Sources (4.02) at Exit |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | G |  |  | H |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  | Entering into project type |  | Count of total records |  |  | Missing time in institution (3.917.2) |  |  | Missing time in housing (3.917.2) |  |  | Approximate date this episode started (3.917.3) Missing |  |  | Number of times (3.917.4) DK/PNTA/ missing |  |  | Number of months (3.917.5) DK/PNTA/ missing |  |  | % of records unable to calculate |  |  |
| 2 |  | ES-EE, ES-NbN, SH, Street Outreach |  |  |  |  | --- |  |  | --- |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  | TH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 | PH (all) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F G H
5 CE
SSO, Day
6
Shelter, HP
7 Total --- --- --- --- ---

> HMIS Reporting Glossary Reference: Data Quality Q5.


### Q6e: Data Quality: Timeliness

A B C
1 Time for Record Entry Number of Project Start Records Number of Project Exit Records
2 < 0 days
3 0 days
4 1-3 days
5 4-6 days
6 7-10 days
7 11+ days

> HMIS Reporting Glossary Reference: Data Quality Q6.


### Q6f: Data Quality: Inactive Records: Street Outreach and Emergency Shelter

A B C D
1 Data Element # of Records # of Inactive Records % of Inactive Records
Contact (Adults and Heads of Household in Street
2
Outreach or PATH-funded SSO)
3 Bed Night (All clients in ES – NbN)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  | G |  |  | H |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 5 |  | CE |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 6 |  |  | SSO, Day Shelter, HP |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | Total |  |  |  |  |  | --- |  |  | --- |  |  | --- |  |  | --- |  |  | --- |  |  |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  | Time for Record Entry |  |  | Number of Project Start Records |  |  | Number of Project Exit Records |  |  |
|  | 2 |  | < 0 days |  |  |  |  |  |  |  |  |
|  | 3 |  | 0 days |  |  |  |  |  |  |  |  |
|  | 4 |  | 1-3 days |  |  |  |  |  |  |  |  |
|  | 5 |  | 4-6 days |  |  |  |  |  |  |  |  |
|  | 6 |  | 7-10 days |  |  |  |  |  |  |  |  |
|  | 7 |  | 11+ days |  |  |  |  |  |  |  |  |


|  |  |  |  | A |  | B |  |  | C |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Data Element |  |  | # of Records |  | # of Inactive Records |  | % of Inactive Records |  |  |
| 2 |  |  | Contact (Adults and Heads of Household in Street Outreach or PATH-funded SSO) |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Bed Night (All clients in ES – NbN) |  |  |  |  |  |  |  |  |  |


> HMIS Reporting Glossary Reference: Data Quality Q7.


### Q7: Persons Served


### Q7a: Number of Persons Served


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
Without With Children With Only Unknown
1
Total Children and Adults Children Household Type
2 Adults ---
3 Children ---
4 Client Doesn’t Know/Prefers Not to Answer
5 Data Not Collected
6 Total
For PSH & RRH – the total persons served who
7
moved into housing
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.20 Housing Move-In Date Only used when reporting on project types 3 and 13; and when
reporting on project type 7 with 2.06 Funding Source of HUD: Pay for
Success (35)
Universe: Active clients in the report date range

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | Adults |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 3 |  | Children |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 7 |  |  | For PSH & RRH – the total persons served who moved into housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.20 |  |  | Housing Move-In Date |  |  | Only used when reporting on project types 3 and 13; and when reporting on project type 7 with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |


> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated Household Counts and Unduplicated

Client Counts by Household Type; Handling Housing Move-In Dates
Programming Instructions:
1. All projects regardless of type: report the distinct counts of active clients by age and household type. See Reporting counts of clients by
element by household type for column instructions.
2. For row 7, when the project type is 3 or 13 or when the project type is 7 with 2.06 Funding Source of HUD: Pay for Success (35):
   a. Count all active clients with a [housing move in date] <= [report end date]. Use [housing move-in dates] that are valid for each person
as defined in the Handling Housing Move-In Dates section of the HMIS Reporting Glossary.
3. For all other project types, include row 7 but output cells B7 through F7 blank or with zeros such that the CSV version of this table should
always have the same number of rows and columns.

### Q7b: Point-in-Time Count of Persons on the Last Wednesday


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
1 Total Without Children With Children and Adults With Only Children Unknown Household Type
2 January
3 April
4 July
5 October

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | January |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | April |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | July |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | October |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.06 Project Type All projects
Only used when reporting on project types 3 and 13; and when reporting on
3.20 Housing Move-In Date
project type 7 with 2.06 Funding Source of HUD: Pay for Success (35)
Universe: Active clients on each different point-in-time date

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.06 |  |  | Project Type |  |  | All projects |  |  |
| 3.20 |  |  | Housing Move-In Date |  |  | Only used when reporting on project types 3 and 13; and when reporting on project type 7 with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |


> HMIS Reporting Glossary Reference: Active Clients; Date of Birth / Age; Household Types; Unduplicated

Household Counts; and Unduplicated Client Counts by Household Type; Handling Housing Move-in Dates.
Programming Instructions:
1. Use the latest possible month if the month appears more than once in the report date range (i.e., if the
range is more than one year).
2. Because the question is reporting project occupancy, use all available enrollment data for clients in
the project – not just each person’s latest one – to ensure correct occupancy for each different point
in time date.
3. For consistency with other questions, each client should be reported using their household type as of
their latest relevant enrollment, which may differ from their household type on the particular point in
time date.
4. For project types 3 and 13 (Permanent Supportive Housing and Rapid Re-Housing) and project type 7
with 2.06 Funding Source of HUD: Pay for Success (35): report the total count of all persons in the
project with a [housing move-in date] on or before the LAST WEDNESDAY of January, April, July, and
October, respectively. Use housing move-in dates that are valid for each person as defined in the
Handling Housing Move-In Dates section of the HMIS Reporting Glossary.
   a. [project start date] <= [point in time date]
   b. AND [project exit date] is null or > [point in time date]
   c. AND [housing move-in date] <= [point in time date]
5. For all other project types: Report the total count of all persons in the project on the LAST
WEDNESDAY of January, April, July, and October falling with the report date range.
6. For all residential project types (types 0, 2, 3, 8, 9, 10, and 13), the client must not be exited on the
point in time date in order to be included ([project exit date] is null or > [point in time date]).
7. For other project types (4, 6, 7, 11, 12, 14), the client’s [project exit date] may be on the point in time
date and still be included on that date.
8. Night-by-night shelters (project type 1) must use bed night records indicating household presence on
each point in time night.

### Q8: Households Served


### Q8a: Number of Households Served


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
Without With Children With Only Unknown
1
Total Children and Adults Children Household Type
2 Total Households
For PSH & RRH – the total households
3
served who moved into housing
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
Only used when reporting on project types 3 and 13; and when
3.20 Housing Move-In Date reporting on project type 7 with 2.06 Funding Source of HUD: Pay for
Success (35)
Universe: Active households in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth / Age; Household Types; Unduplicated Household Counts; and

Unduplicated Client Counts by Household Type; Handling Housing Move-In Dates
Programming Instructions:

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | Total Households |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  | For PSH & RRH – the total households served who moved into housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.20 |  |  | Housing Move-In Date |  |  | Only used when reporting on project types 3 and 13; and when reporting on project type 7 with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |

1. Q8a reports the total number of households served during the report date range. Information on households served must be reported in
total and by household type. The “Total number of households” column is an unduplicated count of distinct households served during the
report date range. See Determining Each Client’s Household Type and Counting Distinct Households for additional instruction. Q8a also
reports on [housing move in date]. Use [housing move-in dates] that are valid for each person as defined in the Handling Housing Move-In
Dates section of the HMIS Reporting Glossary.
2. For row 3, when the project type is 3 or 13 or when the project type is 7 with 2.06 Funding Source of HUD: Pay for Success (35):
   a. Count all households where the head of household record indicates a [housing move in date] <= [report end date].
   b. If the [housing move in date] is blank or > [report end date], do not count that client.
3. For all other project types, include row 3 but leave cells B3 through F3 blank or with zeros. Therefore, the CSV version of this table should
always have the same number of rows and columns.

### Q8b: Point-in-Time Count of Households on the Last Wednesday


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
1 Total Without Children With Children and Adults With Only Children Unknown Household Type
2 January
3 April
4 July
5 October

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | January |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | April |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | July |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | October |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
Only used when reporting on project types 3 and 13; and when
3.20 Housing Move-In Date reporting on project type 7 with 2.06 Funding Source of HUD: Pay for
Success (35)
Universe: Active households in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Bed night; Date of Birth / Age; Household Types; Unduplicated Household Counts; and

Unduplicated Client Counts by Household Type; Handling Housing Move-In Dates.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.20 |  |  | Housing Move-In Date |  |  | Only used when reporting on project types 3 and 13; and when reporting on project type 7 with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |

Programming Instructions:
1. Q8b reports the point in time number of households served on the last Wednesday in January, April,
July, and October. Information on households served must be reported in total and by household type.
The “Total number of households” column is an unduplicated count of distinct households served on
the point in time date in the given month.
2. Use the latest possible month if the month appears more than once in the report date range (i.e., if the
range is more than one year).
3. Because the question is reporting project occupancy, use all available enrollment data for clients in
the project – not just each person’s latest one – to ensure correct occupancy for each different point
in time date.
4. Report the distinct counts of household at a point in time in total and by household type. See
Determining Each Client’s Household Type and Counting Distinct Households for column instructions.
Note that households (i.e., heads of household) reported at any point in the report date range are
reported according to the household type from their latest project stay – even if that is not the
household makeup present on the point in time.
5. For all residential project types (types 0, 1, 2, 3, 8, 9, 10, and 13), there must be at least one client active
in the household on the point in time date for the household to be included ([project exit date] is null
or > [point in time date]).
6. For project types 3 and 13 or when the project type is 7 with 2.06 Funding Source of HUD: Pay for
Success (35):
   a. Report the total count of all heads of household in the project with a move-in date on or before
the LAST WEDNESDAY of January, April, July, and October, respectively. Use [housing move-in
dates] that are valid for each person as defined in the Handling Housing Move-In Dates section of
the HMIS Reporting Glossary.
   i. [project start date] <= [point in time date]
ii. AND [project exit date] is null or > [point in time date]
   b. AND [housing move-in date] <= [point in time date]
7. For all other project types: Report the total count of all households in the project on the LAST
WEDNESDAY of January, April, July, and October falling with the report date range.
8. Night-by-night shelters must use bed night records indicating household presence on each point in
time night.

### Q9: Contacts and Engagements


### Q9a: Number of Persons Contacted


### Q9b: Number of Persons Newly Engaged


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E
First contact – NOT First contact – WAS First contact –
1 Number of Persons All Persons staying on the Streets, ES, staying on Streets, ES, or Worker unable to
Contacted Contacted or SH SH determine
2 Once
3 2-5 Times
4 6-9 Times
5 10+ Times
6 Total Persons Contacted
A B C D E
First contact – NOT First contact – WAS First contact –
1 Number of Persons All Persons staying on the Streets, ES, staying on Streets, ES, or Worker unable to
Newly Engaged Contacted or SH SH determine
2 Once
3 2-5 Contacts
4 6-9 Contacts
5 10+ Contacts
6 Total Persons Engaged
7 Rate of Engagement =B6/(Q9a.B6) =C6/(Q9a.C6) =D6/(Q9a.D6) =E6/(Q9a.E6)

|  |  |  |  | A |  |  | B | C | D |  |  | E |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Number of Persons Contacted |  |  | All Persons Contacted |  | First contact – NOT staying on the Streets, ES, or SH | First contact – WAS staying on Streets, ES, or SH |  | First contact – Worker unable to determine |  |  |
|  | 2 |  | Once |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 2-5 Times |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 6-9 Times |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 10+ Times |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Total Persons Contacted |  |  |  |  |  |  |  |  |  |  |


|  |  |  |  | A |  |  | B | C | D |  |  | E |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Number of Persons Newly Engaged |  |  | All Persons Contacted |  | First contact – NOT staying on the Streets, ES, or SH | First contact – WAS staying on Streets, ES, or SH |  | First contact – Worker unable to determine |  |  |
|  | 2 |  | Once |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 2-5 Contacts |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 6-9 Contacts |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 10+ Contacts |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Total Persons Engaged |  |  |  |  |  |  |  |  |  |  |
| 7 |  |  | Rate of Engagement |  |  | =B6/(Q9a.B6) |  | =C6/(Q9a.C6) | =D6/(Q9a.D6) |  | =E6/(Q9a.E6) |  |  |

Other Relevant Data Standards
Field No Relevant Data
Required
2.02.06 Project Type 1 (ES – Night-by-Night), 4 (Street Outreach)
4.12.1 Information Date (date of contact) mm/dd/yyyy
4.12.2 Current Living Situation all
4.13 Date of Engagement mm/dd/yyyy
Universe:

### Q9a: Adults and Heads of Household who have either or both:

1. a [current living situation] in the report date range that is <= [date of engagement] (or the [date of
engagement] is null),
2. or [date of engagement] in the report date range.

### Q9b: Adults and Heads of Household with a [date of engagement] in the date range.


> HMIS Reporting Glossary Reference: Active Clients; Contact; Date of Engagement

Programming Instructions:
Q9a reports the number of persons contacted, how many times they were contacted, and in which type
of location the first contact occurred.
1. Columns C-E represent each different [current living situation]. Count the total number of clients using
data from their latest project stay in the [report date range] by the [current living situation] of the
client’s earliest contact.
   a. Column C = response 17 (“Other”) or any response in 200:499
   b. Column D = any response in 100:199
   c. Column E = any response in 1:99, excluding response 17 (“Other”)
2. Include all contacts in each clients’ count where all of the following are true. Note that contacts prior
to the [report start date] are included in each person’s total count, provided those contacts are
attached to the client’s latest relevant project stay. Contacts dated after the [date of engagement],
[project exit date], and [report end date] are all excluded.
   a. [date of contact] >= [project start date]
   b. [project exit date] is null or [date of contact] <= [project exit date]
   c. [current living situation] <= [date of engagement] (or the [date of engagement] is null)

| Field No |  | Other Relevant Data Standards |  | Relevant Data |
| --- | --- | --- | --- | --- |
|  |  | Required |  |  |
| 2.02.06 | Project Type |  |  | 1 (ES – Night-by-Night), 4 (Street Outreach) |
| 4.12.1 | Information Date (date of contact) |  |  | mm/dd/yyyy |
| 4.12.2 | Current Living Situation |  |  | all |
| 4.13 | Date of Engagement |  |  | mm/dd/yyyy |

   d. [current living situation] <= [report end date]
3. If there is no [current living situation] on the [date of engagement], also count the [date of
engagement] as 1 contact.
4. If there are no [current living situation] records at all and the [date of engagement] is effectively the
only contact, report the client in cell E2.
5. Rows 2-5 represent the number of times a client was contacted. Determine the total number of times
a client was contacted for each applicable record.
   a. Row 2 = Count each person where [contact] = 1 by [current living situation].
   b. Row 3 = Count each person where ([contact] >=2 and [contact] <=5) by [current living situation].
   c. Row 4 = Count each person where ([contact] >=6 and [contact] <=9) by [current living situation].
   d. Row 5 = Count each person where [contact] >=10 by [current living situation].
   e. Row 6 = Unduplicated count of persons with Contacts during the operating year.
Q9b reports all persons contacted for which a [date of engagement] is recorded based upon how many
times they were contacted up to and including the [date of engagement], and in which type of location
the first contact occurred. It also calculates a rate of engagement by dividing the number of persons
contacted during the report range by the number of persons engaged (both in total and by location of
first contact).
1. Use the same logic as for Q9a but limit the universe of clients to those who were engaged during the
report date range as described in the HMIS Reporting Glossary.

### Q11: Age


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
Without With Children With Only Unknown
1
Total Children and Adults Children Household Type
2 Under 5 ---
3 5-12 ---
4 13-17 ---
5 18-24 ---
6 25-34 ---
7 35-44 ---
8 45-54 ---
9 55-64 ---
10 65+ ---
Client Doesn’t Know/Prefers Not to
11
Answer
12 Data Not Collected
13 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated Household Counts; and

Unduplicated Client Counts by Household Type.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | Under 5 |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 5-12 |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 13-17 |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 18-24 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 6 |  | 25-34 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 7 |  | 35-44 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 8 |  | 45-54 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 9 |  | 55-64 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 10 |  | 65+ |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
| 11 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |

Programming Instructions:
Report the distinct counts of clients by age bracket and household type. See Reporting counts of clients by element by household type for
column instructions.

### Q12: Race and Ethnicity


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F Z
Unknown Data Standards
1 Without With Children With Only Household Response
Total Children and Adults Children Type options
American Indian, Alaska Native, or
2 1
Indigenous
3 Asian or Asian American 2
4 Black, African American, or African 3
5 Hispanic/Latina/o 6
6 Middle Eastern or North African 7
7 Native Hawaiian or Pacific Islander 4
8 White 5
Asian or Asian American & American
9 2 & 1
Indian, Alaska Native, or Indigenous
Black, African American, or African &
10 American Indian, Alaska Native, or 3 & 1
Indigenous

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 2 |  |  | American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |  |
|  | 3 |  | Asian or Asian American |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 2 |  |
|  | 4 |  | Black, African American, or African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 3 |  |
|  | 5 |  | Hispanic/Latina/o |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 |  |
|  | 6 |  | Middle Eastern or North African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 7 |  |
|  | 7 |  | Native Hawaiian or Pacific Islander |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 |  |
|  | 8 |  | White |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 |  |
| 9 |  |  | Asian or Asian American & American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 2 & 1 |  |  |
| 10 |  |  | Black, African American, or African & American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 3 & 1 |  |  |

A B C D E F Z
Unknown Data Standards
1 Without With Children With Only Household Response
Total Children and Adults Children Type options
Hispanic/Latina/o & American Indian,
11 6 & 1
Alaska Native, or Indigenous
Middle Eastern or North African &
12 American Indian, Alaska Native, or 7 & 1
Indigenous
Native Hawaiian or Pacific Islander &
13 American Indian, Alaska Native, or 4 & 1
Indigenous
White & American Indian, Alaska
14 5 & 1
Native, or Indigenous
Black, African American, or African &
15 3 & 2
Asian or Asian American
Hispanic/Latina/o & Asian or Asian
16 6 & 2
American
Middle Eastern or North African &
17 7 & 2
Asian or Asian American
Native Hawaiian or Pacific Islander &
18 4 & 2
Asian or Asian American
19 White & Asian or Asian American 5 & 2
Hispanic/Latina/o & Black, African
20 6 & 3
American, or African
Middle Eastern or North African &
21 7 & 3
Black, African American, or African
Native Hawaiian or Pacific Islander &
22 4 & 3
Black, African American, or African

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 11 |  |  | Hispanic/Latina/o & American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 & 1 |  |  |
| 12 |  |  | Middle Eastern or North African & American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 7 & 1 |  |  |
| 13 |  |  | Native Hawaiian or Pacific Islander & American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 & 1 |  |  |
| 14 |  |  | White & American Indian, Alaska Native, or Indigenous |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 & 1 |  |  |
| 15 |  |  | Black, African American, or African & Asian or Asian American |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 3 & 2 |  |  |
| 16 |  |  | Hispanic/Latina/o & Asian or Asian American |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 & 2 |  |  |
| 17 |  |  | Middle Eastern or North African & Asian or Asian American |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 7 & 2 |  |  |
| 18 |  |  | Native Hawaiian or Pacific Islander & Asian or Asian American |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 & 2 |  |  |
|  | 19 |  | White & Asian or Asian American |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 & 2 |  |
| 20 |  |  | Hispanic/Latina/o & Black, African American, or African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 & 3 |  |  |
| 21 |  |  | Middle Eastern or North African & Black, African American, or African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 7 & 3 |  |  |
| 22 |  |  | Native Hawaiian or Pacific Islander & Black, African American, or African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 & 3 |  |  |

A B C D E F Z
Unknown Data Standards
1 Without With Children With Only Household Response
Total Children and Adults Children Type options
White & Black, African American, or
23 5 & 3
African
Middle Eastern or North African &
24 7 & 6
Hispanic/Latina/o
Native Hawaiian or Pacific Islander &
25 4 & 6
Hispanic/Latina/o
26 White & Hispanic/Latina/o 5 & 6
Native Hawaiian or Pacific Islander &
27 4 & 7
Middle Eastern or North African
White & Middle Eastern or North
28 5 & 7
African
White & Native Hawaiian or Pacific
29 5 & 4
Islander
Multiracial – more than 2
6 & two or more
30 races/ethnicity, with one being
of 1, 2, 3, 4, 5, or 7
Hispanic/Latina/o
Multiracial – more than 2 races, Three or more of
31
where no option is Hispanic/Latina/o 1, 2, 3, 4, 5, or 7
Client Doesn’t Know/Prefers Not to
32 8 or 9
Answer
33 Data Not Collected 99
34 Total

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 23 |  |  | White & Black, African American, or African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 & 3 |  |  |
| 24 |  |  | Middle Eastern or North African & Hispanic/Latina/o |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 7 & 6 |  |  |
| 25 |  |  | Native Hawaiian or Pacific Islander & Hispanic/Latina/o |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 & 6 |  |  |
|  | 26 |  | White & Hispanic/Latina/o |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 & 6 |  |
| 27 |  |  | Native Hawaiian or Pacific Islander & Middle Eastern or North African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 & 7 |  |  |
| 28 |  |  | White & Middle Eastern or North African |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 & 7 |  |  |
| 29 |  |  | White & Native Hawaiian or Pacific Islander |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 & 4 |  |  |
| 30 |  |  | Multiracial – more than 2 races/ethnicity, with one being Hispanic/Latina/o |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 6 & two or more of 1, 2, 3, 4, 5, or 7 |  |  |
| 31 |  |  | Multiracial – more than 2 races, where no option is Hispanic/Latina/o |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Three or more of |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1, 2, 3, 4, 5, or 7 |  |
| 32 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | 33 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 34 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| 6 & two or more |
| --- |
| of 1, 2, 3, 4, 5, or 7 |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.04 Race 1, 2, 3, 4, 5, 6, 7, 8, 9, 99
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated Household Counts; and

Unduplicated Client Counts by Household Type.
Programming Instructions:
Report the distinct counts of clients by race and household type. See Reporting counts of clients by element by household type for column
instructions.
1. Each client must be reported on one and only one row
2. Use column Z to determine on which row to report a client.
   a. Rows 2 through 8 and 32 represent records with only one response option selected.
   b. Rows 9 through 29 represent records with two response options (all combinations have been provided). Select each person where
distinct count [race] > 1 and [race] in (1, 2, 3, 4, 5,6,7).
   c. Row 30 indicates at least 3 response options were identified and one of which is Hispanic/Latina/o (6)
   d. Row 31 indicates at least 3 response options were identified none of which is Hispanic/Latina/o (6)
3. As specified in the Data Standards, responses 8, 9 and 99 are only valid when no other response is indicated. If they are present with
other responses, they should be ignored for the purposes of categorizing a client. For instance, if a client has 2, 4, and 8 selected as [race]
responses, the 8 response should be disregarded and the client should be reported in row 18.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.04 |  |  | Race |  |  | 1, 2, 3, 4, 5, 6, 7, 8, 9, 99 |  |  |


### Q13: Physical and Mental Health Conditions


### Q13a1: Physical and Mental Health Conditions at Start


### Q13b1: Physical and Mental Health Conditions at Exit


### Q13c1: Physical and Mental Health Conditions for Stayers


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F G Z
Data
Adults in HH Children in HH Unknown Standards
1
Total Without with Children with Children With Only Household Response
Persons Children & Adults & Adults Children Type options
2 Mental Health Disorder 1
3 Alcohol Use Disorder 1
4 Drug Use Disorder 2
Both Alcohol and Drug Use 3
5
Disorders
6 Chronic Health Condition 1
7 HIV/AIDS 1
8 Developmental Disability 1
9 Physical Disability 1

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | G |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total Persons |  |  | Without Children |  |  | Adults in HH with Children & Adults |  |  | Children in HH with Children & Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | Mental Health Disorder |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 3 |  | Alcohol Use Disorder |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 4 |  | Drug Use Disorder |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 2 |  |
| 5 |  |  | Both Alcohol and Drug Use Disorders |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 3 | 3 |  |
|  | 6 |  | Chronic Health Condition |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 7 |  | HIV/AIDS |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 8 |  | Developmental Disability |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 9 |  | Physical Disability |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.05 Physical Disability 1
4.06 Developmental Disability 1
4.07 Chronic Health Condition 1
4.08 HIV/AIDS 1
4.09 Mental Health Disorder 1
4.10 Substance Use Disorder 1, 2, 3
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated Household Counts; and Unduplicated

Client Counts by Household Type.
Programming Instructions: Report on the distinct counts of clients by Special Need
1. In 13a1 - based on the record from project start ([data collection stage] = 1) from their latest project stay.
2. In 13b1 - based on the record from project exit ([data collection stage] = 3) from their latest project stay.
3. In 13c1 - based on the record from their latest data available, regardless of [data collection stage], where the [information date] <= [report
end date].
4. Report clients according to each special need listed only when there is a definite “yes” indicator in the field (value = 1, 2 or 3). Values of
null, 8, 9, or 99 are completely ignored.
5. See Reporting counts of clients by element by household type for column instructions. For Households with Children and Adults:
   a. Report all adults in the household in column D.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.05 |  |  | Physical Disability |  |  | 1 |  |  |
| 4.06 |  |  | Developmental Disability |  |  | 1 |  |  |
| 4.07 |  |  | Chronic Health Condition |  |  | 1 |  |  |
| 4.08 |  |  | HIV/AIDS |  |  | 1 |  |  |
| 4.09 |  |  | Mental Health Disorder |  |  | 1 |  |  |
| 4.10 |  |  | Substance Use Disorder |  |  | 1, 2, 3 |  |  |

   b. Report children in column E.
   c. Report other household members with an unknown age who are in that household type in column G.

### Q13a2: Number of Conditions at Start


### Q13b2: Number of Conditions at Exit


### Q13c2: Number of Conditions for Stayers


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F G
Adults in HH Children in HH Unknown
1 Without with Children & with Children & With Only Household
Total Persons Children Adults Adults Children Type
2 None
3 1 Condition
4 2 Conditions
5 3+ Conditions
6 Condition Unknown
Client Doesn’t Know/
7
Prefers Not to Answer
8 Data Not Collected
9 Total

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | G |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total Persons |  |  | Without Children |  |  | Adults in HH with Children & Adults |  |  | Children in HH with Children & Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | None |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 1 Condition |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 2 Conditions |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 3+ Conditions |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Condition Unknown |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 7 |  |  | Client Doesn’t Know/ Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.08 Disabling Condition 0, 1, 8, 9, 99
4.05 Physical Disability 1
4.06 Developmental Disability 1
4.07 Chronic Health Condition 1
4.08 HIV/AIDS 1
4.09 Mental Health Disorder 1
4.10 Substance Use Disorder 1, 2, 3
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Household Types; Unduplicated Household Counts and Unduplicated Client Counts by

Household Type
Programming Instructions:

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.08 |  |  | Disabling Condition |  |  | 0, 1, 8, 9, 99 |  |  |
| 4.05 |  |  | Physical Disability |  |  | 1 |  |  |
| 4.06 |  |  | Developmental Disability |  |  | 1 |  |  |
| 4.07 |  |  | Chronic Health Condition |  |  | 1 |  |  |
| 4.08 |  |  | HIV/AIDS |  |  | 1 |  |  |
| 4.09 |  |  | Mental Health Disorder |  |  | 1 |  |  |
| 4.10 |  |  | Substance Use Disorder |  |  | 1, 2, 3 |  |  |

Report on the total number of conditions each client has
1. In 13a2 - based on the record from project start ([data collection stage] = 1) from their latest project
stay.
2. In 13b2 - based on the record from project exit ([data collection stage] = 3) from their latest project
stay.
3. In 13c2 - based on the record from their latest data available ([data collection stage] = 5, 2 or 1), where
the [information date] <= [report end date].
4. Report each client on lines 3 through 5 according to the number of affirmative responses (“yes” or “1”)
in elements 4.05, 4.06, 4.07, 4.08, 4.09, and 4.10 recorded at the relevant data collection stage as
described above. For element 4.10, a response of 1 (“Alcohol Use Disorder”) or 2 (“Drug Use Disorder”)
counts as 1 condition. A response of 3 (“Both alcohol and drug use disorders”) counts as 2 conditions.
5. For records where the responses to elements 4.05, 4.06, 4.07, 4.08, 4.09, and 4.10 are all 0, 8, 9, or 99,
use [disabling condition] to report the client on line 2 (response = 0), 6 (response = 1), 7 (response = 8
or 9), or 8 (response = 99 or null). Do not use [disabling condition] otherwise.
6. See Reporting counts of clients by element by household type for column instructions. For
Households with Children and Adults:
   a. Report all adults in the household in column D
   b. Report children in column E
   c. Report other household members with an unknown age who are in that household type in column
G.

### Q14: Domestic Violence, Sexual Assault, Dating Violence, Stalking, or Human

Trafficking

### Q14a: History of Domestic Violence, Sexual Assault, Dating Violence, Stalking, or

Human Trafficking

*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F Z
With Data
Children Unknown Standards
1
Without and With Only Household Response
Total Children Adults Children Type options
2 Yes 1
3 No 0
Client Doesn’t 8 or 9
4 Know/Prefers Not to
Answer
5 Data Not Collected 99
6 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.11.2 Survivor of Domestic Violence All
Universe: Adults and heads of household active in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated

Household Counts; and Unduplicated Client Counts by Household Type.
Programming Instructions: Report the distinct counts of heads of households and adult history of
domestic violence. See Reporting counts of clients by element by household type for column instructions.
Use the latest [domestic violence] from the latest project stay for each client where the [information
date] <= [report end date].

### Q14b: Most recent experience of domestic violence, sexual assault, dating violence,

stalking, or human trafficking

*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | Yes |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 3 |  | No |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 0 |  |
| 4 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 | 8 or 9 |  |
|  | 5 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.11.2 |  |  | Survivor of Domestic Violence |  |  | All |  |  |

A B C D E F Z
With Data
Children Unknown Standards
1
Without and With Only Household Response
Total Children Adults Children Type options
Within the past three 1
2
months
3 Three to six months ago 2
4 Six months to one year 3
5 One year ago, or more 4
Client Doesn’t 8 or 9
6 Know/Prefers Not to
Answer
7 Data Not Collected 99
8 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.11.2 Survivor of Domestic Violence 1
Survivor of Domestic Violence (When
4.11.2A All
experience occurred)
Universe: Heads of household and adults who reported “yes” (1) to Domestic Violence History.

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth / Age; Household Types; Unduplicated

Household Counts; and Unduplicated Client Counts by Household Type.
Programming Instructions: Of heads of household and adults who reported “yes” (1) to Domestic
Violence History, report each client according to the response to Survivor of Domestic Violence (When
experience occurred). See Reporting counts of clients by element by household type for column
instructions. Use the latest [domestic violence] from the latest project stay for each client where the
[information date] <= [report end date].

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 2 |  |  | Within the past three months |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 | 1 |  |
|  | 3 |  | Three to six months ago |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 2 |  |
|  | 4 |  | Six months to one year |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 3 |  |
|  | 5 |  | One year ago, or more |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 |  |
| 6 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 | 8 or 9 |  |
|  | 7 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 8 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.11.2 |  |  | Survivor of Domestic Violence |  |  | 1 |  |  |
| 4.11.2A |  |  | Survivor of Domestic Violence (When experience occurred) |  |  | All |  |  |


### Q15: Living Situation


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F Z
With With Unknown
1 Without Children Only Household Data Standards
Total Children and Adults Children Type Response options
2 Homeless Situations
3 Place not meant for habitation 116
Emergency shelter, including hotel or motel paid
4 for with emergency shelter voucher, Host Home 101
shelter
5 Safe Haven 118
6 Subtotal
7 Institutional Situations
8 Foster care home or foster care group home 215
Hospital or other residential non-psychiatric
9 206
medical facility
10 Jail, prison, or juvenile detention facility 207
11 Long-term care facility or nursing home 225
12 Psychiatric hospital or other psychiatric facility 204
Substance abuse treatment facility or detox
13 205
center
14 Subtotal
15 Temporary Situations
Transitional housing for homeless persons
16 302
(including homeless youth)

|  |  |  |  | A |  |  |  |  |  | B |  |  | C |  |  | D |  |  |  |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  |  |  |  | With Only Children |  |  | Unknown Household Type |  |  | Data Standards Response options |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response options |  |
|  | 2 |  |  | Homeless Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Place not meant for habitation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 116 |  |
| 4 |  |  | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 101 |  |  |
|  | 5 |  | Safe Haven |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 118 |  |
|  | 6 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  |  | Institutional Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Foster care home or foster care group home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 215 |  |
| 9 |  |  | Hospital or other residential non-psychiatric medical facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 206 |  |  |
|  | 10 |  | Jail, prison, or juvenile detention facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 207 |  |
|  | 11 |  | Long-term care facility or nursing home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 225 |  |
|  | 12 |  | Psychiatric hospital or other psychiatric facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 204 |  |
| 13 |  |  | Substance abuse treatment facility or detox center |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 205 |  |  |
|  | 14 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  |  | Temporary Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 16 |  |  | Transitional housing for homeless persons (including homeless youth) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 302 |  |  |

A B C D E F Z
With With Unknown
1 Without Children Only Household Data Standards
Total Children and Adults Children Type Response options
Residential project or halfway house with no
17 329
homeless criteria
Hotel or motel paid for without emergency shelter
18 314
voucher
19 Host Home (non-crisis) 332
Staying or living in a friend’s room, apartment, or
20 336
house
Staying or living in a family member’s room,
21 335
apartment, or house
22 Subtotal
23 Permanent Situations
24 Rental by client, no ongoing housing subsidy 410
25 Rental by client, with ongoing housing subsidy 435
26 Owned by client, with ongoing housing subsidy 421
27 Owned by client, no ongoing housing subsidy 411
28 Subtotal
29 Client Doesn’t Know/Prefers Not to Answer 8 or 9
30 Data Not Collected 99
31 Subtotal
32 TOTAL
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  | Data Standards Response options |  |  |
| 17 |  |  | Residential project or halfway house with no homeless criteria |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 329 |  |  |
| 18 |  |  | Hotel or motel paid for without emergency shelter voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 314 |  |  |
|  | 19 |  | Host Home (non-crisis) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 332 |  |
| 20 |  |  | Staying or living in a friend’s room, apartment, or house |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 336 |  |  |
| 21 |  |  | Staying or living in a family member’s room, apartment, or house |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 335 |  |  |
|  | 22 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 23 |  |  | Permanent Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 24 |  | Rental by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 410 |  |
|  | 25 |  | Rental by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 435 |  |
|  | 26 |  | Owned by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 421 |  |
|  | 27 |  | Owned by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 411 |  |
|  | 28 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 29 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |
|  | 30 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 31 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 32 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| Data Standards |
| --- |
| Response options |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |

Field No Other Relevant Data Standards Required Relevant Data
3.917 Prior Living Situation all
Universe: Adults and heads of household active in the report date range.

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated Household Counts; and Unduplicated

Client Counts by Household Type.
Programming Instructions: Report the distinct counts of adults and unaccompanied children by their living situation at project start.
See Reporting counts of clients by element by household type for column instructions.

### Q16: Cash Income - Ranges


*Report Relevance: CoC APR and ESG CAPER*

*Changes from APR FY 2024: Added clarification 2a with instructions on reporting income amounts that are not recorded in whole dollars*

A B C D
Income at Income at Latest Annual Income at Exit
1
Start Assessment for Stayers for Leavers
2 No Income
3 $1 - $150
4 $151 - $250
5 $251 - $500
6 $501 - $1,000
7 $1,001 - $1,500
8 $1,501 - $2,000
9 $2,001+

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 3.917 |  |  | Prior Living Situation |  |  | all |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Income at Start |  |  | Income at Latest Annual Assessment for Stayers |  |  | Income at Exit for Leavers |  |  |
|  | 2 |  | No Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | $1 - $150 |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | $151 - $250 |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | $251 - $500 |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | $501 - $1,000 |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | $1,001 - $1,500 |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | $1,501 - $2,000 |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | $2,001+ |  |  |  |  |  |  |  |  |  |  |  |

A B C D
Income at Income at Latest Annual Income at Exit
1
Start Assessment for Stayers for Leavers
10 Client Doesn’t Know/Prefers Not to Answer
11 Data Not Collected
12 Number of adult stayers not yet required to have an annual assessment --- ---
13 Number of adult stayers without required annual assessment --- ---
14 Total Adults
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.02 Income and Sources Earned Income and all other sources

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Income at Start |  |  | Income at Latest Annual Assessment for Stayers |  |  | Income at Exit for Leavers |  |  |
|  | 10 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Number of adult stayers not yet required to have an annual assessment |  |  |  | --- |  |  |  |  |  | --- |  |
|  | 13 |  | Number of adult stayers without required annual assessment |  |  |  | --- |  |  |  |  |  | --- |  |
|  | 14 |  | Total Adults |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |

Universe: Active adults in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth / Age; Project Stayers; Project Leavers

Programming Instructions:
1. Report using data from each adult’s latest project stay in the [report date range].
2. Rows 2 through 9 report clients according to [total income] based on the client’s record at start
(column B), annual assessment (column C) or at exit (column D). Refer to “Determining Total and
Earned Income” in the HMIS Reporting Glossary to calculate [total income] for this question.
   a. Standard rules for rounding apply: $0.49 and below rounds down to the nearest dollar, while
$0.50 and above rounds up to the nearest dollar. As an example, a monthly income amount
of $500.50 should be rounded up to $501 and reported accordingly.
3. Column B (Income at Start)
   a. For each active adult, determine the Income and Sources record with a [data collection stage] of
project start (1) attached to the selected project stay where the [information date] of the record =
[project start date].
   b. If [total income] is null and [income from any source] = 8 or 9, report the client in cell B10.
   c. If [total income] is null and [income from any source] = 99 or the record is completely missing,
report the client in cell B11.
   d. Report the total number of active adults in cell B14.
4. Column C (Income at Latest Annual Assessment for Stayers)
   a. All project stayers regardless of length of stay must be reported one time in rows 2 through 13 of
column C as well as in C14.
   b. Refer to Determining a Client’s Relevant Annual Assessment to know if a stayer is required to have
an annual assessment, and if so whether or not the relevant record is available.
   c. If the client has the required annual assessment, report the client on row 2 through 11 relative to the
[total income] and [income from any source] on that annual assessment.
   d. If the stayer is not yet required to have an annual assessment, report the client in cell C12.
   e. If the stayer is required to have an annual assessment but the necessary record is completely
missing, report the client in cell C13.
5. Column D (Income at Exit)
   a. For each adult leaver, determine the Income and Sources record with a [data collection
stage] of project exit (3) attached to the selected project stay where the [information date]
of the record = [project exit date].
   b. If [total income] is null and [income from any source] = 8 or 9, report the client in cell D10.
   c. If [total income] is null and [income from any source] = 99 or the record is completely
missing, report the client in cell D11.
   d. Report the total number of adult leavers in cell D14.

### Q17: Cash Income - Sources


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D
Income Income at Latest Income at
at Start Annual Exit for
1
Assessment for Leavers
Stayers
2 Earned Income
3 Unemployment Insurance
4 Supplemental Security Income (SSI)
5 Social Security Disability Insurance (SSDI)
6 VA Service-Connected Disability Compensation
7 VA Non-Service Connected Disability Pension
8 Private Disability Insurance
9 Worker’s Compensation
1 Temporary Assistance for Needy Families (TANF)
0
11 General Assistance (GA)
12 Retirement Income from Social Security
13 Pension or retirement income from a former job
14 Child Support
15 Alimony and other spousal support
16 Other Source
Adults with Income Information at Start and Annual ---
17
Assessment/Exit

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Income at Start |  |  | Income at Latest Annual Assessment for Stayers |  |  | Income at Exit for Leavers |  |  |
|  | 2 |  | Earned Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Unemployment Insurance |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Supplemental Security Income (SSI) |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Social Security Disability Insurance (SSDI) |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | VA Service-Connected Disability Compensation |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | VA Non-Service Connected Disability Pension |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Private Disability Insurance |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | Worker’s Compensation |  |  |  |  |  |  |  |  |  |  |  |
|  | 1 |  | Temporary Assistance for Needy Families (TANF) |  |  |  |  |  |  |  |  |  |  |  |
|  | 0 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | General Assistance (GA) |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Retirement Income from Social Security |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | Pension or retirement income from a former job |  |  |  |  |  |  |  |  |  |  |  |
|  | 14 |  | Child Support |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Alimony and other spousal support |  |  |  |  |  |  |  |  |  |  |  |
|  | 16 |  | Other Source |  |  |  |  |  |  |  |  |  |  |  |
| 17 |  |  | Adults with Income Information at Start and Annual Assessment/Exit |  |  | --- |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.02 Income and Sources Earned Income and all other sources
Universe: Active Adults in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Project Leavers; Project Stayers

Programming Instructions:
1. Report using data from each adult’s latest project stay in the [report date range].
2. Rows 2 through 16 report clients according to income sources indicated as “yes” (1) on the client’s
record at start (column B), annual assessment (column C) or at exit (column D).
3. Column B (Income at Start)
   a. For each active adult, determine the Income and Sources record with a [data collection stage] of
project start (1) attached to the selected project stay where the [information date] of the record =
[project start date].
   b. Report the adult as having the income source if the record indicates “yes” (1) to that source.
4. Column C (Income at Latest Annual Assessment for Stayers)
   a. Refer to Determining a Client’s Relevant Annual Assessment to know if a stayer is required to have
an annual assessment, and if so whether or not the relevant record is available.
   b. If the stayer has the required annual assessment,
   i. Report the adult on row 2 through 16 according to any income sources indicated as “yes” (1) on
that annual assessment.
ii. If the [income from any source] element (4.02.2) on the annual assessment AND the [income
from any source] on the income record from project start are both 0 or 1 (i.e. income data is
known for both data points, even if it is known to be zero), report the client in C17. If either or
both of the [income and sources] records are completely missing, or the [income from any
source] field on either record is 8, 9, 99, or missing, do not count the client in cell C17.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |

   c. If the stayer is not yet required to have an annual assessment, do not report that client in this
question.
5. Column D (Income at Exit)
   a. For each adult leaver, determine the Income and Sources record with a [data collection stage] of
project exit (3) attached to the selected project stay where the [information date] of the record =
[project exit date].
   b. If the leaver has the required record,
   i. Report the adult on row 2 through 16 according to any income sources indicated as “yes” (1) on
that record.
ii. If the [income from any source] element (4.02.2) on the income record at exit AND the [income
from any source] on the income record from project start are both 0 or 1 (i.e. income data is
known for both data points, even if it is known to be zero), report the client in D17. If either or
both of the [income and sources] records are completely missing, or the [income from any
source] field on either record is 8, 9, 99, or missing, do not count the client in cell D17.
6. Clients reported in cells C17 and D17 – those with two usable data points for income comparisons –
are the universe of clients for questions 19a1 and 19a2.

### Q18: Client Cash Income Category - Earned/Other Income Category - by Start and Annual

Assessment/Exit Status

*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D
Number of Adults at
1 Number of Annual Assessment Number of Adults at
Adults at Start (Stayers) Exit (Leavers)
2 Adults with Only Earned Income (i.e., Employment Income)
3 Adults with Only Other Income
4 Adults with Both Earned and Other Income
5 Adults with No Income
Adults with Client Doesn’t Know/Prefers Not to Answer Income
6
Information
7 Adults with Missing Income Information
8 Number of adult stayers not yet required to have an annual assessment --- ---
9 Number of adult stayers without required annual assessment --- ---
10 Total Adults
11 1 or more source of income
12 Adults with Income Information at Start and Annual Assessment/Exit ---

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Number of Adults at Start |  |  | Number of Adults at Annual Assessment (Stayers) |  |  | Number of Adults at Exit (Leavers) |  |  |
|  | 2 |  | Adults with Only Earned Income (i.e., Employment Income) |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Adults with Only Other Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Adults with Both Earned and Other Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Adults with No Income |  |  |  |  |  |  |  |  |  |  |  |
| 6 |  |  | Adults with Client Doesn’t Know/Prefers Not to Answer Income Information |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | Adults with Missing Income Information |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Number of adult stayers not yet required to have an annual assessment |  |  |  | --- |  |  |  |  |  | --- |  |
|  | 9 |  | Number of adult stayers without required annual assessment |  |  |  | --- |  |  |  |  |  | --- |  |
|  | 10 |  | Total Adults |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | 1 or more source of income |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Adults with Income Information at Start and Annual Assessment/Exit |  |  |  | --- |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.02 Income and Sources Earned Income and all other sources
Universe: Active adults in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Project Leavers; Project Stayers

Programming Instructions:
1. Report using data from each adult’s latest project stay in the [report date range].
2. The [total income] on a specific Income and Sources record is required to determine “other income”.
Refer to “Determining Total and Earned Income” in the HMIS Reporting Glossary to calculate [total
income] for this question.
3. “Earned income” reports on adults with earned income at start, annual assessment, or exit as
appropriate to the column, with an associated dollar amount > $0.00. If the response to [earned
income] is ‘Yes’ but no amount is recorded in element 4.02.3.A, do not report the person as having
earned income.
4. “Other income” reports on adults with [other income] = [total income] minus [earned income]. If the
response to [earned income] is ‘Yes’ but no amount is recorded, or if the person has a total monthly
income without any specific sources and dollars for those sources specified, assume that [total
income] is entirely “other income”.
5. Adults with Only Earned Income (row 2) = A count of all adults with only [earned income] > $0 and no
[other income].
6. Adults with Only Other Income (row 3) = A count of all adults with [other income] > $0 and who have
no [earned income].
7. Adults with Both Earned Income and Other Income (row 4) = A count of all adults with both [earned
income] and [other income], both greater than zero.
8. Adults with No Income (row 5) = a count of all adults with [total income] of $0.00.
9. Adults with Doesn’t Know/Prefers Not to Answer Income Information (row 6) = a count of all adults
who did not know or preferred not to disclose their income, as calculated using “Determining Total and
Earned Income” in the HMIS Reporting Glossary .
10. Adults with Missing Income Information (row 7) = a count of all adults who have a missing [total
income] as calculated using “Determining Total and Earned Income” in the HMIS Reporting Glossary or,

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |

for columns B and D, whose relevant Income and Sources record is completely missing. Stayers whose
annual assessment is completely missing are reported in row 9.
11. Number of adult stayers not yet required to have an annual assessment (row 8) and Number of
adult stayers without required annual assessment (row 9) – see #15 below.
12. Total adults (row 10) = the total number of adults active during the [report date range]. Note that the
total adults in Number of adults at start column should be equal to the total adults in the Number of
adults at annual assessment column plus the Number of adults at exit column.
13. 1 or more source of Income (row 11) = A count of all adults with a [total income] amount > $0.00.
14. Column B (Number of Adults at Start)
   a. For each active adult use the Income and Sources record with a [data collection stage] of project
start (1) attached to the selected project stay where the [information date] of the record = [project
start date].
   b. Report the adult on rows 2 through 7 and 11 according to the above instructions using data from
that record.
   c. Report all active adults in cell B10.
15. Column C (Number of Adults at Annual Assessment (Stayers))
   a. Refer to Determining a Client’s Relevant Annual Assessment to know if a stayer is required to have
an annual assessment, and if so whether or not the relevant record is available.
   b. If the stayer has the required annual assessment,
i) Report the adult on rows 2 through 7 and 11 according to the above instructions using data from
that annual assessment.
ii) Also report the client in cell C12 if the same client has an income record from project start.
   c. If the stayer is not yet required to have an annual assessment, report the client in cell C8.
   d. If the stayer is completely missing the annual assessment record, report the client in cell C9.
   e. Report all stayers in cell C10 regardless of length of stay and presence of the required annual
assessment.
16. Column D (Number of Adults at Exit (Leavers))
   a. For each adult leaver, determine the Income and Sources record with a [data collection stage] of project exit (3) attached to the
selected project stay where the [information date] of the record = [project exit date].
   b. If the leaver has the required record,
i) Report the adult on rows 2 through 7 and 11 according to the above instructions using data from that record.
ii) Also report the client in cell D12 if the same client has an income record from project start.
   c. Report all leavers in cell D10.
17. Clients reported in cells C12 and D12 – those with two usable data points for income comparisons – are the universe of clients for
questions 19a1 and 19a2

### Q19: Cash Income – Changes over Time


### Q19a1: Client Cash Income Change - Income Source - by Start and Latest Status


### Q19a2: Client Cash Income Change - Income Source - by Start and Exit


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F G H I J
Did Not Have Performance
the Income Measure:
Income Change by Retained Retained Category at Adults who Performance
Income Category Had Income Income Income Retained Start and Did Not Have Gained or measure:
1 (Universe: Adult Category at Category But Category and Income Gained the the Income Increased Income Percent of
Stayers with Start and Did Had Less $ at Same $ at Category and Income Category at Total Adults from Start to persons who
Income Information Not Have It at Annual Annual Increased $ Category at Start or at (including Annual accomplishe
at Start and Annual Annual Assessment Assessment at Annual Annual Annual those with Assessment, d this
Assessment) Assessment Than at Start as at Start Assessment Assessment Assessment No Income) Average Gain measure
Number of
Adults with
Earned Income
2 # =I2/H2
(i.e.,
Employment
Income)
Average Change --- ---
3 in Earned $ $ --- $ $ $ ---
Income

|  | A | B | C | D | E | F | G | H | I | J |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Income Change by Income Category (Universe: Adult Stayers with Income Information at Start and Annual Assessment) | Had Income Category at Start and Did Not Have It at Annual Assessment | Retained Income Category But Had Less $ at Annual Assessment Than at Start | Retained Income Category and Same $ at Annual Assessment as at Start | Retained Income Category and Increased $ at Annual Assessment | Did Not Have the Income Category at Start and Gained the Income Category at Annual Assessment | Did Not Have the Income Category at Start or at Annual Assessment | Total Adults (including those with No Income) | Performance Measure: Adults who Gained or Increased Income from Start to Annual Assessment, Average Gain | Performance measure: Percent of persons who accomplishe d this measure |
| 1 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |
|  | Number of Adults with Earned Income (i.e., Employment Income) |  |  |  |  |  |  |  | # | =I2/H2 |
| 2 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |
|  | Average Change in Earned Income | $ | $ |  | $ | $ | --- | --- | $ |  |
| 3 |  |  |  | --- |  |  |  |  |  | --- |
|  |  |  |  |  |  |  |  |  |  |  |

A B C D E F G H I J
Did Not Have Performance
the Income Measure:
Income Change by Retained Retained Category at Adults who Performance
Income Category Had Income Income Income Retained Start and Did Not Have Gained or measure:
1 (Universe: Adult Category at Category But Category and Income Gained the the Income Increased Income Percent of
Stayers with Start and Did Had Less $ at Same $ at Category and Income Category at Total Adults from Start to persons who
Income Information Not Have It at Annual Annual Increased $ Category at Start or at (including Annual accomplishe
at Start and Annual Annual Assessment Assessment at Annual Annual Annual those with Assessment, d this
Assessment) Assessment Than at Start as at Start Assessment Assessment Assessment No Income) Average Gain measure
Number of
4 Adults with # =I4/H4
Other Income
Average Change --- ---
5 $ $ --- $ $ $ ---
in Other Income
Number of
Adults with Any
6 # =I6/H6
Income (i.e.,
Total Income)
Average Change
7 in Overall $ $ --- $ $ --- $ $ ---
Income

|  | A | B | C | D | E | F | G | H | I | J |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Income Change by Income Category (Universe: Adult Stayers with Income Information at Start and Annual Assessment) | Had Income Category at Start and Did Not Have It at Annual Assessment | Retained Income Category But Had Less $ at Annual Assessment Than at Start | Retained Income Category and Same $ at Annual Assessment as at Start | Retained Income Category and Increased $ at Annual Assessment | Did Not Have the Income Category at Start and Gained the Income Category at Annual Assessment | Did Not Have the Income Category at Start or at Annual Assessment | Total Adults (including those with No Income) | Performance Measure: Adults who Gained or Increased Income from Start to Annual Assessment, Average Gain | Performance measure: Percent of persons who accomplishe d this measure |
| 1 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |
|  | Number of Adults with Other Income |  |  |  |  |  |  |  | # | =I4/H4 |
| 4 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |
|  | Average Change in Other Income | $ | $ |  | $ | $ | --- | --- | $ |  |
| 5 |  |  |  | --- |  |  |  |  |  | --- |
|  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |
|  | Number of Adults with Any Income (i.e., Total Income) |  |  |  |  |  |  |  | # | =I6/H6 |
| 6 |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |
|  | Average Change in Overall Income | $ | $ |  | $ | $ |  | $ | $ |  |
| 7 |  |  |  | --- |  |  | --- |  |  | --- |
|  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.02 Income and Sources Earned Income and all other sources
Universe:

### Q19a1: All adult stayers where the head of household has been in the project 365 days or more, with

Income and Sources at start and at Annual Assessment

### Q19a2: All adult leavers with Income and Sources at start and exit


> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Project Leavers; Project Stayers

Programming Information:
Q19a1
1. Report using data from each adult project stayer’s last project stay during the [report date range].
2. The [total income] on a specific Income and Sources record is required to determine “other income”.
Refer to “Determining Total and Earned Income” in the HMIS Reporting Glossary to calculate [total
income] for this question and to Determining a Client’s Relevant Annual Assessment to locate required
annual assessment records. Clients with doesn’t know / refusing / missing [total income] at project
start OR annual assessment are completely excluded from this question.
3. “Earned income” reports on adults with earned income at start, annual assessment, or exit as
appropriate to the column, with an associated dollar amount > $0.00. If the response to [earned
income] is ‘Yes’ but no amount is recorded, do not report the person as having earned income.
4. “Other income” reports on adults with [other income] = [total income] minus [earned income]. If the
response to [earned income] is ‘Yes’ but no amount is recorded, or if the person has a total monthly
income without any specific sources and dollars for those sources specified, assume that [total
income] is entirely “other income”.
5. “Change in Income” is computed by subtracting the amount of monthly income reported on the
assessment at project start from the monthly income reported at annual assessment. For the columns
B and C this should result in negative responses. For columns E and F this should result in positive
responses.
6. Description of rows
   a. Number of Adults with Earned Income (row 2) counts adult stayers with earned income at
program start, annual assessment, or both, as appropriate to the column.
   b. Average Change in Earned Income (row 3) is calculated by dividing the sum of all changes in
Earned income for adult stayers in that column by the total number of adult stayers with earned

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |

income who are reported in that column. For example, if under “Retained Income Category and
Increased $ at Annual Assessment” there is one adult stayer who gained $200.00 in earned
income and one other adult stayer who gained $400.00 in earned income within the date range,
the two increases are added together ($600.00) and divided by the number of clients in that
category (2) for an average change of $300.00.
   c. Number of Adults with Other Income (row 4) counts adult stayers according to other income
recorded at program start, annual assessment, or both, as appropriate to the column.
   d. Average Change in Other Income (row 5) is calculated by dividing the sum of all changes in other
income for adult stayers in that column by the total number of adult stayers with other income
who are reported in that column. For example, if under “Retained Income Category and Increased $
at Annual Assessment” there is one adult stayer who gained $200.00 in other income and another
adult stayer who gained $400.00 in other income within the date range, the two increases are
added together ($600.00) and divided by the number of clients in that category (2), for an
average change of $300.00.
   e. Number of Adults with Any Income (row 6) counts adult stayers according to total monthly
income recorded at program start, annual assessment, or both, as appropriate to the column.
   f. Average Change in Overall Income (row 7) is calculated by dividing the sum of all total monthly
changes in any income for adult stayers in that column by the total number of adult stayers who
are reported in that column. Because the calculation for overall change of income can include
changes in earned income as well as other income, it is possible that a person counted in one
column for earned or other income may appear in a different column for any or overall income. For
example, suppose under “had income category at start and increased income at annual
assessment” there is one adult stayer who gained $200.00 in other income and another adult
stayer who gained $400.00 in other income within the date range. The average change in other
income for these two stayers would be $300.00. As long as this is the only income reported for
these two clients, they would also appear in the Number of Adults with Any Income and Average
Change in Overall Income for “had income category at start and increased income at annual
assessment.” However, if these two clients also had earned income upon program start, and both
clients lost $500.00 each in earned income at annual assessment, then both clients would end up
under the “Retained income category but had less income at annual assessment than at start” for
Number of Adults with Any Income and Average Change in Overall Income because their total
income losses exceed their other income increases.
7. Description of columns
   a. Had Income Category at Start and Did Not Have It at Annual Assessment (column B) counts
adult stayers who had > $0.00 in the Income and Sources category at project start and $0.00 in
the Income and Sources category at Annual assessment.
   b. Retained Income Category but Had Less $ at Annual Assessment than at Start (column C)
counts adult stayers who had > $0.00 in Income and Sources category at project start and at
Annual assessment had < the dollar amount at project start, but still > $0.00.
   c. Retained Income Category and Same $ at Annual Assessment as at Start (column D) counts
adult stayers for whom the dollar amount recorded in the Income and Sources category at project
start is > $0.00 and = the dollar amount recorded in the Income and Sources category at Annual
assessment.
   d. Retained Income Category and Increased $ at Annual Assessment (column E) counts adult
stayers who had > $0.00 in the Income and Sources category at project start and at Annual
assessment had > the dollar amount at project start.
   e. Did Not Have the Income Category at Start and Gained the Income Category at Annual
Assessment (column F) = counts adult stayers who had $0.00 in the Income and Sources
category at project start and had > $0.00 in the Income and Sources category at Annual
assessment.
   f. Did Not Have the Income Category at Start or at Annual Assessment (column G) counts adult
stayers for whom the dollar amount recorded in the Income and Sources category at project start
= $0.00 and the dollar amount recorded in the Income and Sources category at annual
assessment also = $0.00.
   g. Total Adults -including those with $0.00 income (column H) = the total number of adult stayers
with Income and Sources records both at project start and at annual assessment, i.e. the total
universe of clients for this question.
   h. Performance Measures: Adults who Gained or Increased Income from Start to Annual
Assessment, Average Gain (column I) = the number of adult stayers with an Income and Sources
record at Annual assessment > Income and Sources record at project start for the Income and
Sources category.
   i. Average Gain for each Income and Sources category. (Earned – A2, Other – A4, and Any – A6)
is calculated by dividing the sum of monthly changes in income for adult stayers who gained or
increased income from project start to Annual assessment by the total number of adults with such
a change in income.
   j. Performance measure: Percent of persons who accomplished this measure (column J) = Adults
who Gained or Increased Income (column I) / Total Adults (column h).
Q19a2
The programming for this question is identical to the programming for Q19a1, with the following changes:
1. This question reports on adult leavers with total monthly income >= $0.00 at project start and project exit. Adult leavers with Doesn’t
Know/Prefers Not to Answer or Missing income as calculated using “Determining Total and Earned Income” in the HMIS Reporting Glossary
at project start or project exit are not included in this question.
2. Each project leaver’s assessment at project exit is used in lieu of data from each client’s annual assessment. Again, project leavers
missing an exit assessment are not reported in this question.
3. Use the header row shown below (text changed from “Annual Assessment” to “Exit”).
A B C D E F G H I J
Income Had Retained Retained Retained Did Not Did Not Total Adults Performanc Performance
Change by Income Income Income Income Have the Have the (including e Measure: measure:
Income Category Category Category Category Income Income those with Adults who Percent of
Category at Start But Had Less and and Category at Category No Income) Gained or persons who
(Universe: and Did $ at Exit Same $ Increase Start and at Start or Increased accomplished
1
Adult Leavers Not Have It Than at Start at Exit as d $ at Gained the at Exit Income this measure
with Income at Exit at Start Exit Income from Start
Information Category at to Exit,
at Start and Exit Average
Exit) Gain

|  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | G |  |  | H |  |  | I |  |  | J |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Income Change by Income Category (Universe: Adult Leavers with Income Information at Start and Exit) |  |  | Had Income Category at Start and Did Not Have It at Exit |  |  | Retained Income Category But Had Less $ at Exit Than at Start |  |  | Retained Income Category and Same $ at Exit as at Start |  |  | Retained Income Category and Increase d $ at Exit |  |  | Did Not Have the Income Category at Start and Gained the Income Category at Exit |  |  | Did Not Have the Income Category at Start or at Exit |  |  | Total Adults (including those with No Income) |  |  | Performanc e Measure: Adults who Gained or Increased Income from Start to Exit, Average Gain |  |  | Performance measure: Percent of persons who accomplished this measure |  |  |


### Q19b: Disabling Conditions and Income for Adults at Exit


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F G H I J K L M
AO: AO: AO: AC: AC: UK: UK:
Adult Adult % with AC: Adult % with UK: Adult % with
1 with without AO: Disabling Adult with without AC: Disabling Adult with without UK: Disabling
Disabling Disabling Total Condition Disabling Disabling Total Condition Disabling Disabling Total Condition
Condition Condition Adults by Source Condition Condition Adults by Source Condition Condition Adults by Source
2 Earned Income
Unemployment
3
Insurance
Supplemental
4 Security
Income (SSI)
Social Security
Disability
5
Insurance
(SSDI)
VA Service-
Connected
6
Disability
Compensation

|  | A | B | C | D | E | F | G | H | I | J | K | L | M |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | AO: Adult with Disabling Condition | AO: Adult without Disabling Condition | AO: Total Adults | AO: % with Disabling Condition by Source | AC: Adult with Disabling Condition | AC: Adult without Disabling Condition | AC: Total Adults | AC: % with Disabling Condition by Source | UK: Adult with Disabling Condition | UK: Adult without Disabling Condition | UK: Total Adults | UK: % with Disabling Condition by Source |
| 1 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 2 | Earned Income |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Unemployment Insurance |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Supplemental Security Income (SSI) |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Social Security Disability Insurance (SSDI) |  |  |  |  |  |  |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | VA Service- Connected Disability Compensation |  |  |  |  |  |  |  |  |  |  |  |  |
| 6 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F G H I J K L M
AO: AO: AO: AC: AC: UK: UK:
Adult Adult % with AC: Adult % with UK: Adult % with
1 with without AO: Disabling Adult with without AC: Disabling Adult with without UK: Disabling
Disabling Disabling Total Condition Disabling Disabling Total Condition Disabling Disabling Total Condition
Condition Condition Adults by Source Condition Condition Adults by Source Condition Condition Adults by Source
VA Non-
Service-
7 Connected
Disability
Pension
Private
8 Disability
Insurance
Worker's
9
Compensation
Temporary
Assistance for
10
Needy Families
(TANF)
General
11
Assistance (GA)
Retirement
12 Income from
Social Security
Pension or
retirement
13
income from a
former job

|  | A | B | C | D | E | F | G | H | I | J | K | L | M |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | AO: Adult with Disabling Condition | AO: Adult without Disabling Condition | AO: Total Adults | AO: % with Disabling Condition by Source | AC: Adult with Disabling Condition | AC: Adult without Disabling Condition | AC: Total Adults | AC: % with Disabling Condition by Source | UK: Adult with Disabling Condition | UK: Adult without Disabling Condition | UK: Total Adults | UK: % with Disabling Condition by Source |
| 1 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | VA Non- Service- Connected Disability Pension |  |  |  |  |  |  |  |  |  |  |  |  |
| 7 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Private Disability Insurance |  |  |  |  |  |  |  |  |  |  |  |  |
| 8 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Worker's Compensation |  |  |  |  |  |  |  |  |  |  |  |  |
| 9 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Temporary Assistance for Needy Families (TANF) |  |  |  |  |  |  |  |  |  |  |  |  |
| 10 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | General Assistance (GA) |  |  |  |  |  |  |  |  |  |  |  |  |
| 11 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Retirement Income from Social Security |  |  |  |  |  |  |  |  |  |  |  |  |
| 12 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Pension or retirement income from a former job |  |  |  |  |  |  |  |  |  |  |  |  |
| 13 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F G H I J K L M
AO: AO: AO: AC: AC: UK: UK:
Adult Adult % with AC: Adult % with UK: Adult % with
1 with without AO: Disabling Adult with without AC: Disabling Adult with without UK: Disabling
Disabling Disabling Total Condition Disabling Disabling Total Condition Disabling Disabling Total Condition
Condition Condition Adults by Source Condition Condition Adults by Source Condition Condition Adults by Source
14 Child Support
Alimony and
15 other spousal
support
16 Other source
17 No Sources
Unduplicated
18
Total Adults --- --- ---

|  | A | B | C | D | E | F | G | H | I | J | K | L | M |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | AO: Adult with Disabling Condition | AO: Adult without Disabling Condition | AO: Total Adults | AO: % with Disabling Condition by Source | AC: Adult with Disabling Condition | AC: Adult without Disabling Condition | AC: Total Adults | AC: % with Disabling Condition by Source | UK: Adult with Disabling Condition | UK: Adult without Disabling Condition | UK: Total Adults | UK: % with Disabling Condition by Source |
| 1 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 14 | Child Support |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Alimony and other spousal support |  |  |  |  |  |  |  |  |  |  |  |  |
| 15 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 16 | Other source |  |  |  |  |  |  |  |  |  |  |  |  |
| 17 | No Sources |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Unduplicated Total Adults |  |  |  |  |  |  |  |  |  |  |  |  |
| 18 |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  | --- |  |  |  | --- |  |  |  | --- |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.08 Disabling Condition 0 or 1
4.02 Income and Sources Earned Income and all other sources
Universe: Adult leavers with known income and disabling condition information

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Project Leavers

Programming Instructions:
1. This question reports clients according [disabling condition] at project start, [income and sources] at
exit, and household type.
2. See Reporting counts of clients by element by household type for household type determination.
3. Report using data from each adult’s latest project stay in the [report date range].
4. Clients missing [income and sources] at exit, or where [income from any source] (element 4.02.2) is 8,
9, or 99, or where [disabling condition] (3.08) is 8, 9, or 99 should be completely excluded from this
question.
5. Report clients according to household type in the appropriate set of columns:
   a. Columns B through E = Adults Only (“AO”). Same as “Without Children” in other questions.
   b. Columns F through I = Adults and Children (“AC”). Same as “With Children and Adults” in other
questions.
   c. Columns J through M = Unknown household type (“UK”).
6. Report clients according to [disabling condition]:
   a. Columns B, F, and I = [disabling condition] = 1 (yes).
   b. Columns C, G, and J = [disabling condition] = 0 (no).
   c. Columns D, H and L = [disabling condition] = 0 or 1.
7. Rows 2 through 16 report clients according to income sources indicated as “yes” (1) on the client’s
[income and sources] at exit.
8. Row 17 reports clients who have no sources of income ( [income from any source] = 0 ).
9. Row 18 reports the total unduplicated clients from rows 2 through 17.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.08 |  |  | Disabling Condition |  |  | 0 or 1 |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |

10. Columns E, I and M show a percentage of clients who have a disabling condition and the specific
income source as a percentage of all clients with that income source. For example, cell E2 = B2 / D2.

### Q20: Non-Cash Benefits


### Q20a: Type of Non-Cash Benefit Sources


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D Z
Benefit at Data
Latest Annual Benefit at Standards
1
Benefit at Assessment for Exit for Response
Start Stayers Leavers options
Supplemental Nutrition Assistance 4.03.3 = 1
2 Program (SNAP) (Previously known as
Food Stamps)
Special Supplemental Nutrition Program 4.03.4 = 1
3
for Women, Infants, and Children (WIC)
4 TANF Child Care Services 4.03.5 = 1
5 TANF Transportation Services 4.03.6 = 1
6 Other TANF-Funded Services 4.03.7 = 1
7 Other Source 4.03.8 = 1
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.03 Non-Cash Benefits Non-Cash Benefits and all other sources
Universe: Active adults in the report date range, further described below.

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Project Leavers; Project Stayers

Programming Instructions:
1. Report using data from each adult project stayer’s last project stay during the [report date range].
2. Column B (Benefit at Start)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Benefit at Start |  |  | Benefit at Latest Annual Assessment for Stayers |  |  | Benefit at Exit for Leavers |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 2 |  |  | Supplemental Nutrition Assistance Program (SNAP) (Previously known as Food Stamps) |  |  |  |  |  |  |  |  |  |  |  | 4.03.3 = 1 | 4.03.3 = 1 |  |
| 3 |  |  | Special Supplemental Nutrition Program for Women, Infants, and Children (WIC) |  |  |  |  |  |  |  |  |  |  |  | 4.03.4 = 1 |  |  |
|  | 4 |  | TANF Child Care Services |  |  |  |  |  |  |  |  |  |  |  |  | 4.03.5 = 1 |  |
|  | 5 |  | TANF Transportation Services |  |  |  |  |  |  |  |  |  |  |  |  | 4.03.6 = 1 |  |
|  | 6 |  | Other TANF-Funded Services |  |  |  |  |  |  |  |  |  |  |  |  | 4.03.7 = 1 |  |
|  | 7 |  | Other Source |  |  |  |  |  |  |  |  |  |  |  |  | 4.03.8 = 1 |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.03 |  |  | Non-Cash Benefits |  |  | Non-Cash Benefits and all other sources |  |  |

   a. For all active adults determine the most recent Income and Sources record with a [data collection
stage] of project start (1) attached to the selected project stay where the [information date] of the
record = [project start date].
   b. Report the client according to specific non-cash benefit listed on each row. Clients may be
reported on multiple rows in column B, but no more than one time in a single cell of column B.
3. Column C (Benefit at Latest Annual Assessment for Stayers)
   c. Refer to Determining a Client’s Relevant Annual Assessment to know if a stayer is required to have
an annual assessment, and if so whether or not the relevant record is available.
   d. If the head of household has the required annual assessment record, allow other household
members who are also stayers to be included in the universe according to their most recent data
even if it is not annual assessment data and regardless of their length of stay.
   e. If the head of household is missing their relevant annual assessment but another household
member has the annual assessment, report that household members in this question.
4. Column D (Benefit at Exit)
   f. For leavers, report only heads of households who left plus other adult household members who left
at the same time as the head of household. Do not include household members who left prior to
the head of household even though that person is otherwise considered a “leaver” in other report
questions.
   g. For each client determine the most recent Income and Sources record with a [data collection
stage] of project exit (3) attached to the selected project stay where the [information date] of the
record = [project exit date].

### Q20b: Number of Non-Cash Benefit Sources


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D
Benefit at Latest
1 Annual Assessment for Benefit at Exit
Benefit at Start Stayers for Leavers
2 No Sources
3 1 + Source(s)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Benefit at Start |  |  | Benefit at Latest Annual Assessment for Stayers |  |  | Benefit at Exit for Leavers |  |  |
|  | 2 |  | No Sources |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 1 + Source(s) |  |  |  |  |  |  |  |  |  |  |  |

A B C D
Benefit at Latest
1 Annual Assessment for Benefit at Exit
Benefit at Start Stayers for Leavers
Client Doesn’t Know/Prefers Not to
4
Answer
Data Not Collected/Not stayed long
5
enough for Annual Assessment
6 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.03 Non-Cash Benefits Non-Cash Benefits and all other sources
Universe: Active adults in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Project Leavers; Project Stayers

Programming Instructions:
1. Use the same logic for client and record selection as Q20a, but instead of reporting according to
individual sources this question reports on the total number of sources for each client.
2. On row 2, report clients where all specific non-cash benefits indicate “no” or are null/blank AND where
[Non-Cash Benefits from Any Source] = “no” (0).
3. On row 3, report each client that has one or more specific sources of non-cash benefits. If a specific
Income and Sources record indicates [Non-Cash Benefits from Any Source] = “yes” (1), report the
client on row 3 even if no other specific benefits are indicated.
4. For any remaining records not reported in rows 2 or 3, report the client in row 4 or 5 according to the
response in [Non-Cash Benefits from Any Source].
5. Stayers that have not been in the project long enough to receive an Annual Assessment should be
reported in row 5.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Benefit at Start |  |  | Benefit at Latest Annual Assessment for Stayers |  |  | Benefit at Exit for Leavers |  |  |
| 4 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |
| 5 |  |  | Data Not Collected/Not stayed long enough for Annual Assessment |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.03 |  |  | Non-Cash Benefits |  |  | Non-Cash Benefits and all other sources |  |  |


### Q21: Health Insurance


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D Z
At Annual Assessment At Exit for Data Standards
1
At Start for Stayers Leavers Response options
2 MEDICAID 4.04.3 = 1
3 MEDICARE 4.04.4 = 1
4 State Children’s Health Insurance Program 4.04.5 = 1
5 Veteran's Health Administration (VHA) 4.04.6 = 1
6 Employer-Provided Health Insurance 4.04.7 = 1
7 Health Insurance obtained through COBRA 4.04.8 = 1
8 Private Pay Health Insurance 4.04.9 = 1
9 State Health Insurance for Adults 4.04.10 = 1
10 Indian Health Services Program 4.04.11 = 1
11 Other 4.04.12 = 1
12 No Health Insurance see below
13 Client Doesn’t Know/Prefers Not to Answer see below
14 Data not Collected see below
Number of Stayers not yet Required to Have an --- ---
15
Annual Assessment
16 1 Source of Health Insurance see below
17 More than 1 Source of Health Insurance see below
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.04 Health Insurance Health Insurance from all sources

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | At Start |  |  | At Annual Assessment for Stayers |  |  | At Exit for Leavers |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response options |  |
|  | 2 |  | MEDICAID |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.3 = 1 |  |
|  | 3 |  | MEDICARE |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.4 = 1 |  |
|  | 4 |  | State Children’s Health Insurance Program |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.5 = 1 |  |
|  | 5 |  | Veteran's Health Administration (VHA) |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.6 = 1 |  |
|  | 6 |  | Employer-Provided Health Insurance |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.7 = 1 |  |
|  | 7 |  | Health Insurance obtained through COBRA |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.8 = 1 |  |
|  | 8 |  | Private Pay Health Insurance |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.9 = 1 |  |
|  | 9 |  | State Health Insurance for Adults |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.10 = 1 |  |
|  | 10 |  | Indian Health Services Program |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.11 = 1 |  |
|  | 11 |  | Other |  |  |  |  |  |  |  |  |  |  |  |  | 4.04.12 = 1 |  |
|  | 12 |  | No Health Insurance |  |  |  |  |  |  |  |  |  |  |  |  | see below |  |
|  | 13 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  | see below |  |
|  | 14 |  | Data not Collected |  |  |  |  |  |  |  |  |  |  |  |  | see below |  |
| 15 |  |  | Number of Stayers not yet Required to Have an Annual Assessment |  |  | --- |  |  |  |  |  | --- |  |  |  |  |  |
|  | 16 |  | 1 Source of Health Insurance |  |  |  |  |  |  |  |  |  |  |  |  | see below |  |
|  | 17 |  | More than 1 Source of Health Insurance |  |  |  |  |  |  |  |  |  |  |  |  | see below |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.04 |  |  | Health Insurance |  |  | Health Insurance from all sources |  |  |

Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Project Leavers; Project Stayers

Programming Instructions:
1. Report using data from each client’s latest project stay in the [report date range].
2. Rows 2 through 11 report clients according to specific health insurance sources based on the client’s
record at start (column B), annual assessment (column C) or at exit (column D).
3. Row 12 reports clients where all specific sources of health insurance indicate “no” or are null/blank
AND where [Covered by Health Insurance] is “no” (0) or “yes” (1).
4. Row 13 reports clients where all specific sources of health insurance indicate “no” or are null/blank
AND where [Covered by Health Insurance] is “Client Doesn’t Know” (8) or “Client Prefers Not to
Answer” (9).
5. Row 14 reports clients where the relevant Health Insurance record is completely missing, or where
specific sources of health insurance indicate “no” or are null/blank AND where [Covered by Health
Insurance] is missing or “Data not collected” (99).
6. Row 15 reports only on stayers – see 9c below.
7. Rows 16 and 17 report clients with exactly one or more than one specific source of health insurance
indicating “yes” (1). Do not include the response [Covered by Health Insurance] in the total number –
this count is based exclusively around the specific sources.
8. Column B (at Start)
   a. For each active client, determine the Health Insurance record with a [data collection stage] of
project start (1) attached to the selected project stay where the [information date] of the record =
[project start date].
   b. Report the client on row 2 through 17 as described above.
9. Column C (at Latest Annual Assessment for Stayers)
   a. Refer to Determining a Client’s Relevant Annual Assessment to know if a stayer is required to have
an annual assessment, and if so whether or not the relevant record is available.
   b. If the client has the required annual assessment, report the client on row 2 through 17 as described
above.
   c. If the stayer is not yet required to have an annual assessment, report the client in cell C15.
   d. If the stayer is required to have an annual assessment but the necessary record is completely
missing, report the client in cell C14.
10. Column D (at Exit)
   a. For each leaver, determine the Health Insurance record with a [data collection stage] of project exit
(3) attached to the selected project stay where the [information date] of the record = [project exit
date].
   b. Report the client on row 2 through 17 as described above.

### Q22: Length of participation


### Q22a1: Length of Participation – CoC Projects


### Q22a2: Length of Participation – ESG Projects


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D
1 Total Leavers Stayers
2 30 days or less
3 31 to 60 days
4 61 to 90 days
5 91 to 180 days
6 181 to 365 days
7 366 to 730 days (1-2 Yrs)
8 731 to 1,095 days (2-3 Yrs)
9 1,096 to 1,460 days (3-4 Yrs)
10 1,461 to 1,825 days (4-5 Yrs)
11 More than 1,825 days (> 5 Yrs)
12 Total

*Report Relevance: ESG CAPER*

*Changes from FY 2024: None*


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  | Total |  |  | Leavers |  |  | Stayers |  |  |
|  | 2 |  | 30 days or less |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 731 to 1,095 days (2-3 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 1,096 to 1,460 days (3-4 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 1,461 to 1,825 days (4-5 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | More than 1,825 days (> 5 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Total |  |  |  |  |  |  |  |  |  |  |  |

A B C D
1 Total Leavers Stayers
2 0 to 7 days
3 8 to 14 days
4 15 to 21 days
5 22 to 30 days
6 31 to 60 days
7 61 to 90 days
8 91 to 180 days
9 181 to 365 days
10 366 to 730 days (1-2 Yrs)
11 731 to 1,095 days (2-3 Yrs)
12 1,096 to 1,460 days (3-4 Yrs)
13 1,461 to 1,825 days (4-5 Yrs)
14 More than 1,825 days (> 5 Yrs)
15 Total
Other Relevant Data Standards
Field No Relevant Data
Required
2.02.6 Project Type All projects
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Project Leavers; Project Stayers; Bed Night; and

Length of Stay
Programming Instructions:
1. Report the distinct counts of clients by length of stay intervals using data from each client’s latest
project stay according to whether the client was a leaver or stayer.
2. Refer to the HMIS Reporting Glossary for determining a client’s length of stay. Exclude criteria of
[report start date]; for reporting purposes, length of stay should include all time relevant to the client’s
latest project stay even if it is before the start of the report.

### Q22b: Average and Median Length of Participation in Days


*Report Relevance: CoC APR*


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  | Total |  |  | Leavers |  |  | Stayers |  |  |
|  | 2 |  | 0 to 7 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 8 to 14 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 15 to 21 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 22 to 30 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | 731 to 1,095 days (2-3 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | 1,096 to 1,460 days (3-4 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | 1,461 to 1,825 days (4-5 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 14 |  | More than 1,825 days (> 5 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Total |  |  |  |  |  |  |  |  |  |  |  |


| Field No |  | Other Relevant Data Standards |  | Relevant Data |
| --- | --- | --- | --- | --- |
|  |  | Required |  |  |
| 2.02.6 | Project Type |  |  | All projects |

*Changes from FY 2024: None*

A B C
1 Leavers Stayers
2 Average Length
3 Median Length
Other Relevant Data Standards
Field No Relevant Data
Required
2.02.6 Project Type All projects
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Project Leavers; Project Stayers; Bed Night; and

Length of Stay
Programming Instructions:
1. Using each client’s length of stay as determined in Q22a, calculate the average and median across
each client universe (leavers and stayers).
   a. Clients who erroneously have [project start date] > [project exit date] for this particular
project stay are excluded from these calculations. These clients are included in row 3 of
Q6b and should have their project stay dates corrected.

### Q22c: Length of Time between Project Start Date and Housing Move-in Date


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
With Unknown
1 Without Children With Only Household
Total Children and Adults Children Type
2 7 days or less
3 8 to 14 days
4 15 to 21 days
5 22 to 30 days
6 31 to 60 days
7 61 to 90 days
8 91 to 180 days

|  |  |  |  | A |  |  |  |  | B |  |  |  |  | C |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  |  |  | Leavers |  |  |  |  | Stayers |  |  |
|  | 2 |  | Average Length |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Median Length |  |  |  |  |  |  |  |  |  |  |  |  |
| Field No |  |  |  |  |  | Other Relevant Data Standards |  |  |  |  | Relevant Data |  |  |  |  |
|  |  |  |  |  |  | Required |  |  |  |  |  |  |  |  |  |
| 2.02.6 |  |  |  |  | Project Type |  |  |  |  |  | All projects |  |  |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 7 days or less |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 8 to 14 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 15 to 21 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 22 to 30 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F
With Unknown
1 Without Children With Only Household
Total Children and Adults Children Type
9 181 to 365 days
10 366 to 730 days (1-2 Yrs)
Total (persons moved into
11
housing)
12 Average length of time to housing
Persons who were exited without
13
move-in
14 Total persons
Other Relevant Data Standards
Field No Relevant Data
Required
3 (PSH); 13 (RRH); and when reporting on project
2.02.6 Project Type type 7 (Other) with 2.06 Funding Source of HUD:
Pay for Success (35)
3.20 Housing Move-in Date mm/dd/yyyy
Universe: All active clients where the head of household had a move-in date in the report date range plus
leavers who exited in the date range and never had a move-in date.

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated

Household Counts and Unduplicated Client Counts by Household Type; Handling Housing Move-In Dates
Programming Instructions:
1. On rows 2 through 10, report the distinct counts of clients by the length of time between the person’s
[project start date] and [housing move-in date]. See Reporting counts of clients by element by
household type for column instructions. Use [housing move in dates] that are valid for each person as
defined in the Handling Housing Move-In Dates section of the HMIS Reporting Glossary.
2. On row 11, report the distinct counts of clients who have moved into housing.
3. On row 12, of clients who have moved into housing, report the average length of time between [project
start date] and [housing move-in date].
4. On row 13, report the distinct counts of clients who exited without moving into housing.
5. On row 14, report the total number of clients.

|  |  |  |  | A |  |  | B | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  | Without Children |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 9 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 11 |  |  | Total (persons moved into housing) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Average length of time to housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 13 |  |  | Persons who were exited without move-in |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 14 |  | Total persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| Field No |  | Other Relevant Data Standards Required | Relevant Data |
| --- | --- | --- | --- |
| 2.02.6 | Project Type |  | 3 (PSH); 13 (RRH); and when reporting on project type 7 (Other) with 2.06 Funding Source of HUD: Pay for Success (35) |
| 3.20 | Housing Move-in Date |  | mm/dd/yyyy |


### Q22d: Length of Participation by Household Type


*Report Relevance: ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
With Unknown
1 Without Children With Only Household
Total Children and Adults Children Type
2 7 days or less
3 8 to 14 days
4 15 to 21 days
5 22 to 30 days
6 31 to 60 days
7 61 to 90 days
8 91 to 180 days
9 181 to 365 days
366 to 730 days (1-2
10
Yrs)
11 731 days or more
12 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Bed Nights and Length of Stay; Project Leavers;

Project Stayers; Household Types; Unduplicated Household Counts; and Unduplicated Client Counts by
Household Type
Programming Instructions: Using length of stay as calculated for Q22a, report each client in the relevant
range according to household type. See Reporting counts of clients by element by household type for
column instructions.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 7 days or less |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 8 to 14 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 15 to 21 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 22 to 30 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 10 |  |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | 731 days or more |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |


### Q22e: Length of Time Prior to Housing - based on 3.917 Date Homelessness Started


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: Corrected typo in programming instruction 2c, which now refers to the correct*

row number for “Data not collected.”
A B C D E F
With
Children With
1
Without and Only Unknown
Total Children Adults Children Household Type
2 7 days or less
3 8 to 14 days
4 15 to 21 days
5 22 to 30 days
6 31 to 60 days
7 61 to 90 days
8 91 to 180 days
9 181 to 365 days
10 366 to 730 days (1-2 Yrs)
11 731 days or more
Total (persons moved into
12
housing)
13 Not yet moved into housing
14 Data not collected
15 Total persons
Field No Other Relevant Data Standards Required Relevant Data
0 (ES-EE); 1 (EE-NbN); 2 (TH); 3 (PSH); 8
(SH); 9 (PH); 13 (RRH); and when reporting on
2.02.6 Project Type
project type 7 (Other) with 2.06 Funding
Source of HUD: Pay for Success (35)
3.917.3 Approximate date this episode started
3.20 Housing Move-in Date mm/dd/yyyy
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated

Household Counts; and Unduplicated Client Counts by Household Type; Handling Housing Move-In Dates

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 7 days or less |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 8 to 14 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 15 to 21 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 22 to 30 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | 731 days or more |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 12 |  |  | Total (persons moved into housing) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | Not yet moved into housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 14 |  | Data not collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Total persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 0 (ES-EE); 1 (EE-NbN); 2 (TH); 3 (PSH); 8 (SH); 9 (PH); 13 (RRH); and when reporting on project type 7 (Other) with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |
| 3.917.3 |  |  | Approximate date this episode started |  |  |  |  |  |
| 3.20 |  |  | Housing Move-in Date |  |  | mm/dd/yyyy |  |  |

Programming Instructions:
1. This question reports on the time the client reported experiencing homelessness up until housing in
the project. For permanent housing and Pay for Success projects, this means the person’s move into a
PH bed or unit according to the [housing move-in date]. Use [housing move-in dates] that are valid for
each person as defined in the Handling Housing Move-In Dates section of the HMIS Reporting
Glossary. For all other project types, it means moving into a bed or unit at the project as indicated
simply by the [project start date].
2. On rows 2 through 11, report the distinct counts of clients by the length of time between the person’s
[Approximate date this episode started] to the point the person was housed as defined below. See
Reporting counts of clients by element by household type for column instructions.
   a. The data from the head of household’s response to 3.917 should be propagated to the children.
   b. This applies to any household member whose age is <= 17 (calculated according to the HMIS
Reporting Glossary), regardless of their relationship to the head of household, but not clients of
unknown age.
   c. Only propagate the head of household’s data to children with the same [project start date] as the
head of household. Children who enter after the HoH would be counted on row 14 (data not
collected).
3. For permanent housing projects (types 3, 9 and 13) and project type 7 with 2.06 Funding Source of
HUD: Pay for Success (35):
   a. Use the person’s [housing move-in date]. Household members already in the household when the
head of household moves into housing have the same [housing move-in date] as the head of
household. For household members joining the household after it is already in housing, use the
person’s [project start date] as their [housing move-in date].
   b. Include clients who moved into housing prior to the [report start date] who were still active in the
project.
   c. If a client is active in the PH/PSH/RRH project but either has not moved into housing or did so after
the [report end date], report that person on line 13.
4. For all other project types on this question, use each person’s [project start date] as the date they
moved into housing.
5. Report the total of all clients in housing on line 12.
6. If a client is missing their [Approximate date this episode started], or if that date occurs after the
person has moved into housing, report that person on line 14. This includes people who would not be
expected to have an [approximate date this episode started] based on the project type they are
entering and their [prior living situation] responses.
7. Report the totals of all active clients on line 15. Line 15 should be the sum of lines 12, 13, and 14.

### Q22f: Length of Time between Project Start Date and Housing Move-in Date by Race and Ethnicity


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F G H I J K
American Multi-racial Unknown
Indian, Black, Middle Native At Least 1 Race (does not (Doesn’t Know,
1 Alaska Asian or African Eastern or Hawaiian and include Prefers not to
Native, or Asian American, Hispanic/ North or Pacific Hispanic/Latin Hispanic/ Answer, Data
Indigenous American or African Latina/o African Islander White a/o Latina/o) not Collected)
2 Persons Moved Into
Housing
3 Persons Exited Without
Move-In
4 Average time to Move-In
5 Median time to
Move-In

|  | A | B | C | D | E | F | G | H | I | J | K |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | American Indian, Alaska Native, or Indigenous | Asian or Asian American | Black, African American, or African | Hispanic/ Latina/o | Middle Eastern or North African | Native Hawaiian or Pacific Islander | White | At Least 1 Race and Hispanic/Latin a/o | Multi-racial (does not include Hispanic/ Latina/o) | Unknown (Doesn’t Know, Prefers not to Answer, Data not Collected) |
| 1 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
| 2 | Persons Moved Into Housing |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
| 3 | Persons Exited Without Move-In |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
| 4 | Average time to Move-In |  |  |  |  |  |  |  |  |  |  |
| 5 | Median time to Move-In |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
13 (RRH), 3 (PSH); and when reporting on
2.02.6 Project Type project type 7 (Other) with 2.06 Funding
Source of HUD: Pay for Success (35)
3.20 Housing Move-in Date mm/dd/yyyy
Universe: All active clients where the head of household had a move-in date in the report date range plus
leavers who exited in the date range and never had a move-in date.

> HMIS Reporting Glossary Reference: Active Clients; Race and Ethnicity; Handling Housing Move-In Dates

Programming Instructions:
1. Clients who identify with one and only one race/ethnicity will be counted in that specific column.
Clients who identify with more than one race where none of the options selected is
“Hispanic/Latina/o” will be counted in the “Multiracial (Does not include Hispanic/Latina/o)” column.
Clients who identify with more than one race/ethnicity where one of the options selected is
“Hispanic/Latina/o” will be counted in the “Multiracial (Includes Hispanic/Latina/o)” column.
2. The response options “Client doesn’t know”, “Client prefers not to answer”, and “Data not collected”
are not valid in conjunction with any other element; if any of these elements are present in addition to
a race/ethnicity response, disregard the 8/9/99 response and report the client according to the
known race/ethnicity information for that client. Clients with a response option of only “Client doesn’t
know”, “Client prefers not to answer”, or “Data not collected” will be counted in the “Unknown” column.
3. Use [housing move-in dates] that are valid for each person as defined in the Handling Housing Move-
In Dates section of the HMIS Reporting Glossary.
4. In row 2, report the distinct counts of clients who have moved into housing.
5. In row 3, report the distinct counts of clients who exited without moving into housing.
6. In row 4, report the average length of time between [project start date] and [housing move-in date] for
clients who have moved into housing.
7. In row 5, report the median length of time between [project start date] and [housing move-in date] for
clients who have moved into housing.

| Field No | Other Relevant Data Standards Required | Relevant Data |
| --- | --- | --- |
| 2.02.6 | Project Type | 13 (RRH), 3 (PSH); and when reporting on project type 7 (Other) with 2.06 Funding Source of HUD: Pay for Success (35) |
| 3.20 | Housing Move-in Date | mm/dd/yyyy |


### Q22g: Length of Time Prior to Housing by Race and Ethnicity - based on 3.917 Date Homelessness Started


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F G H I J K
Unknown
American Multi-racial (Doesn’t
Indian, Black, Middle Native At Least 1 (does not Know, Prefers
1
Alaska Asian or African Eastern or Hawaiian or Race and include not to Answer,
Native, or Asian American, Hispanic/ North Pacific Hispanic/ Hispanic/ Data not
Indigenous American or African Latina/o African Islander White Latina/o Latina/o) Collected)
Persons Moved
2
Into Housing
Persons Not
3 Yet Moved Into
Housing
Average time
4
to Move-In
Median time to
5
Move-In
Field No Other Relevant Data Standards Required Relevant Data
0 (ES-EE); 1 (EE-NbN); 2 (TH); 3 (PSH); 8 (SH); 9 (PH); 13 (RRH); and
2.02.6 Project Type when reporting on project type 7 (Other) with 2.06 Funding Source of
HUD: Pay for Success (35)
3.917.3 Approximate date this episode started
3.20 Housing Move-in Date mm/dd/yyyy
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Race and Ethnicity; Handling Housing Move-In Dates


|  | A | B | C | D | E | F | G | H | I | J | K |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | American Indian, Alaska Native, or Indigenous | Asian or Asian American | Black, African American, or African | Hispanic/ Latina/o | Middle Eastern or North African | Native Hawaiian or Pacific Islander | White | At Least 1 Race and Hispanic/ Latina/o | Multi-racial (does not include Hispanic/ Latina/o) | Unknown (Doesn’t Know, Prefers not to Answer, Data not Collected) |
| 1 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  | Persons Moved Into Housing |  |  |  |  |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  | Persons Not Yet Moved Into Housing |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  | Average time to Move-In |  |  |  |  |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |
|  | Median time to Move-In |  |  |  |  |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 0 (ES-EE); 1 (EE-NbN); 2 (TH); 3 (PSH); 8 (SH); 9 (PH); 13 (RRH); and when reporting on project type 7 (Other) with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |
| 3.917.3 |  |  | Approximate date this episode started |  |  |  |  |  |
| 3.20 |  |  | Housing Move-in Date |  |  | mm/dd/yyyy |  |  |

Programming Instructions:
1. This question reports on the time the client reported being homeless up until housing in the project.
For permanent housing and Pay for Success projects, this means the person’s move into a PH bed or
unit according to the [housing move-in date]. Use [housing move-in dates] that are valid for each
person as defined in the Handling Housing Move-In Dates section of the HMIS Reporting Glossary. For
all other project types, it means moving into a bed or unit at the project as indicated simply by the
[project start date].
2. Use the following instructions to apply the head of household’s responses to 3.917 to other household
members as appropriate:
   a. The data from the head of household’s response to 3.917 should be propagated to the children.
   b. This applies to any household member whose age is <= 17 (calculated according to the HMIS
Reporting Glossary), regardless of their relationship to the head of household, but not clients of
unknown age.
   c. Only propagate the head of household’s data to children with the same [project start date] as the
head of household. Children who enter after the HoH are excluded from this question entirely.
3. For permanent housing projects (types 3, 9 and 13) and project type 7 with 2.06 Funding Source of
HUD: Pay for Success (35):
   a. Use the person’s [housing move-in date]. Household members already in the household when the
head of household moves into housing have the same [housing move-in date] as the head of
household. For household members joining the household after it is already in housing, use the
person’s [project start date] as their [housing move-in date].
   b. Include clients who moved into housing prior to the [report start date] who were still active in the
project.
4. For all other project types on this question, use each person’s [project start date] as the date they
moved into housing.
5. If a client is missing their [Approximate date this episode started], or if that date occurs after the
person has moved into housing, exclude them from this question entirely.
6. Clients who identify with one and only one race/ethnicity will be counted in that specific column.
Clients who identify with more than one race where none of the options selected is
“Hispanic/Latina/o” will be counted in the “Multiracial (Does not include Hispanic/Latina/o)” column.
Clients who identify with more than one race/ethnicity where one of the options selected is
“Hispanic/Latina/o” will be counted in the “Multiracial (Includes Hispanic/Latina/o)” column.
7. The response options “Client doesn’t know”, “Client prefers not to answer”, and “Data not collected” are not valid in conjunction with any
other element; if any of these elements are present in addition to a race/ethnicity response, disregard the 8/9/99 response and report
the client according to the known race/ethnicity information for that client. Clients with a response option of only “Client doesn’t know”,
“Client prefers not to answer”, or “Data not collected” will be counted in the “Unknown” column.
8. In row 2, report the total of all clients in housing
9. In row 3, report clients who were active in a PH/PSH/RRH project but either have not moved into housing or did so after the [report end
date]. This row will only contain zeros when run for any other project type.
10. Rows 4 and 5 report on the length of time people report experiencing homelessness prior to becoming housed. This is defined as the
length of time between the person’s [Approximate date this episode started] to the point the person was housed as defined above.
   a. In row 4, report the average length of time people report experiencing homelessness prior to becoming housed.
   b. In row 5, report the median length of time people report experiencing homelessness prior to becoming housed.

### Q23: Exit Destination Information


### Q23c: Exit Destination


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
2 Homeless Situations
Place not meant for habitation (e.g., a
3 116
vehicle, an abandoned building,

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  |  | Homeless Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  | Place not meant for habitation (e.g., a vehicle, an abandoned building, |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 116 |  |  |

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
bus/train/subway station/airport or
anywhere outside)
Emergency shelter, including hotel or
4 motel paid for with emergency shelter 101
voucher, Host Home shelter
5 Safe Haven 118
6 Subtotal
7 Institutional Situations
Foster care home or foster care group
8 215
home
Hospital or other residential non-
9 206
psychiatric medical facility
Jail, prison, or juvenile detention
10 207
facility
Long-term care facility or nursing
11 225
home
Psychiatric hospital or other
12 204
psychiatric facility
Substance abuse treatment facility or
13 205
detox center
14 Subtotal
15 Temporary Situations
Transitional housing for homeless
16 302
persons (including homeless youth)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  |  |  | bus/train/subway station/airport or anywhere outside) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 |  |  | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 101 |  |  |
|  | 5 |  | Safe Haven |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 118 |  |
|  | 6 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  |  | Institutional Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 8 |  |  | Foster care home or foster care group home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 215 |  |  |
| 9 |  |  | Hospital or other residential non- psychiatric medical facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 206 |  |  |
| 10 |  |  | Jail, prison, or juvenile detention facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 207 |  |  |
| 11 |  |  | Long-term care facility or nursing home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 225 |  |  |
| 12 |  |  | Psychiatric hospital or other psychiatric facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 204 |  |  |
| 13 |  |  | Substance abuse treatment facility or detox center |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 205 |  |  |
|  | 14 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  |  | Temporary Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 16 |  |  | Transitional housing for homeless persons (including homeless youth) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 302 |  |  |

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Residential project or halfway house
17 329
with no homeless criteria
Hotel or motel paid for without
18 314
emergency shelter voucher
19 Host Home (non-crisis) 332
Staying or living with family, temporary
20 tenure (e.g., room, apartment, or 312
house)
Staying or living with friends,
21 temporary tenure (e.g., room, 313
apartment, or house)
Moved from one HOPWA funded
22 327
project to HOPWA TH
23 Subtotal
24 Permanent Situations
Staying or living with family,
25 422
permanent tenure
Staying or living with friends,
26 423
permanent tenure
Moved from one HOPWA funded
27 426
project to HOPWA PH
Rental by client, no ongoing housing
28 410
subsidy

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 17 |  |  | Residential project or halfway house with no homeless criteria |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 329 |  |  |
| 18 |  |  | Hotel or motel paid for without emergency shelter voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 314 |  |  |
|  | 19 |  | Host Home (non-crisis) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 332 |  |
| 20 |  |  | Staying or living with family, temporary tenure (e.g., room, apartment, or house) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 312 |  |  |
| 21 |  |  | Staying or living with friends, temporary tenure (e.g., room, apartment, or house) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 313 |  |  |
| 22 |  |  | Moved from one HOPWA funded project to HOPWA TH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 327 |  |  |
|  | 23 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 24 |  |  | Permanent Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 25 |  |  | Staying or living with family, permanent tenure |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 422 |  |  |
| 26 |  |  | Staying or living with friends, permanent tenure |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 423 |  |  |
| 27 |  |  | Moved from one HOPWA funded project to HOPWA PH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 426 |  |  |
| 28 |  |  | Rental by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 410 |  |  |

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Rental by client, with ongoing housing
29 435
subsidy
Owned by client, with ongoing housing
30 421
subsidy
Owned by client, no ongoing housing
31 411
subsidy
32 Subtotal
33 Other Situations
34 No Exit Interview completed 30
35 Other 17
36 Deceased 24
Client Doesn’t Know/Prefers Not to
37 8 or 9
Answer
38 Data Not Collected 99
39 Subtotal
40 TOTAL
Total persons exiting to positive
41
housing destinations
Total persons exiting to destinations
42 that excluded them from the
calculation
Percentage of persons exiting to = B41 /(B40 = C41 /(C40 = D41 /(D40 – = E41 / (E40 = F41 /
43
positive housing destinations –B42) –C42) D42) –E42) (F40 – F42)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 29 |  |  | Rental by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 435 |  |  |
| 30 |  |  | Owned by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 421 |  |  |
| 31 |  |  | Owned by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 411 |  |  |
|  | 32 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 33 |  |  | Other Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 34 |  | No Exit Interview completed |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 30 |  |
|  | 35 |  | Other |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 17 |  |
|  | 36 |  | Deceased |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 24 |  |
| 37 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | 38 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 39 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 40 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 41 |  |  | Total persons exiting to positive housing destinations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 42 |  |  | Total persons exiting to destinations that excluded them from the calculation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 43 |  |  | Percentage of persons exiting to positive housing destinations |  |  | = B41 /(B40 –B42) |  |  | = C41 /(C40 –C42) |  |  | = D41 /(D40 – D42) |  |  | = E41 / (E40 –E42) |  |  | = F41 / (F40 – F42) |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All
3.12 Destination All
Universe: Leavers in the report date range

> HMIS Reporting Glossary Reference: Leavers; Date of Birth/Age; Household Types; Unduplicated Household Counts; and Unduplicated Client

Counts by Household Type
Programming Instructions:
1. Report the distinct counts of clients by each different housing destination. See Reporting counts of clients by element by household type
for column instructions.
2. Use [destination] recorded separately in each client’s record. Data recorded under the 2014 Data Standards may not have this field
present for child household members. In this case, use the [destination] of the head of household for these child household members.
3. Row 40 is the unduplicated count of [project leavers] in the [report date range] based on Unduplicated Household Counts and
Unduplicated Client Counts by Household Type as determined by the HMIS Reporting Glossary.
4. Row 41 is the [number of clients exiting to positive destinations]. Reference the destinations of project exits against Appendix A (row
headers) and the column corresponding to the project type of the data. Positive destinations are indicated with a ✔.
5. Row 42 is the [total clients excluded], whose destinations cause them to be removed from the percentage calculation. Refer to Appendix
A for these destinations, indicated with an ✗, corresponding to the project type of the data.
6. Row 43 is the [number of clients exiting to positive destinations] divided by ([total clients exiting] – [total clients excluded]).

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All |  |  |
| 3.12 |  |  | Destination |  |  | All |  |  |


### Q23d: Exit Destination – Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F Z
Data Standards
1 Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
2 GPD TIP housing subsidy 428
3 VASH housing subsidy 419
4 RRH or equivalent subsidy 431
HCV voucher (tenant or project based)
5 433
(not dedicated)
6 Public housing unit 434
Rental by client, with other ongoing
7 420
housing subsidy
8 Housing Stability Voucher 436
Family Unification Program Voucher
9 437
(FUP)
Foster Youth to Independence Initiative
10 438
(FYI)
11 Permanent Supportive Housing 439
Other permanent housing dedicated for
12 440
formerly homeless persons
13 TOTAL
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects except Homelessness Prevention

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | GPD TIP housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 428 |  |
|  | 3 |  | VASH housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 419 |  |
|  | 4 |  | RRH or equivalent subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 431 |  |
| 5 |  |  | HCV voucher (tenant or project based) (not dedicated) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 433 |  |  |
|  | 6 |  | Public housing unit |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 434 |  |
| 7 |  |  | Rental by client, with other ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 420 |  |  |
|  | 8 |  | Housing Stability Voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 436 |  |
| 9 |  |  | Family Unification Program Voucher (FUP) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 437 |  |  |
| 10 |  |  | Foster Youth to Independence Initiative (FYI) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 438 |  |  |
|  | 11 |  | Permanent Supportive Housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 439 |  |
| 12 |  |  | Other permanent housing dedicated for formerly homeless persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 440 |  |  |
|  | 13 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects except Homelessness Prevention |  |  |

Field No Other Relevant Data Standards Required Relevant Data
3.12.1 Destination 435
3.12.A Rental Subsidy Type All
Universe: Leavers in the report date range with an exit destination of 435 (“Rental by client, with housing subsidy”).

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Unduplicated Household Counts; and Unduplicated

Client Counts by Household Type.
Programming Instructions:
1. Report the distinct counts of included clients by their subsidy type at project exit.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 3.12.1 |  |  | Destination |  |  | 435 |  |  |
| 3.12.A |  |  | Rental Subsidy Type |  |  | All |  |  |


### Q23e: Exit Destination Type by Race and Ethnicity


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F G H I J K L
American Multi-racial Unknown
Black, Middle Native At Least 1
Indian, Asian or Hispanic (does not (Doesn’t Know,
African Eastern Hawaiian Race and
1 Total Alaska Asian / White include Prefers not to
American, or North or Pacific Hispanic/L
Native, or American Latina/o Hispanic/ Answer, Data
or African African Islander atina/o
Indigenous Latina/o) not Collected)
Homeless
2
Situations
Institutional
3
Situations
Temporary
4
Situations
Permanent
5
Situations
6 Other Situations
7 Total

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | G |  |  | H |  |  | I |  |  | J |  |  | K |  |  | L |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | American Indian, Alaska Native, or Indigenous |  |  | Asian or Asian American |  |  | Black, African American, or African |  |  | Hispanic / Latina/o |  |  | Middle Eastern or North African |  |  | Native Hawaiian or Pacific Islander |  |  | White |  |  | At Least 1 Race and Hispanic/L atina/o |  |  | Multi-racial (does not include Hispanic/ Latina/o) |  |  | Unknown (Doesn’t Know, Prefers not to Answer, Data not Collected) |  |  |
| 2 |  |  | Homeless Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  | Institutional Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 |  |  | Temporary Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 5 |  |  | Permanent Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Other Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Relevant Data
Required
2.02.6 Project Type All
3.12 Destination All
Universe: Leavers in the report date range

> HMIS Reporting Glossary Reference: Leavers; Race and Ethnicity

Programming Instructions:
1. Clients who identify with one and only one race/ethnicity will be counted in that specific column.
Clients who identify with more than one race where none of the options selected is
“Hispanic/Latina/o” will be counted in the “Multiracial (Does not include Hispanic/Latina/o)” column.
Clients who identify with more than one race/ethnicity where one of the options selected is
“Hispanic/Latina/o” will be counted in the “Multiracial (Includes Hispanic/Latina/o)” column.
   a. The response options “Client doesn’t know”, “Client prefers not to answer”, and “Data not
collected” are not valid in conjunction with any other element; if any of these elements are present
in addition to a race/ethnicity response, disregard the 8/9/99 response and report the client
according to the known race/ethnicity information for that client. Clients with a response option of
only “Client doesn’t know”, “Client prefers not to answer”, or “Data not collected” will be counted in
the “Unknown” column.
2. Clients appear in rows as follows:
   a. Row 2 uses the logic from Q23c, row 6
   b. Row 3 uses the logic from Q23c, row 14
   c. Row 4 uses the logic from Q23c, row 23
   d. Row 5 uses the logic from Q23c, row 32
   e. Row 6 uses the logic from Q23c, row 39
   f. Row 7 shows the total unduplicated count of all clients selecting this response option for race and
ethnicity

| Field No |  | Other Relevant Data Standards |  | Relevant Data |
| --- | --- | --- | --- | --- |
|  |  | Required |  |  |
| 2.02.6 | Project Type |  |  | All |
| 3.12 | Destination |  |  | All |


### Q24: Targeted Questions


### Q24a: Homelessness Prevention Housing Assessment at Exit


*Report Relevance: ESG CAPER (HP only)*

*Changes from FY 2024: None*

A B C D E F Y Z
Data Standards
With Response to Data Standards
1 Children With Unknown [housing Response to
Without and Only Household assessment at [housing assessment
Total Children Adults Children Type exit] at exit - subsidy]
Able to maintain the housing they had at project start-
2 1 1
-Without a subsidy
Able to maintain the housing they had at project start-
3 1 2
-With the subsidy they had at project start
Able to maintain the housing they had at project start-
4 -With an on-going subsidy acquired since project 1 3
start
Able to maintain the housing they had at project start-
5 1 4
-Only with financial assistance other than a subsidy
6 Moved to new housing unit--With on-going subsidy 2 1
Moved to new housing unit--Without an on-going
7 2 2
subsidy
8 Moved in with family/friends on a temporary basis 3 n/a
9 Moved in with family/friends on a permanent basis 4 n/a
Moved to a transitional or temporary housing facility
10 5 n/a
or program
Client became homeless – moving to a shelter or
11 6 n/a
other place unfit for human habitation

|  | A | B | C | D | E | F | Y | Z |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Total | Without Children | With Children and Adults | With Only Children | Unknown Household Type | Data Standards |  |
|  |  |  |  |  |  |  | Response to | Data Standards |
| 1 |  |  |  |  |  |  | [housing | Response to |
|  |  |  |  |  |  |  | assessment at | [housing assessment |
|  |  |  |  |  |  |  | exit] | at exit - subsidy] |
|  | Able to maintain the housing they had at project start- -Without a subsidy |  |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  | 1 | 1 |
|  |  |  |  |  |  |  |  |  |
|  | Able to maintain the housing they had at project start- -With the subsidy they had at project start |  |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  | 1 | 2 |
|  |  |  |  |  |  |  |  |  |
|  | Able to maintain the housing they had at project start- -With an on-going subsidy acquired since project start |  |  |  |  |  |  |  |
| 4 |  |  |  |  |  |  | 1 | 3 |
|  |  |  |  |  |  |  |  |  |
|  | Able to maintain the housing they had at project start- -Only with financial assistance other than a subsidy |  |  |  |  |  |  |  |
| 5 |  |  |  |  |  |  | 1 | 4 |
|  |  |  |  |  |  |  |  |  |
| 6 | Moved to new housing unit--With on-going subsidy |  |  |  |  |  | 2 | 1 |
|  | Moved to new housing unit--Without an on-going subsidy |  |  |  |  |  |  |  |
| 7 |  |  |  |  |  |  | 2 | 2 |
|  |  |  |  |  |  |  |  |  |
| 8 | Moved in with family/friends on a temporary basis |  |  |  |  |  | 3 | n/a |
| 9 | Moved in with family/friends on a permanent basis |  |  |  |  |  | 4 | n/a |
|  | Moved to a transitional or temporary housing facility or program |  |  |  |  |  |  |  |
| 10 |  |  |  |  |  |  | 5 | n/a |
|  |  |  |  |  |  |  |  |  |
|  | Client became homeless – moving to a shelter or other place unfit for human habitation |  |  |  |  |  |  |  |
| 11 |  |  |  |  |  |  | 6 | n/a |
|  |  |  |  |  |  |  |  |  |

A B C D E F Y Z
Data Standards
With Response to Data Standards
1 Children With Unknown [housing Response to
Without and Only Household assessment at [housing assessment
Total Children Adults Children Type exit] at exit - subsidy]
12 Jail/prison 7 n/a
13 Deceased 10 n/a
14 Client Doesn’t Know/Prefers Not to Answer 8 or 9 n/a
15 Data not collected (no exit interview completed) 99 n/a
16 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type 12
1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 99
W5 Housing Assessment at Exit (If W5.1 = 1, then) 1, 2, 3, 4
(If W5.1 = 2, then) 1, 2
Universe: Leavers in the report date range

> HMIS Reporting Glossary Reference: Leavers; Date of Birth/Age; Household Types; Unduplicated Household Counts; and Unduplicated Client

Counts by Household Type.
Programming Instructions:
1. Using data from each client’s latest project stay, report the distinct counts of clients by housing assessment recorded at exit ([data
collection stage] = 3 and [information date] = [project exit date]). See Reporting counts of clients by element by household type for
column instructions.

|  | A | B | C | D | E | F | Y | Z |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Total | Without Children | With Children and Adults | With Only Children | Unknown Household Type | Data Standards |  |
|  |  |  |  |  |  |  | Response to | Data Standards |
| 1 |  |  |  |  |  |  | [housing | Response to |
|  |  |  |  |  |  |  | assessment at | [housing assessment |
|  |  |  |  |  |  |  | exit] | at exit - subsidy] |
| 12 | Jail/prison |  |  |  |  |  | 7 | n/a |
| 13 | Deceased |  |  |  |  |  | 10 | n/a |
| 14 | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  | 8 or 9 | n/a |
| 15 | Data not collected (no exit interview completed) |  |  |  |  |  | 99 | n/a |
| 16 | Total |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 12 |  |  |
| W5 |  |  | Housing Assessment at Exit |  |  | 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 99 (If W5.1 = 1, then) 1, 2, 3, 4 (If W5.1 = 2, then) 1, 2 |  |  |

2. Reference column Y against [housing assessment at exit] (element W5) and column Z against [housing assessment at exit – subsidy
information] (elements W5.1.A or W5.1.B, depending on the response to element W5.1) to count the client in the correct row.

### Q24b: Moving On Assistance Provided to Households in PSH


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F Z
Unknown Data Standards
1 Without With Children With Only Household Response
Total Children and Adults Children Type options
Subsidized housing application
2 1
assistance
Financial assistance for Moving On
3 (e.g., security deposit, moving 2
expenses)
Non-financial assistance for Moving
4 On (e.g., housing navigation, 3
transition support)
5 Housing referral/placement 4
6 Other (please specify) 5
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type 3
C3 Moving On Assistance Provided 1, 2, 3, 4, 5

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 2 |  |  | Subsidized housing application assistance |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |  |
| 3 |  |  | Financial assistance for Moving On (e.g., security deposit, moving expenses) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 2 |  |  |
| 4 |  |  | Non-financial assistance for Moving On (e.g., housing navigation, transition support) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 3 |  |  |
|  | 5 |  | Housing referral/placement |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 4 |  |
|  | 6 |  | Other (please specify) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 5 |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 3 |  |  |
| C3 |  |  | Moving On Assistance Provided |  |  | 1, 2, 3, 4, 5 |  |  |

Universe: Heads of household active in PSH during the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; and Unduplicated Client Counts by Household

Type.
Programming Instructions:
1. Using data from each client’s latest project stay, report the distinct counts of heads of household receiving each type of [moving on
assistance] within the report period. See Reporting counts of clients by element by household type for column instructions.
2. Each cell must contain a distinct count of heads of household in that household type who received that type of [moving on
assistance]. Heads of household will be reported in multiple rows if they received more than one type of [moving on assistance] within
the report period.

### Q24e: Sex


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: New question*

A B C D E F Z
With Data
Children Unknown Standards
1
Without and With Only Household Response
Total Children Adults Children Type Options
2 Female 0
3 Male 1
Client Doesn’t
4 Know/Prefers Not to 8 or 9
Answer
5 Data not collected 99
6 Total
Other Relevant Data Standards
Field No Relevant Data
Required
2.02.6 Project Type All projects
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types;

Unduplicated Household Counts; and Unduplicated Client Counts by Household Type.
Programming Instructions: Report the distinct counts of clients by sex and household type. See
Reporting counts of clients by element by household type for column instructions.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Options |  |
|  | 2 |  | Female |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 0 |  |
|  | 3 |  | Male |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
| 4 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | 5 |  | Data not collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| Field No |  | Other Relevant Data Standards |  | Relevant Data |
| --- | --- | --- | --- | --- |
|  |  | Required |  |  |
| 2.02.6 | Project Type |  |  | All projects |


### Q25: Veterans Questions

To be completed if there are any Veterans served during the operating year
The Veterans questions are a subset of questions required to be completed for all CoC-APR’s where at
least one veteran is served.
The Veteran questions are designed, to reuse programming from a previous APR question with the
application of a filter for Veterans.
For all veteran questions (Q25 series) a Veteran:
1. Must be age 18 or older at time of [project start] or [report start date] – whichever is greater.
2. Must indicate ‘yes’ for [veteran status].
It is critical to include the client’s age in this determination to avoid reporting children as veterans, either
because of data entry error or because the client’s [veteran status] changed at some point during the
client’s HMIS history.
Report Add veteran filter
Veteran Status Questions Relevance Changes from APR FY 2024 to this question


ESG CAPER


Households


Veterans


Persons Exiting to Rental by
Client With An Ongoing
Subsidy – Veterans

| Veteran Status Questions |  | Report |  | Changes from APR FY 2024 |  | Add veteran filter |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Relevance |  |  |  | to this question |  |
| Q25a: Number of Veterans | CoC APR and ESG CAPER |  |  | None | n/a |  |  |
| Q25b: Number of Veteran Households | CoC APR |  |  | None | n/a |  |  |
| Q25d: Age - Veterans | CoC APR |  |  | None | Q11 |  |  |
| Q25i: Exit Destination - Veterans | CoC APR |  |  | None | Q23c |  |  |
| Q25j: Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy – Veterans | CoC APR |  |  | None | Q23d |  |  |


### Q25a: Number of Veterans


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E Z
Data
Unknown Standards
1
Without With Children Household Response
Total Children and Adults Type options
2 Chronically Homeless Veteran 1
Non-Chronically Homeless 1
3
Veteran
4 Not a Veteran 0
Client Doesn’t Know/Prefers 8 or 9
5
Not to Answer
6 Data Not Collected 99
7 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.07 Veteran Status 0, 1, 8, 9, 99
3.08 Disabling Condition (used in calculation of chronic homelessness)
3.917 Living Situation (used in calculation of chronic homelessness)
4.5 Physical Disability (used in calculation of chronic homelessness)
4.6 Developmental Disability (used in calculation of chronic homelessness)
4.7 Chronic Health Condition (used in calculation of chronic homelessness)
4.8 HIV/AIDS (used in calculation of chronic homelessness)
4.9 Mental Health Disorder (used in calculation of chronic homelessness)
4.10 Substance Use Disorder (used in calculation of chronic homelessness)
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Chronically

Homeless at Project Start

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | Chronically Homeless Veteran |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
| 3 |  |  | Non-Chronically Homeless Veteran |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 | 1 |  |
|  | 4 |  | Not a Veteran |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 0 |  |
| 5 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 | 8 or 9 |  |
|  | 6 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 7 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.07 |  |  | Veteran Status |  |  | 0, 1, 8, 9, 99 |  |  |
| 3.08 |  |  | Disabling Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 3.917 |  |  | Living Situation |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.5 |  |  | Physical Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.6 |  |  | Developmental Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.7 |  |  | Chronic Health Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.8 |  |  | HIV/AIDS |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.9 |  |  | Mental Health Disorder |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.10 |  |  | Substance Use Disorder |  |  | (used in calculation of chronic homelessness) |  |  |

Programming Instructions:
Count the total number of adults based on the response to [veteran status] as indicated in column Z
along with the client’s chronic homelessness status. See Reporting counts of clients by element by
household type for column instructions. See the HMIS Reporting Glossary for instructions on determining
chronic homelessness status. For the purposes of determining CH in this question, a client with a CH
status of “Client Doesn’t Know/Prefers Not to Answer/Unknown” with no other household members or in a
household with no other CH members can be simply considered NOT chronically homeless. In other
words, rows 5 and 6 apply solely to the person’s [veteran status].

### Q25b: Number of Veteran Households


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E Z
Data
With Unknown Standards
1
Without Children and Household Response
Total Children Adults Type options
2 Chronically Homeless Veteran 1
Non-Chronically Homeless
3 1
Veteran
4 Not a Veteran 0
Client Doesn’t Know/Prefers
5 8 or 9
Not to Answer
6 Data Not Collected 99
7 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.07 Veteran Status 0, 1, 8, 9, 99
3.08 Disabling Condition (used in calculation of chronic homelessness)
3.917 Living Situation (used in calculation of chronic homelessness)
4.05 Physical Disability (used in calculation of chronic homelessness)
4.06 Developmental Disability (used in calculation of chronic homelessness)
4.07 Chronic Health Condition (used in calculation of chronic homelessness)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | Chronically Homeless Veteran |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
| 3 |  |  | Non-Chronically Homeless Veteran |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 1 |  |  |
|  | 4 |  | Not a Veteran |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 0 |  |
| 5 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | 6 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 7 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.07 |  |  | Veteran Status |  |  | 0, 1, 8, 9, 99 |  |  |
| 3.08 |  |  | Disabling Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 3.917 |  |  | Living Situation |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.05 |  |  | Physical Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.06 |  |  | Developmental Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.07 |  |  | Chronic Health Condition |  |  | (used in calculation of chronic homelessness) |  |  |

Field No Other Relevant Data Standards Required Relevant Data
4.08 HIV/AIDS (used in calculation of chronic homelessness)
4.09 Mental Health Disorder (used in calculation of chronic homelessness)
4.10 Substance Use Disorder (used in calculation of chronic homelessness)
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Household Types; Chronically

Homeless at Project Start
Programming Instructions:
Count the total number of households based on whether any of the adults are veterans and/or chronically
homeless. Determine the row to report the household in as follows. Stop processing when a match is
found, i.e. do not report the household in more than one row in rows 2 through 6:
1. Use data attached to each head of household’s latest project stay in the report date range. Include all
other adults present with the head of household on that project stay who are also active in the date
range, along with their data from that stay. This is necessary in order to determine the veteran and
chronic homelessness status of the entire household, even though one or more of the adult household
members may have another later project stay in the report date range with a different head of
household or as the head of household. Please note: this is a departure from most other questions
on this report which exclusively use data associated with each person’s latest project stay.
2. For the purposes of determining chronic homelessness in this question, any household with a CH
status of Doesn’t Know/Prefers Not to Answer/Unknown can be simply considered NOT chronically
homeless.
3. Chronically Homeless Veteran (row 2): Any household with at least one veteran who is chronically
homeless.
4. Non-Chronically Homeless Veteran (row 3): Any household not reported above with at least one non-
chronically homeless veteran.
5. Not a Veteran (row 4): Any household not reported above where all the adults have a veteran status of
“no” (0).
6. Client Doesn’t Know/Client Prefers Not to Answer (row 5): Any household not reported above where at
least one of the adults has a veteran status of “Client doesn’t know” (8) or “Client prefers not to
answer” (9).
7. Data Not Collected (row 6): Any household not reported above where at least one of the adults is
missing his/her veteran status or it is “Data not collected” (99).

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 4.08 |  |  | HIV/AIDS |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.09 |  |  | Mental Health Disorder |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.10 |  |  | Substance Use Disorder |  |  | (used in calculation of chronic homelessness) |  |  |

8. Report each household by type as described in Determining Each Client’s Household Type and
Counting Distinct Households.
Note that the household type “With Only Children” is not applicable for this question (by definition,
child-only households should not have veterans).

### Q25d: Age – Veterans


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E
Without With Children Unknown
1
Total Children and Adults Household Type
2 18-24
3 25-34
4 35-44
5 45-54
6 55-64
7 65 +
8 Client Doesn’t Know/Prefers Not to Answer --- --- --- ---
9 Data Not Collected --- --- --- ---
10 Total
Add veteran filter to Q11 for programming. Exclude first three rows from Q11, which apply only to children,
as well as the “With only children” column.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | Unknown Household Type |  |  |
|  | 2 |  | 18-24 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 25-34 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 35-44 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 45-54 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 55-64 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 65 + |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  | --- |  |  | --- |  |  | --- |  |  | --- |  |
|  | 9 |  | Data Not Collected |  |  |  | --- |  |  | --- |  |  | --- |  |  | --- |  |
|  | 10 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


### Q25i: Exit Destination – Veterans


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F Z
Data
With With Unknown Standards
1
Without Children Only Household Response
Total Children and Adults Children Type options
2 Homeless Situations
Place not meant for habitation (e.g., a vehicle, an
3 abandoned building, bus/train/subway station/airport 116
or anywhere outside)
Emergency shelter, including hotel or motel paid for
4 101
with emergency shelter voucher, Host Home shelter
5 Safe Haven 118
6 Subtotal
7 Institutional Situations
8 Foster care home or foster care group home 215
Hospital or other residential non-psychiatric medical
9 206
facility
10 Jail, prison, or juvenile detention facility 207
11 Long-term care facility or nursing home 225
12 Psychiatric hospital or other psychiatric facility 204
13 Substance abuse treatment facility or detox center 205
14 Subtotal
15 Temporary Situations

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  |  | Homeless Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  | Place not meant for habitation (e.g., a vehicle, an abandoned building, bus/train/subway station/airport or anywhere outside) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 116 |  |  |
| 4 |  |  | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 101 |  |  |
|  | 5 |  | Safe Haven |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 118 |  |
|  | 6 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  |  | Institutional Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Foster care home or foster care group home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 215 |  |
| 9 |  |  | Hospital or other residential non-psychiatric medical facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 206 |  |  |
|  | 10 |  | Jail, prison, or juvenile detention facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 207 |  |
|  | 11 |  | Long-term care facility or nursing home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 225 |  |
|  | 12 |  | Psychiatric hospital or other psychiatric facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 204 |  |
|  | 13 |  | Substance abuse treatment facility or detox center |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 205 |  |
|  | 14 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  |  | Temporary Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F Z
Data
With With Unknown Standards
1
Without Children Only Household Response
Total Children and Adults Children Type options
Transitional housing for homeless persons (including
16 302
homeless youth)
Residential project or halfway house with no homeless
17 329
criteria
Hotel or motel paid for without emergency shelter
18 314
voucher
19 Host Home (non-crisis) 332
Staying or living with family, temporary tenure (e.g.,
20 312
room, apartment, or house)
Staying or living with friends, temporary tenure (e.g.,
21 313
room, apartment, or house)
Moved from one HOPWA funded project to HOPWA
22 327
TH
23 Subtotal
24 Permanent Situations
25 Staying or living with family, permanent tenure 422
26 Staying or living with friends, permanent tenure 423
Moved from one HOPWA funded project to HOPWA
27 426
PH
28 Rental by client, no ongoing housing subsidy 410
29 Rental by client, with ongoing housing subsidy 435
30 Owned by client, with ongoing housing subsidy 421
31 Owned by client, no ongoing housing subsidy 411
32 Subtotal

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 16 |  |  | Transitional housing for homeless persons (including homeless youth) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 302 |  |  |
| 17 |  |  | Residential project or halfway house with no homeless criteria |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 329 |  |  |
| 18 |  |  | Hotel or motel paid for without emergency shelter voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 314 |  |  |
|  | 19 |  | Host Home (non-crisis) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 332 |  |
| 20 |  |  | Staying or living with family, temporary tenure (e.g., room, apartment, or house) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 312 |  |  |
| 21 |  |  | Staying or living with friends, temporary tenure (e.g., room, apartment, or house) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 313 |  |  |
| 22 |  |  | Moved from one HOPWA funded project to HOPWA TH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 327 |  |  |
|  | 23 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 24 |  |  | Permanent Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 25 |  | Staying or living with family, permanent tenure |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 422 |  |
|  | 26 |  | Staying or living with friends, permanent tenure |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 423 |  |
| 27 |  |  | Moved from one HOPWA funded project to HOPWA PH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 426 |  |  |
|  | 28 |  | Rental by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 410 |  |
|  | 29 |  | Rental by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 435 |  |
|  | 30 |  | Owned by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 421 |  |
|  | 31 |  | Owned by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 411 |  |
|  | 32 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F Z
Data
With With Unknown Standards
1
Without Children Only Household Response
Total Children and Adults Children Type options
33 Other Situations
34 No Exit Interview completed 30
35 Other 17
36 Deceased 24
37 Client Doesn’t Know/Prefers Not to Answer 8 or 9
38 Data Not Collected 99
39 Subtotal
40 TOTAL
41 Total persons exiting to positive housing destinations
Total persons exiting to destinations that excluded
42
them from the calculation
Percentage of persons exiting to positive housing = B41 / = C42 / = D42 / = E42 / = F42 /
43 destinations (B40 – (C40 – (D40 – D42) (E40 – (F40 – F42)
B42) C42) E42)
Add veteran filter to Q23c for programming.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 33 |  |  | Other Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 34 |  | No Exit Interview completed |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 30 |  |
|  | 35 |  | Other |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 17 |  |
|  | 36 |  | Deceased |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 24 |  |
|  | 37 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |
|  | 38 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 39 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 40 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 41 |  | Total persons exiting to positive housing destinations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 42 |  |  | Total persons exiting to destinations that excluded them from the calculation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 43 |  |  | Percentage of persons exiting to positive housing destinations |  |  | = B41 / (B40 – B42) |  |  | = C42 / (C40 – C42) |  |  | = D42 / (D40 – D42) |  |  | = E42 / (E40 – E42) |  |  | = F42 / (F40 – F42) |  |  |  |  |  |


### Q25j: Exit Destination – Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy - Veteran


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E Z
Data
Standards
1
Without With Children Unknown Response
Total Children and Adults Household Type options
2 GPD TIP housing subsidy 428
3 VASH housing subsidy 419
4 RRH or equivalent subsidy 431
HCV voucher (tenant or project based)
5 433
(not dedicated)
6 Public housing unit 434
Rental by client, with other ongoing
7 420
housing subsidy
8 Housing Stability Voucher 436
Family Unification Program Voucher
9 437
(FUP)
Foster Youth to Independence Initiative
10 438
(FYI)
11 Permanent Supportive Housing 439
Other permanent housing dedicated for
12 440
formerly homeless persons
13 TOTAL
Add veteran filter to Q23d for programming and exclude “With only children” column.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | GPD TIP housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 428 |  |
|  | 3 |  | VASH housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 419 |  |
|  | 4 |  | RRH or equivalent subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 431 |  |
| 5 |  |  | HCV voucher (tenant or project based) (not dedicated) |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 433 |  |  |
|  | 6 |  | Public housing unit |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 434 |  |
| 7 |  |  | Rental by client, with other ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 420 |  |  |
|  | 8 |  | Housing Stability Voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 436 |  |
| 9 |  |  | Family Unification Program Voucher (FUP) |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 437 |  |  |
| 10 |  |  | Foster Youth to Independence Initiative (FYI) |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 438 |  |  |
|  | 11 |  | Permanent Supportive Housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 439 |  |
| 12 |  |  | Other permanent housing dedicated for formerly homeless persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 440 |  |  |
|  | 13 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


### Q26: Chronically Homeless Questions

To be completed if there are any persons identified as chronically homeless and served during the operating year.
The CH questions are designed, where possible, to reuse programming from a previous APR question with the application of a “CH filter” for
chronically homeless clients at project start as described in the HMIS Reporting Glossary. Unlike other APR questions, this may require the
examination of client data for clients not active in the report date range.
**Note: For HMIS data entry and programming purposes, the head of household is not required to be the person who is CH. However, for HUD
record keeping and documentation purposes the CH person is expected to be the head of household.
CH Status Questions Report Relevance Changes from APR FY 2024 Add CH filter to this
question


one or more Chronically Homeless person


Persons by Household


Persons


Conditions - Chronically Homeless Persons

### Q26a: Chronic Homeless Status - Number of Households w/at least one or more CH person


*Report Relevance: CoC APR*

*Changes from FY 2024: None*


| CH Status Questions | Report Relevance | Changes from APR FY 2024 |  | Add CH filter to this |  |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  | question |  |
| Q26a: Number of Households w/at least one or more Chronically Homeless person | CoC APR | None | n/a |  |  |
| Q26b: Number of Chronically Homeless Persons by Household | CoC APR and ESG CAPER | None | n/a |  |  |
| Q26d: Age of Chronically Homeless Persons | CoC APR | None | Q11 |  |  |
| Q26e: Physical and Mental Health Conditions - Chronically Homeless Persons | CoC APR | None | Q13a1, Q13b1, Q13c1 |  |  |

A B C D E F
Without With Children and With Only Unknown Household
1
Total Children Adults Children Type
2 Chronically Homeless
3 Not Chronically Homeless
4 Client Doesn’t Know/Prefers Not to Answer
5 Data Not Collected
6 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.08 Disabling Condition (used in calculation of chronic homelessness)
3.917 Living Situation (used in calculation of chronic homelessness)
4.05 Physical Disability (used in calculation of chronic homelessness)
4.06 Developmental Disability (used in calculation of chronic homelessness)
4.07 Chronic Health Condition (used in calculation of chronic homelessness)
4.08 HIV/AIDS (used in calculation of chronic homelessness)
4.09 Mental Health Disorder (used in calculation of chronic homelessness)
4.10 Substance Use Disorder (used in calculation of chronic homelessness)
Universe: Active clients in the report date range

> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Chronically Homeless at Project Start, Unduplicated Household

Counts and Unduplicated Client Counts by Household Type

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | Chronically Homeless |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Not Chronically Homeless |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.08 |  |  | Disabling Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 3.917 |  |  | Living Situation |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.05 |  |  | Physical Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.06 |  |  | Developmental Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.07 |  |  | Chronic Health Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.08 |  |  | HIV/AIDS |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.09 |  |  | Mental Health Disorder |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.10 |  |  | Substance Use Disorder |  |  | (used in calculation of chronic homelessness) |  |  |

Programming Instructions:
Count the total number of households based on whether any of the adults or heads of household (including unaccompanied children) are
chronically homeless at project start. Determine the row to report the household in as follows. Stop processing when a match is found, i.e. do
not report the household in more than one row in rows 2 through 5:
1. Use data attached to each head of household’s latest project stay in the report date range. Determine the chronic homelessness status
at project start as described in the HMIS Reporting Glossary.
2. Chronically Homeless (row 2): Any household with at least one chronically homeless adult or head of household.
3. Non-Chronically Homeless (row 3): Any household not reported above where the head of household and all other adults are not
chronically homeless.
4. Client Doesn’t Know/Prefers Not to Answer (row 4): Any household not reported above where the head of household or at least one other
adult has a CH status of DK/PNTA (Doesn’t Know/Prefers Not to Answer).
5. Data Not Collected (row 5): Any household not reported above where the head of household or at least one other adult has a CH status of
missing.
6. Report each household by type as described in Determining Each Client’s Household Type and Counting Distinct Households.
7. Each head of household, and thus each household, should be reported only once in rows 2 through 5, and again in row 6. Similarly, each
household should be reported only once in columns C through F, and again in column B.

### Q26b: Number of Chronically Homeless Persons by Household


*Report Relevance: CoC APR and ESG CAPER*

*Changes from FY 2024: None*

A B C D E F
Without With Children and With Only Unknown
1
Total Children Adults Children Household Type
2 Chronically Homeless
3 Not Chronically Homeless
Client Doesn’t Know/Prefers Not to
4
Answer
5 Data Not Collected
6 Total
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.08 Disabling Condition (used in calculation of chronic homelessness)
3.917 Living Situation (used in calculation of chronic homelessness)
4.05 Physical Disability (used in calculation of chronic homelessness)
4.06 Developmental Disability (used in calculation of chronic homelessness)
4.07 Chronic Health Condition (used in calculation of chronic homelessness)
4.08 HIV/AIDS (used in calculation of chronic homelessness)
4.09 Mental Health Disorder (used in calculation of chronic homelessness)
4.10 Substance Use Disorder (used in calculation of chronic homelessness)
Universe: Active clients in the report date range

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | Chronically Homeless |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Not Chronically Homeless |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.08 |  |  | Disabling Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 3.917 |  |  | Living Situation |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.05 |  |  | Physical Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.06 |  |  | Developmental Disability |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.07 |  |  | Chronic Health Condition |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.08 |  |  | HIV/AIDS |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.09 |  |  | Mental Health Disorder |  |  | (used in calculation of chronic homelessness) |  |  |
| 4.10 |  |  | Substance Use Disorder |  |  | (used in calculation of chronic homelessness) |  |  |


> HMIS Reporting Glossary Reference: Active Clients; Date of Birth/Age; Chronically Homeless at Project Start; Household Types;

Unduplicated Household Counts and Unduplicated Client Counts by Household Type
Programming Instructions:
1. Report using data from each person’s latest project stay in the [report date range].
2. Report each person on lines 2 through 5 according to their chronic homelessness status at project start as described in the HMIS
Reporting Glossary.
3. See Reporting counts of clients by element by household type for column instructions.
4. Report each person again in row 6 and column B.

### Q26d: Age of Chronically Homeless Persons


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F
Without With Children and With Only Unknown
1
Total Children Adults Children Household Type
2 0-17 ---
3 18-24 ---
4 25-34 ---
5 35-44 ---
6 45-54 ---
7 55-64 ---
8 65 + ---

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 0-17 |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 18-24 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 4 |  | 25-34 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 5 |  | 35-44 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 6 |  | 45-54 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 7 |  | 55-64 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 8 |  | 65 + |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |

A B C D E F
Without With Children and With Only Unknown
1
Total Children Adults Children Household Type
Client Doesn’t Know/Prefers Not to ---
9
Answer
10 Data Not Collected ---
11 Total
Add CH status filter to Q11 for programming with different age groupings.

### Q26e: Physical and Mental Health Conditions - Chronically Homeless Persons


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D Z
Conditions at Latest Conditions at Exit Data Standards
1
Conditions At Start Assessment for Stayers for Leavers Response options
2 Mental Health Disorder 1
3 Alcohol Use Disorder 1
4 Drug Use Disorder 2
5 Both Drug and Alcohol Use Disorders 3
6 Chronic Health Condition 1
7 HIV/AIDS 1
8 Developmental Disability 1
9 Physical Disability 1
Column B = Add CH status filter to Q13a1 and report clients in total, without regard to household type.

|  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
| 9 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |  |
|  | 10 | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
|  | 11 | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  |  | A |  |  | B |  |  | C |  |  | D |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  | Conditions At Start |  |  | Conditions at Latest Assessment for Stayers |  |  | Conditions at Exit for Leavers |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response options |  |
|  | 2 | Mental Health Disorder |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 3 | Alcohol Use Disorder |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 4 | Drug Use Disorder |  |  |  |  |  |  |  |  |  |  |  | 2 |  |
|  | 5 | Both Drug and Alcohol Use Disorders |  |  |  |  |  |  |  |  |  |  |  | 3 |  |
|  | 6 | Chronic Health Condition |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 7 | HIV/AIDS |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 8 | Developmental Disability |  |  |  |  |  |  |  |  |  |  |  | 1 |  |
|  | 9 | Physical Disability |  |  |  |  |  |  |  |  |  |  |  | 1 |  |

Column C = Add CH status filter to Q13c1 and report clients in total, without regard to household type.
Column D = Add CH status filter to Q13b1 and report clients in total, without regard to household type.

### Q27: Youth Questions

To be completed if there are any youth served during the operating year
The questions on youth are a subset of questions required to be completed for all CoC APRs regarding youth households.
The Youth questions are designed, where possible, to reuse programming from a previous APR question with the application of a youth filter.
For all youth questions (Q27 series), “Youth” = any client age >= 12 and <= 24 provided that not one household member is above that age
range. If so, exclude the entire household including the person age >= 12 and <= 24.
Report Changes from APR Add Youth filter
Youth Questions Relevance FY 2024 to this question


With An Ongoing Subsidy


and Annual Assessment/Exit Status - Youth


| Youth Questions |  | Report |  |  | Changes from APR |  |  | Add Youth filter |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Relevance |  |  | FY 2024 |  |  | to this question |  |
| Q27a: Age of Youth | CoC APR |  |  | None |  |  | Q11 |  |  |
| Q27b: Parenting Youth | CoC APR |  |  | None |  |  | n/a |  |  |
| Q27d: Living Situation - Youth | CoC APR |  |  | None |  |  | Q15 |  |  |
| Q27e: Length of Participation - Youth | CoC APR |  |  | None |  |  | Q22a1 |  |  |
| Q27f1: Exit Destination - Youth | CoC APR |  |  | None |  |  | Q23c |  |  |
| Q27f2: Exit Destination - – Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy | CoC APR |  |  | None |  |  | Q23d |  |  |
| Q27g: Cash Income – Sources - Youth | CoC APR |  |  | None |  |  | Q17* |  |  |
| Q27h: Client Cash Income Category - Earned/Other Income Category - by Start and Annual Assessment/Exit Status - Youth | CoC APR |  |  | None |  |  | Q18* |  |  |
| Q27i: Disabling Conditions and Income for Youth at Exit | CoC APR |  |  | None |  |  | Q19b* |  |  |
| Q27j: Average and Median Length of Participation in Days - Youth | CoC APR |  |  | None |  |  | Q22b |  |  |

Report Changes from APR Add Youth filter
Youth Questions Relevance FY 2024 to this question


Youth


Started - Youth


* Q27g, Q27h, and Q27i also include youth heads of household who are minors, where the general questions (Q17, Q18, Q19b) apply only to
adults.

### Q27a: Age of Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F
Without With Children and With Only Unknown
1
Total Children Adults Children Household Type
2 12-17 ---
3 18-24 ---
Client Doesn’t Know/Prefers Not to --- --- --- --- ---
4
Answer
5 Data Not Collected --- --- --- --- ---
6 Total ---
Add Youth filter to Q11 for programming. Adjust age ranges as shown above.

| Youth Questions |  | Report |  |  | Changes from APR |  |  | Add Youth filter |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  | Relevance |  |  | FY 2024 |  |  | to this question |  |
| Q27k: Length of Time between Project Start Date and Housing Move-in Date - Youth | CoC APR |  |  | None |  |  | Q22c |  |  |
| Q27l: Length of Time Prior to Housing - based on 3.917 Date Homelessness Started - Youth | CoC APR |  |  | None |  |  | Q22e |  |  |
| Q27m: Education Status - Youth | CoC APR |  |  | None |  |  | N/A |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 12-17 |  |  |  |  |  |  | --- |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 18-24 |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |  |  |
| 4 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  | --- |  |  | --- |  |  | --- |  |  | --- | --- |  | --- |  |  |
|  | 5 |  | Data Not Collected |  |  |  | --- |  |  | --- |  |  | --- |  |  | --- |  |  | --- |  |
|  | 6 |  | Total |  |  |  |  |  |  |  |  |  |  |  |  |  |  | --- |  |  |


### Q27b: Parenting Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E
Total parenting Total children of
1
youth parenting youth Total Persons Total Households
2 Parent youth < 18
3 Parent youth 18 to 24
Field No Other Relevant Data Standards Required Relevant Data
3.15 Relationship to Head of Household 1, 2
Universe: Households with a youth who is a parent

> HMIS Reporting Glossary Reference: Active clients; Date of Birth/Age

Programming Instructions:
1. Use data attached to each head of household’s latest project stay in the report date range. Include all other clients present with the head
of household on that project stay who are also active in the date range. This is necessary in order to determine the “parenting youth”
status of the entire household, even though one or more of the household members may have another later project stay in the report
date range with a different head of household or as the head of household. Please note: this is a departure from most other questions
on this report which exclusively use data associated with each person’s latest project stay.
2. Apply the youth filter to the selected clients.
3. Of the youth clients, determine the heads of household ([relationship to head of household] = 1).

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total parenting youth |  |  | Total children of parenting youth |  |  | Total Persons |  |  | Total Households |  |  |
|  | 2 |  | Parent youth < 18 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Parent youth 18 to 24 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 3.15 |  |  | Relationship to Head of Household |  |  | 1, 2 |  |  |

4. With the youth heads of household, determine if any of the household members active in the report date range are the child of the head
of household ([relationship to head of household] = 2). Include clients of any age between 0 and 17 years old, even though clients below
age 12 would not normally be included in the universe of “youth”.
5. If the youth household has a child as determined in step 4:
   a. Report all heads of household plus all adults (age 18 – 24) in the household in column B according to the age of the head of household
(age < 18 on line 2, or 18-24 on line 3). Include all adults in the household regardless of [relationship to head of household].
   b. Report all children (age 0 - 17) in the household in column C according to the age of the head of household. This includes children age
0 to 11 who will not be reported in any other youth question. Only include children in the household where the [relationship to head of
household] = 2.
   c. Report all clients in the household in column D according to the age of the head of household. Include all members of the household
regardless of [relationship to head of household].
   d. Report the household itself in column E according to the age of the head of household.

### Q27d: Living Situation – Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F Z
Data Standards
1 Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
2 Homeless Situations

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | Homeless Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F Z
Data Standards
1 Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Place not meant for habitation (e.g., a 116
vehicle, an abandoned building,
3
bus/train/subway station/airport or
anywhere outside)
Emergency shelter, including hotel or 101
4 motel paid for with emergency shelter
voucher, Host Home shelter
5 Safe Haven 118
6 Subtotal
7 Institutional Situations
Foster care home or foster care group 215
8
home
Hospital or other residential non- 206
9
psychiatric medical facility
10 Jail, prison, or juvenile detention facility 207
11 Long-term care facility or nursing home 225
Psychiatric hospital or other psychiatric 204
12
facility
Substance abuse treatment facility or 205
13
detox center
14 Subtotal
15 Temporary Situations
Transitional housing for homeless
16 302
persons (including homeless youth)

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 3 |  |  | Place not meant for habitation (e.g., a vehicle, an abandoned building, bus/train/subway station/airport or anywhere outside) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 116 | 116 |  |
| 4 |  |  | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 101 |  |  |
|  | 5 |  | Safe Haven |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 118 |  |
|  | 6 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | Institutional Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 8 |  |  | Foster care home or foster care group home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 215 | 215 |  |
| 9 |  |  | Hospital or other residential non- psychiatric medical facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 206 |  |  |
|  | 10 |  | Jail, prison, or juvenile detention facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 207 |  |
|  | 11 |  | Long-term care facility or nursing home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 225 |  |
| 12 |  |  | Psychiatric hospital or other psychiatric facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 204 | 204 |  |
| 13 |  |  | Substance abuse treatment facility or detox center |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 205 |  |  |
|  | 14 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Temporary Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 16 |  |  | Transitional housing for homeless persons (including homeless youth) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 302 |  |  |

A B C D E F Z
Data Standards
1 Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Residential project or halfway house with
17 329
no homeless criteria
Hotel or motel paid for without
18 314
emergency shelter voucher
19 Host Home (non-crisis) 332
Staying or living in a friend’s room,
20 336
apartment, or house
Staying or living in a family member’s
21 335
room, apartment, or house
22 Subtotal
23 Permanent Situations
Rental by client, no ongoing housing
24 410
subsidy
Rental by client, with ongoing housing
25 435
subsidy
Owned by client, with ongoing housing
26 421
subsidy
Owned by client, no ongoing housing
27 411
subsidy
28 Subtotal
Client Doesn’t Know/Prefers Not to
29 8 or 9
Answer
30 Data Not Collected 99
31 Subtotal
32 TOTAL

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 17 |  |  | Residential project or halfway house with no homeless criteria |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 329 |  |  |
| 18 |  |  | Hotel or motel paid for without emergency shelter voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 314 |  |  |
|  | 19 |  | Host Home (non-crisis) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 332 |  |
| 20 |  |  | Staying or living in a friend’s room, apartment, or house |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 336 |  |  |
| 21 |  |  | Staying or living in a family member’s room, apartment, or house |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 335 |  |  |
|  | 22 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 23 |  | Permanent Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 24 |  |  | Rental by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 410 |  |  |
| 25 |  |  | Rental by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 435 |  |  |
| 26 |  |  | Owned by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 421 |  |  |
| 27 |  |  | Owned by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 411 |  |  |
|  | 28 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 29 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | 30 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 31 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 32 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Add youth filter to Q15 for programming. Note: this table only includes youth who are heads of a household.

### Q27e: Length of Participation - Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D
1 Total Leavers Stayers
2 30 days or less
3 31 to 60 days
4 61 to 90 days
5 91 to 180 days
6 181 to 365 days
7 366 to 730 days (1-2 Yrs)
8 731 to 1,095 days (2-3 Yrs)
9 1,096 to 1,460 days (3-4 Yrs)
10 1,461 to 1,825 days (4-5 Yrs)
11 More than 1,825 days (> 5 Yrs)
12 Total
Add youth filter to Q22a1 for programming.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  | Total |  |  | Leavers |  |  | Stayers |  |  |
|  | 2 |  | 30 days or less |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 731 to 1,095 days (2-3 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 1,096 to 1,460 days (3-4 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 1,461 to 1,825 days (4-5 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | More than 1,825 days (> 5 Yrs) |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Total |  |  |  |  |  |  |  |  |  |  |  |


### Q27f1: Exit Destination – Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
2 Homeless Situations
Place not meant for habitation (e.g., a
vehicle, an abandoned building,
3 116
bus/train/subway station/airport or
anywhere outside)
Emergency shelter, including hotel or
4 motel paid for with emergency shelter 101
voucher, Host Home shelter
5 Safe Haven 118
6 Subtotal
7 Institutional Situations
Foster care home or foster care group
8 215
home
Hospital or other residential non-
9 206
psychiatric medical facility
Jail, prison, or juvenile detention
10 207
facility
Long-term care facility or nursing
11 225
home

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | Homeless Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 |  |  | Place not meant for habitation (e.g., a vehicle, an abandoned building, bus/train/subway station/airport or anywhere outside) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 116 |  |  |
| 4 |  |  | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 101 |  |  |
|  | 5 |  | Safe Haven |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 118 |  |
|  | 6 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | Institutional Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 8 |  |  | Foster care home or foster care group home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 215 |  |  |
| 9 |  |  | Hospital or other residential non- psychiatric medical facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 206 |  |  |
| 10 |  |  | Jail, prison, or juvenile detention facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 207 |  |  |
| 11 |  |  | Long-term care facility or nursing home |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 225 |  |  |

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Psychiatric hospital or other
12 204
psychiatric facility
Substance abuse treatment facility or
13 205
detox center
14 Subtotal
15 Temporary Situations
Transitional housing for homeless
16 302
persons (including homeless youth)
Residential project or halfway house
17 329
with no homeless criteria
Hotel or motel paid for without
18 314
emergency shelter voucher
19 Host Home (non-crisis) 332
Staying or living with family, temporary
20 tenure (e.g., room, apartment, or 312
house)
Staying or living with friends,
21 temporary tenure (e.g., room, 313
apartment, or house)
Moved from one HOPWA funded
22 327
project to HOPWA TH
23 Subtotal
24 Permanent Situations

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 12 |  |  | Psychiatric hospital or other psychiatric facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 204 |  |  |
| 13 |  |  | Substance abuse treatment facility or detox center |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 205 |  |  |
|  | 14 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Temporary Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 16 |  |  | Transitional housing for homeless persons (including homeless youth) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 302 |  |  |
| 17 |  |  | Residential project or halfway house with no homeless criteria |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 329 |  |  |
| 18 |  |  | Hotel or motel paid for without emergency shelter voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 314 |  |  |
|  | 19 |  | Host Home (non-crisis) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 332 |  |
| 20 |  |  | Staying or living with family, temporary tenure (e.g., room, apartment, or house) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 312 |  |  |
| 21 |  |  | Staying or living with friends, temporary tenure (e.g., room, apartment, or house) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 313 |  |  |
| 22 |  |  | Moved from one HOPWA funded project to HOPWA TH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 327 |  |  |
|  | 23 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 24 |  | Permanent Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Staying or living with family,
25 422
permanent tenure
Staying or living with friends,
26 423
permanent tenure
Moved from one HOPWA funded
27 426
project to HOPWA PH
Rental by client, no ongoing housing
28 410
subsidy
Rental by client, with ongoing housing
29 435
subsidy
Owned by client, with ongoing housing
30 421
subsidy
Owned by client, no ongoing housing
31 411
subsidy
32 Subtotal
33 Other Situations
34 No Exit Interview completed 30
35 Other 17
36 Deceased 24
Client Doesn’t Know/Prefers Not to
37 8 or 9
Answer
38 Data Not Collected 99
39 Subtotal
40 TOTAL

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 25 |  |  | Staying or living with family, permanent tenure |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 422 |  |  |
| 26 |  |  | Staying or living with friends, permanent tenure |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 423 |  |  |
| 27 |  |  | Moved from one HOPWA funded project to HOPWA PH |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 426 |  |  |
| 28 |  |  | Rental by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 410 |  |  |
| 29 |  |  | Rental by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 435 |  |  |
| 30 |  |  | Owned by client, with ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 421 |  |  |
| 31 |  |  | Owned by client, no ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 411 |  |  |
|  | 32 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 33 |  | Other Situations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 34 |  | No Exit Interview completed |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 30 |  |
|  | 35 |  | Other |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 17 |  |
|  | 36 |  | Deceased |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 24 |  |
| 37 |  |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 8 or 9 |  |  |
|  | 38 |  | Data Not Collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 99 |  |
|  | 39 |  | Subtotal |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 40 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F Z
Data
Standards
1
Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
Total persons exiting to positive
41
housing destinations
Total persons exiting to destinations
42 that excluded them from the
calculation
Percentage of persons exiting to = B41 / = C42 / = D42 / = E42 / = F42 /
43 positive housing destinations (B40 – (C40 – (D40 – D42) (E40 – (F40 – F42)
B42) C42) E42)
Add Youth filter to Q23c for programming.

### Q27f2: Exit Destination – Subsidy Type of Persons Exiting to Rental by Client With An Ongoing Subsidy - Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F Z
Data Standards
1 Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
2 GPD TIP housing subsidy 428
3 VASH housing subsidy 419
4 RRH or equivalent subsidy 431

|  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 41 | Total persons exiting to positive housing destinations |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 42 | Total persons exiting to destinations that excluded them from the calculation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 43 | Percentage of persons exiting to positive housing destinations |  |  | = B41 / (B40 – B42) |  |  | = C42 / (C40 – C42) |  |  | = D42 / (D40 – D42) |  |  | = E42 / (E40 – E42) |  |  | = F42 / (F40 – F42) |  |  |  |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
|  | 2 |  | GPD TIP housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 428 |  |
|  | 3 |  | VASH housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 419 |  |
|  | 4 |  | RRH or equivalent subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 431 |  |

A B C D E F Z
Data Standards
1 Without With Children With Only Unknown Response
Total Children and Adults Children Household Type options
HCV voucher (tenant or project based)
5 433
(not dedicated)
6 Public housing unit 434
Rental by client, with other ongoing
7 420
housing subsidy
8 Housing Stability Voucher 436
Family Unification Program Voucher
9 437
(FUP)
Foster Youth to Independence Initiative
10 438
(FYI)
11 Permanent Supportive Housing 439
Other permanent housing dedicated for
12 440
formerly homeless persons
13 TOTAL
Add Youth filter to Q23d for programming.

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | options |  |
| 5 |  |  | HCV voucher (tenant or project based) (not dedicated) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 433 |  |  |
|  | 6 |  | Public housing unit |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 434 |  |
| 7 |  |  | Rental by client, with other ongoing housing subsidy |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 420 |  |  |
|  | 8 |  | Housing Stability Voucher |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 436 |  |
| 9 |  |  | Family Unification Program Voucher (FUP) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 437 |  |  |
| 10 |  |  | Foster Youth to Independence Initiative (FYI) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 438 |  |  |
|  | 11 |  | Permanent Supportive Housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 439 |  |
| 12 |  |  | Other permanent housing dedicated for formerly homeless persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | 440 |  |  |
|  | 13 |  | TOTAL |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


### Q27g: Cash Income – Sources - Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D
Income at Income at Latest Annual Income at Exit
1
Start Assessment for Stayers for Leavers
2 Earned Income
3 Unemployment Insurance
4 Supplemental Security Income (SSI)
5 Social Security Disability Insurance (SSDI)
6 VA Service – Connected Disability Compensation
7 VA Non-Service Connected Disability Pension
8 Private Disability Insurance
9 Worker’s Compensation
10 Temporary Assistance for Needy Families (TANF)
11 General Assistance (GA)
12 Retirement Income from Social Security
13 Pension or retirement income from a former job
14 Child Support
15 Alimony and other spousal support
16 Other Source
17 Youth with Income Information at Start and Annual Assessment/Exit ---
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Income at Start |  |  | Income at Latest Annual Assessment for Stayers |  |  | Income at Exit for Leavers |  |  |
|  | 2 |  | Earned Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Unemployment Insurance |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Supplemental Security Income (SSI) |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Social Security Disability Insurance (SSDI) |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | VA Service – Connected Disability Compensation |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | VA Non-Service Connected Disability Pension |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | Private Disability Insurance |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | Worker’s Compensation |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | Temporary Assistance for Needy Families (TANF) |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | General Assistance (GA) |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Retirement Income from Social Security |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | Pension or retirement income from a former job |  |  |  |  |  |  |  |  |  |  |  |
|  | 14 |  | Child Support |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Alimony and other spousal support |  |  |  |  |  |  |  |  |  |  |  |
|  | 16 |  | Other Source |  |  |  |  |  |  |  |  |  |  |  |
|  | 17 |  | Youth with Income Information at Start and Annual Assessment/Exit |  |  |  | --- |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |

Field No Other Relevant Data Standards Required Relevant Data
4.02 Income and Sources Earned Income and all other sources
Add youth filter to Q17, but expand universe to include youth adults AND youth heads of household even if they are not adults.

### Q27h: Client Cash Income Category - Earned/Other Income Category - by Start and Annual Assessment/Exit

Status - Youth

*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D
1 Number of Number of Youth at
Youth at Annual Assessment Number of Youth
Number of Youth By Income Category Start (Stayers) at Exit (Leavers)
2 Youth with Only Earned Income (i.e., Employment Income)
3 Youth with Only Other Income
4 Youth with Both Earned and Other Income
5 Youth with No Income
6 Youth with Client Doesn’t Know/Prefers Not to Answer Income
Information
7 Youth with Missing Income Information
8 Number of youth stayers not yet required to have an annual --- ---
assessment
9 Number of youth stayers without required annual assessment --- ---
10 Total Youth
11 1 or more source of income

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Number of Youth By Income Category |  |  | Number of Youth at Start |  |  | Number of Youth at Annual Assessment (Stayers) |  |  | Number of Youth at Exit (Leavers) |  |  |
|  | 2 |  | Youth with Only Earned Income (i.e., Employment Income) |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | Youth with Only Other Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | Youth with Both Earned and Other Income |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | Youth with No Income |  |  |  |  |  |  |  |  |  |  |  |
| 6 | 6 |  | Youth with Client Doesn’t Know/Prefers Not to Answer Income Information |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | Youth with Missing Income Information |  |  |  |  |  |  |  |  |  |  |  |
| 8 | 8 |  | Number of youth stayers not yet required to have an annual assessment |  |  | --- | --- |  |  |  |  | --- |  |  |
|  | 9 |  | Number of youth stayers without required annual assessment |  |  |  | --- |  |  |  |  |  | --- |  |
|  | 10 |  | Total Youth |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | 1 or more source of income |  |  |  |  |  |  |  |  |  |  |  |

A B C D
1 Number of Number of Youth at
Youth at Annual Assessment Number of Youth
Number of Youth By Income Category Start (Stayers) at Exit (Leavers)
12 Youth with Income Information at Start and Annual ---
Assessment/Exit
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
4.02 Income and Sources Earned Income and all other sources
Add youth filter to Q18, but expand universe to include youth adults AND youth heads of household even if they are not adults.

|  |  | A |  |  | B |  |  | C |  |  | D |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Number of Youth By Income Category |  |  | Number of Youth at Start |  |  | Number of Youth at Annual Assessment (Stayers) |  |  | Number of Youth at Exit (Leavers) |  |  |
| 12 | Youth with Income Information at Start and Annual Assessment/Exit |  |  | --- |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |


### Q27i: Disabling Conditions and Income for Youth at Exit


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F G H I J K L M N O P Q
1 AO: AO: AO: AO: AC: AC: AC: AC: CO: CO: CO: CO: UK: UK: UK: UK:
Youth Youth Total % with Youth Youth Total % with Youth Youth Total % with Youth Youth Total % with
with witho Youth Disabli with without Youth Disabli with without Yout Disablin with without Youth Disabling
Disabli ut ng Disabli Disablin ng Disabling Disabling h g Disabli Disabling Condition
ng Disabl Condit ng g Condit Conditio Conditio Conditi ng Conditio by Source
Condit ing ion by Condit Conditi ion by n n on by Conditi n
ion Condi Source ion on Source Source on
tion
2 Earned Income
3 Unemployment
Insurance
4 Supplemental
Security
Income (SSI)
5 Social Security
Disability
Insurance
(SSDI)
6 VA Service-
Connected
Disability
Compensation

|  | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  | AO: Youth with Disabli ng Condit ion | AO: Youth witho ut Disabl ing Condi tion | AO: Total Youth | AO: % with Disabli ng Condit ion by Source | AC: Youth with Disabli ng Condit ion | AC: Youth without Disablin g Conditi on | AC: Total Youth | AC: % with Disabli ng Condit ion by Source | CO: Youth with Disabling Conditio n | CO: Youth without Disabling Conditio n | CO: Total Yout h | CO: % with Disablin g Conditi on by Source | UK: Youth with Disabli ng Conditi on | UK: Youth without Disabling Conditio n | UK: Total Youth | UK: % with Disabling Condition by Source |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 2 | Earned Income |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 | Unemployment Insurance |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 | Supplemental Security Income (SSI) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 5 | Social Security Disability Insurance (SSDI) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 6 | VA Service- Connected Disability Compensation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F G H I J K L M N O P Q
7 VA Non-
Service-
Connected
Disability
Pension
8 Private
Disability
Insurance
9 Worker's
Compensation
10 Temporary
Assistance for
Needy Families
(TANF)
11 General
Assistance
(GA)
12 Retirement
Income from
Social Security
13 Pension or
retirement
income from a
former job
14 Child Support
15 Alimony and
other spousal
support
16 Other source

|  | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 7 | VA Non- Service- Connected Disability Pension |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 8 | Private Disability Insurance |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 9 | Worker's Compensation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 10 | Temporary Assistance for Needy Families (TANF) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 11 | General Assistance (GA) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 12 | Retirement Income from Social Security |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 13 | Pension or retirement income from a former job |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 14 | Child Support |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 15 | Alimony and other spousal support |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 16 | Other source |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F G H I J K L M N O P Q
17 No Sources
18 Unduplicated --- --- --- ---
Total Youth
Add youth filter to Q19b, but expand universe to include youth adults AND youth heads of household even if they are not adults. This results
in needing four additional columns (J through M) to accommodate child-only households, with the unknown-household columns staying at
the far right.
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects
3.08 Disabling Condition
4.02 Income and Sources Earned Income and all other sources

### Q27j: Average and Median Length of Participation in Days - Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C
1 Leavers Stayers
2 Average Length
3 Median Length
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type All projects

|  | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 17 | No Sources |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 18 | Unduplicated Total Youth |  |  |  | --- |  |  |  | --- |  |  |  | --- |  |  |  | --- |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |
| 3.08 |  |  | Disabling Condition |  |  |  |  |  |
| 4.02 |  |  | Income and Sources |  |  | Earned Income and all other sources |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | 1 |  |  |  |  | Leavers |  |  | Stayers |  |  |
|  | 2 |  | Average Length |  |  |  |  |  |  |  |  |
|  | 3 |  | Median Length |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | All projects |  |  |

Add youth filter to Q22b.

### Q27k: Length of Time between Project Start Date and Housing Move-in Date - Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F
Unknown
1 Without With Children With Only Household
Total Children and Adults Children Type
2 7 days or less
3 8 to 14 days
4 15 to 21 days
5 22 to 30 days
6 31 to 60 days
7 61 to 90 days
8 91 to 180 days
9 181 to 365 days
10 366 to 730 days (1-2 Yrs)
11 Total (persons moved into housing)
12 Average length of time to housing
13 Persons who were exited without move-in
14 Total persons

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 7 days or less |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 8 to 14 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 15 to 21 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 22 to 30 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | Total (persons moved into housing) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Average length of time to housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | Persons who were exited without move-in |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 14 |  | Total persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

Field No Other Relevant Data Standards Required Relevant Data
13 (RRH); 3 (PSH); and when reporting on project type 7 (Other) with
2.02.6 Project Type
2.06 Funding Source of HUD: Pay for Success (35)
3.20 Housing Move-in Date mm/dd/yyyy
Add youth filter to Q22c.

### Q27l: Length of Time Prior to Housing - based on 3.917 Date Homelessness Started - Youth


*Report Relevance: CoC APR*

*Changes from FY 2024: None*

A B C D E F
Unknown
1 Without With Children With Only Household
Total Children and Adults Children Type
2 7 days or less
3 8 to 14 days
4 15 to 21 days
5 22 to 30 days
6 31 to 60 days
7 61 to 90 days
8 91 to 180 days
9 181 to 365 days
10 366 to 730 days (1-2 Yrs)
11 731 days or more
12 Total (persons moved into housing)
13 Not yet moved into housing

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 13 (RRH); 3 (PSH); and when reporting on project type 7 (Other) with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |
| 3.20 |  |  | Housing Move-in Date |  |  | mm/dd/yyyy |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 2 |  | 7 days or less |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 |  | 8 to 14 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 4 |  | 15 to 21 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 5 |  | 22 to 30 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 6 |  | 31 to 60 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 |  | 61 to 90 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 8 |  | 91 to 180 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 9 |  | 181 to 365 days |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 10 |  | 366 to 730 days (1-2 Yrs) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 11 |  | 731 days or more |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 12 |  | Total (persons moved into housing) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 13 |  | Not yet moved into housing |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

A B C D E F
Unknown
1 Without With Children With Only Household
Total Children and Adults Children Type
14 Data not collected
15 Total persons
Field No Other Relevant Data Standards Required Relevant Data
0 (ES-EE); 1 (ES-NbN); 2 (TH); 3 (PSH); 8 (SH); 9 (PH); 13 (RRH); and
2.02.6 Project Type when reporting on project type 7 (Other) with 2.06 Funding Source of
HUD: Pay for Success (35)
3.917.3 Approximate date this episode started
3.20 Housing Move-in Date mm/dd/yyyy
Add youth filter to Q22e.

### Q27m: Education Status – Youth

*Changes from FY 2024: None*

A B C Z
Data Standards
1
Current school and attendance At Project Start At Project Exit Response
2 Not currently enrolled in any school or education course C3 = 0
3 Currently enrolled but not attending regularly C3 = 1
4 Currently enrolled and attending regularly C3 = 2
5 Client Doesn’t Know / Prefers Not to Answer C3 = 8 or 9

|  |  |  |  | A |  |  | B |  |  | C |  |  | D |  |  | E |  |  | F |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  | Total |  |  | Without Children |  |  | With Children and Adults |  |  | With Only Children |  |  | Unknown Household Type |  |  |
|  | 14 |  | Data not collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 15 |  | Total persons |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 0 (ES-EE); 1 (ES-NbN); 2 (TH); 3 (PSH); 8 (SH); 9 (PH); 13 (RRH); and when reporting on project type 7 (Other) with 2.06 Funding Source of HUD: Pay for Success (35) |  |  |
| 3.917.3 |  |  | Approximate date this episode started |  |  |  |  |  |
| 3.20 |  |  | Housing Move-in Date |  |  | mm/dd/yyyy |  |  |


|  |  |  |  | A |  |  | B |  |  | C |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Current school and attendance |  |  | At Project Start |  |  | At Project Exit |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  | 2 |  | Not currently enrolled in any school or education course |  |  |  |  |  |  |  |  |  | C3 = 0 |  |
|  | 3 |  | Currently enrolled but not attending regularly |  |  |  |  |  |  |  |  |  | C3 = 1 |  |
|  | 4 |  | Currently enrolled and attending regularly |  |  |  |  |  |  |  |  |  | C3 = 2 |  |
|  | 5 |  | Client Doesn’t Know / Prefers Not to Answer |  |  |  |  |  |  |  |  |  | C3 = 8 or 9 |  |

A B C Z
Data Standards
1
Current school and attendance At Project Start At Project Exit Response
6 Data not collected C3 = 99
7 For those not enrolled – most recent education status --- ---
8 K12: Graduated from high school C3.A = 0
9 K12: Obtained GED C3.A =1
10 K12: Dropped out C3.A =2
11 K12: Suspended C3.A =3
12 K12: Expelled C3.A =4
13 Higher education: Pursuing a credential but not currently attending C3.A =5
14 Higher education: Dropped out C3.A =6
15 Higher education: Obtained a credential/degree C3.A =7
16 Client Doesn’t Know/Prefers Not to Answer C3.A = 8 or 9
17 Data not collected C3.A = 99
18 For those currently enrolled – current status --- ---
19 Pursuing a high school diploma or GED C3.B = 0
20 Pursuing Associate Degree C3.B = 1
21 Pursuing Bachelor Degree C3.B = 2
22 Pursuing Graduate Degree C3.B = 3
23 Pursuing other post-secondary credential C3.B = 4
24 Client Doesn’t Know/Prefers Not to Answer C3.B = 8 or 9
25 Data not collected C3.B = 99
26 Total persons
Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type 2 (TH); 3 (PSH); 4 (SO); 6 (SSO); 13 (RRH)
C3 Youth Education Status All

|  |  |  |  | A |  |  | B |  |  | C |  |  | Z |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  | Current school and attendance |  |  | At Project Start |  |  | At Project Exit |  |  |  | Data Standards |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  | Response |  |
|  | 6 |  | Data not collected |  |  |  |  |  |  |  |  |  | C3 = 99 |  |
|  | 7 |  | For those not enrolled – most recent education status |  |  |  | --- |  |  | --- |  |  |  |  |
|  | 8 |  | K12: Graduated from high school |  |  |  |  |  |  |  |  |  | C3.A = 0 |  |
|  | 9 |  | K12: Obtained GED |  |  |  |  |  |  |  |  |  | C3.A =1 |  |
|  | 10 |  | K12: Dropped out |  |  |  |  |  |  |  |  |  | C3.A =2 |  |
|  | 11 |  | K12: Suspended |  |  |  |  |  |  |  |  |  | C3.A =3 |  |
|  | 12 |  | K12: Expelled |  |  |  |  |  |  |  |  |  | C3.A =4 |  |
|  | 13 |  | Higher education: Pursuing a credential but not currently attending |  |  |  |  |  |  |  |  |  | C3.A =5 |  |
|  | 14 |  | Higher education: Dropped out |  |  |  |  |  |  |  |  |  | C3.A =6 |  |
|  | 15 |  | Higher education: Obtained a credential/degree |  |  |  |  |  |  |  |  |  | C3.A =7 |  |
|  | 16 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  | C3.A = 8 or 9 |  |
|  | 17 |  | Data not collected |  |  |  |  |  |  |  |  |  | C3.A = 99 |  |
|  | 18 |  | For those currently enrolled – current status |  |  |  | --- |  |  | --- |  |  |  |  |
|  | 19 |  | Pursuing a high school diploma or GED |  |  |  |  |  |  |  |  |  | C3.B = 0 |  |
|  | 20 |  | Pursuing Associate Degree |  |  |  |  |  |  |  |  |  | C3.B = 1 |  |
|  | 21 |  | Pursuing Bachelor Degree |  |  |  |  |  |  |  |  |  | C3.B = 2 |  |
|  | 22 |  | Pursuing Graduate Degree |  |  |  |  |  |  |  |  |  | C3.B = 3 |  |
|  | 23 |  | Pursuing other post-secondary credential |  |  |  |  |  |  |  |  |  | C3.B = 4 |  |
|  | 24 |  | Client Doesn’t Know/Prefers Not to Answer |  |  |  |  |  |  |  |  |  | C3.B = 8 or 9 |  |
|  | 25 |  | Data not collected |  |  |  |  |  |  |  |  |  | C3.B = 99 |  |
|  | 26 |  | Total persons |  |  |  |  |  |  |  |  |  |  |  |


|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 2 (TH); 3 (PSH); 4 (SO); 6 (SSO); 13 (RRH) |  |  |
| C3 |  |  | Youth Education Status |  |  | All |  |  |

Field No Other Relevant Data Standards Required Relevant Data
2.02.6 Project Type 2 (TH); 3 (PSH); 4 (SO); 6 (SSO); 13 (RRH)
C3.A Most Recent Educational Status All
C3.B Current Educational Status All
Universe: Youth heads of household who exited from YHDP-funded projects in the report date range

> HMIS Reporting Glossary Reference: Active Client; Date of Birth/Age; Household Types; Unduplicated Household Counts; and Unduplicated

Client Counts by Household Type
Programming Instructions:
1. Report the distinct counts of youth heads of household by their responses in [youth education status] and any relevant dependencies.
See Reporting counts of clients by element by household type for column instructions.
2. Column B reports on leavers according to their value at project start. Column C reports on leavers according to their value at project exit.
Stayers are excluded from this question.
3. Report included clients in rows 2-6 according to their response to [current school enrollment and attendance].
4. On rows 8-17, report clients where [current school enrollment and attendance] = 0 according to their response to [most recent
educational status].
5. On rows 19-25, report clients where [current school enrollment and attendance] = 1 or 2 according to their response to [current
educational status].
6. On row 26, report the distinct count of all included clients.

|  | Field No |  |  | Other Relevant Data Standards Required |  |  | Relevant Data |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2.02.6 |  |  | Project Type |  |  | 2 (TH); 3 (PSH); 4 (SO); 6 (SSO); 13 (RRH) |  |  |
| C3.A |  |  | Most Recent Educational Status |  |  | All |  |  |
| C3.B |  |  | Current Educational Status |  |  | All |  |  |

Appendix A: Exit Destinations
Destinations indicated with an ✗ cause leavers with those destinations to be completely excluded from the entire measure universe. Clients
whose destination is indicated with an ✔ will be included in the measure universe. Undefined project types should use the “HP & PH (all)”
column when determining positive exit destinations.
HP &
Data Standards
ES- ES- PH
Response
Exit Destinations SO EE NbN TH (all) SH SSO
Homeless Situations (100-199)
Emergency shelter, including hotel or motel paid for with
101 ✔
emergency shelter voucher, Host Home shelter
116 Place not meant for habitation
118 Safe Haven ✔
Institutional Situations (200-299)
206 Hospital or other residential non-psychiatric medical facility ✗ ✗ ✗ ✗ ✗ ✗ ✗
215 Foster care home or foster care group home ✔ ✗ ✗ ✗ ✗ ✗ ✗
207 Jail, prison, or juvenile detention facility
204 Psychiatric hospital or other psychiatric facility ✔
205 Substance abuse treatment facility or detox center ✔
225 Long-term care facility or nursing home ✔ ✗ ✗ ✗ ✗ ✗ ✗
Temporary Housing Situations (300-399)
329 Residential project or halfway house with no homeless criteria ✗
314 Hotel or motel paid for without emergency shelter voucher ✔
312 Staying or living with family, temporary tenure ✔
313 Staying or living with friends, temporary tenure ✔
Transitional housing for homeless persons (including homeless ✔
302
youth)
327 Moved from one HOPWA funded project to HOPWA TH ✔

| Data Standards Response |  |  | Exit Destinations |  |  | SO |  |  | ES- EE |  |  | ES- NbN |  |  | TH |  |  |  | HP & |  | SH |  |  | SSO |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | PH |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | (all) |  |  |  |  |  | SSO |  |
|  | Homeless Situations (100-199) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 101 |  |  | Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 116 |  |  | Place not meant for habitation |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 118 |  |  | Safe Haven |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | Institutional Situations (200-299) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 206 |  |  | Hospital or other residential non-psychiatric medical facility |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |
| 215 |  |  | Foster care home or foster care group home |  |  |  | ✔ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |
| 207 |  |  | Jail, prison, or juvenile detention facility |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 204 |  |  | Psychiatric hospital or other psychiatric facility |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 205 |  |  | Substance abuse treatment facility or detox center |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 225 |  |  | Long-term care facility or nursing home |  |  |  | ✔ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |
|  | Temporary Housing Situations (300-399) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 329 |  |  | Residential project or halfway house with no homeless criteria |  |  |  | ✗ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 314 |  |  | Hotel or motel paid for without emergency shelter voucher |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 312 |  |  | Staying or living with family, temporary tenure |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 313 |  |  | Staying or living with friends, temporary tenure |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 302 |  |  | Transitional housing for homeless persons (including homeless youth) |  |  | ✔ | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 327 |  |  | Moved from one HOPWA funded project to HOPWA TH |  |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| Data Standards |
| --- |
| Response |


| ES- |
| --- |
| EE |


| ES- |
| --- |
| NbN |

HP &
Data Standards
ES- ES- PH
Response
Exit Destinations SO EE NbN TH (all) SH SSO
332 Host Home (non-crisis) ✔ ✔ ✔ ✔
Permanent Housing Situations (400-499)
426 Moved from one HOPWA funded project to HOPWA PH ✔ ✔ ✔ ✔ ✔ ✔ ✔
411 Owned by client, no ongoing housing subsidy ✔ ✔ ✔ ✔ ✔ ✔ ✔
421 Owned by client, with ongoing housing subsidy ✔ ✔ ✔ ✔ ✔ ✔ ✔
410 Rental by client, no ongoing housing subsidy ✔ ✔ ✔ ✔ ✔ ✔ ✔
435 Rental by client, with housing subsidy ✔ ✔ ✔ ✔ ✔ ✔ ✔
422 Staying or living with family, permanent tenure ✔ ✔ ✔ ✔ ✔ ✔ ✔
423 Staying or living with friends, permanent tenure ✔ ✔ ✔ ✔ ✔ ✔ ✔
Other (1-99)
24 Deceased ✗ ✗ ✗ ✗ ✗ ✗ ✗
8 Client doesn’t know
9 Client prefers not to answer
99 Data not collected
30 No exit interview completed
17 Other
This material is based upon work supported, in whole or in part, by Federal award number H-20-NP-VA-001 awarded to ICF by the U.S. Department of Housing
and Urban Development for NHDAP-related technical assistance. The substance and findings of the work are dedicated to the public. Neither the United
States Government, nor any of its employees, makes any warranty, express or implied, or assumes any legal liability or responsibility for the accuracy,
completeness, or usefulness of any information, apparatus, product, or process disclosed, or represents that its use would not infringe privately-owned rights.
Reference herein to any individuals, agencies, companies, products, process, services, service by trade name, trademark, manufacturer, or otherwise does not
constitute or imply an endorsement, recommendation, or favoring by the author(s), contributor(s), the U.S. Government or any agency thereof. Opinions
contained herein are those of the author(s) and do not necessarily reflect the official position of, or a position that is endorsed by, HUD or any Federal agency.

| Data Standards Response |  |  | Exit Destinations |  |  | SO |  |  | ES- EE |  |  | ES- NbN |  |  | TH |  |  |  | HP & |  | SH |  |  | SSO |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |  |  |  | ES- |  |  | ES- |  |  |  |  |  | PH |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  | SO |  |  | EE |  |  | NbN |  |  | TH |  |  | (all) |  |  |  |  |  |  |  |
| 332 |  |  | Host Home (non-crisis) |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  |  |  |  |  |  |  |  |  |
|  | Permanent Housing Situations (400-499) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 426 |  |  | Moved from one HOPWA funded project to HOPWA PH |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
| 411 |  |  | Owned by client, no ongoing housing subsidy |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
| 421 |  |  | Owned by client, with ongoing housing subsidy |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
| 410 |  |  | Rental by client, no ongoing housing subsidy |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
| 435 |  |  | Rental by client, with housing subsidy |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
| 422 |  |  | Staying or living with family, permanent tenure |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
| 423 |  |  | Staying or living with friends, permanent tenure |  |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |  | ✔ |  |
|  | Other (1-99) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 24 |  |  | Deceased |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |  | ✗ |  |
| 8 |  |  | Client doesn’t know |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 9 |  |  | Client prefers not to answer |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 99 |  |  | Data not collected |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 30 |  |  | No exit interview completed |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 17 |  |  | Other |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


| Data Standards |
| --- |
| Response |
