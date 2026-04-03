# HMIS CSV Format Specifications

**Version 1.0**

**U.S. Department of Housing and Urban Development**

ALIGNS WITH FY 2026 HMIS DATA STANDARDS | RELEASED OCTOBER 2025
FOR REPORTING BEGINNING OCTOBER 1, 2025

---

## **Contents**

**Revisions for FY 2026**  **Overview**  **Document Purpose and Scope**  **Document Format**  **File Definitions**  **Fields Not Defined in the HMIS Data Dictionary**  _Unique Identifiers_  _Date Deleted_  _Data Types_  **General Rules and Assumptions**  **Export**  **Import**  **Export Characteristics**  **Export Period Types**  **Reporting Period**  **Updated**  **Other**  **Export Directive Types**  _Delta refresh_  _Full refresh_  _Other_  **Hash Status**  _Unhashed_  _SHA-1_  _Hashed – other_  _SHA-256_  **Export File**  **Export.csv**  **Project Descriptor Files**  **Organization.csv**
**User.csv**  **Project.csv**  **Funder.csv**  **ProjectCoC.csv**  **Affiliation.csv**  **HMISParticipation.csv**  **CEParticipation.csv**  **Client File**  **Client.csv**  **Enrollment Files**  **Enrollment.csv**  **Exit.csv**  **IncomeBenefits.csv**  **HealthAndDV.csv**  **EmploymentEducation.csv**  **Disabilities.csv**  **Services.csv**  **CurrentLivingSituation.csv**  **Assessment.csv**  **AssessmentQuestions.csv**  **AssessmentResults.csv**  **Event.csv**  **YouthEducationStatus.csv**  **Appendix A – List of Data Elements and Associated CSV Files**  **Appendix B – Lists**  **Notes**  **Appendix C – Custom File Transfer Template**
## **Revisions for FY 2026**

|**Date**||**Version**|**Description**|**Description**|
|---|---|---|---|---|
|October|2025|1.0|Overview||
||||•|Removed any reference to the XML specifications – deprecated as|
|||||of FY 2024 Data Standards|
||||•|Added note regarding expected testing availability timeline|
||||Document Format: Characters Permitted in String Fields||
||||•|Updated to reflect the significantly expanded allowable character|
|||||set (UTF-8)|
||||Export.csv||
||||•|Added a note to SourceID to allow for the inclusion of multiple CoC|
|||||Codes, as appropriate|
||||•|Significantly expanded character limit for SourceID from 32 to 350 to|
|||||accommodate listing of up to 50 CoCs in a single export|
||||•|Removed SourceType instruction to type multi-CoC HMIS|
|||||implementations as data warehouses|
||||Client.csv||
||||•|Added note that veteran elements are expected to be null for non-|
|||||veterans|
||||•|Removed 3.06 Gender|
||||•|Added 4.21 Sex|
||||Enrollment.csv||
||||•|Updated lists for R13 to 1.8 from 1.10|
||||•|Added V10 MentalHealthConsultation|
||||•|Removed R3 Sexual Orientation|
||||•|Removed C4 Translation Assistance Needed|
||||Exit.csv||
||||•|Updated list for R20.A (multiple columns), R18.1 CounselingReceived,|
|||||R18.A (multiple columns), and R18.3 PostExitCounselingPlan to 1.10|
|||||instead of 1.7|
||||CurrentLivingSituation.csv||
||||•|Updated maximum length for 4.12.3 VerifiedBy to S200|
||||Lists||
||||•|Added information regarding retired list items in “Notes” section|
||||•|2.06.1 FundingSource|
|||||`o` Added “HUD: CoC Builds” (56)|
|||||`o` Marked “HUD: ESG-CV” (47) and “HUD: HOPWA-CV” (48)|
|||||retired|
||||•|V2.2 SSVFServices|
|||||`o` Added “Healthcare navigation” (10)|
||||Label||
||||•|Updated label for Hispanic/Latina/e/o to Hispanic/Latina/o|
## **Overview**

The US Department of Housing and Urban Development (HUD), in cooperation with the Department of Health and Human Services (HHS) and the Department of Veterans Affairs (VA), is responsible for the Homeless Management Information System (HMIS) Data Standards, which define data collection requirements for any software used as an HMIS. The first version of the data standards was published in 2004; the current version, FY 2026 HMIS Data Standards, has an effective date of October 1, 2025. HUD expects that vendors will have fiscal year data standards updates available for testing in HMIS by communities at least one month prior to the changes taking effect.

This document provides specifications for a standard set of comma-separated values (CSV) files that include all data elements and fields defined by the FY 2026 HMIS Data Standards, along with information that describes an exported data set.

The structure of the files and their relationships are based on the original HMIS Logical Model; although, the HMIS CSV is less granular than that of the model to reduce the overall number of files.

The files have been denormalized to facilitate a simplified structure under circumstances where it is appropriate. For example, in a fully normalized structure, _Inventory.csv_ records could only be joined with _Project.csv_ records using _ProjectCoC.csv_ as an intermediary, but in these files _Inventory.csv_ is denormalized to include ProjectID. This allows for a direct join to _Project.csv_ when working with a data set that has been filtered to include only one CoC.

## **Document Purpose and Scope**

There are several purposes for which HMIS data might be exported from one system and imported to another. The use cases that the HMIS CSV format is primarily intended to support include:

- Migration from one HMIS application to another;

- Warehousing of data from multiple HMIS implementations for analysis and reporting;

- Self-service analytics and data quality tools that rely on the HMIS CSV schema; and

- Participation in a local HMIS implementation by regularly providing data entered and exported from an alternate database.

This document is primarily technical; it describes a common format and associated basic expectations and assumptions related to the processes of exporting and importing HMIS data in a standard manner. In general, HUD expects that it should be possible to export, in a standard format, all data entered into an HMIS for any data element defined by the HMIS Data Dictionary, regardless
of whether a given data element is required based on project type or funder.

The HMIS Data Dictionary defines several hundred fields. HUD is aware that there is, in addition, a wide variety of expanded and customized data collection in HMIS instances across the country.

While HUD is cognizant that the exchange of additional data that may be included in an HMIS will often be useful and necessary, it is not practical to include accommodations for every potential need, even if it were possible to anticipate them. As a result, the scope of this document is generally limited to data collected in a manner consistent with the HMIS Data Dictionary. The HMIS CSV format may be extended to include additional files and fields by parties engaged in HMIS data exchange; technical assistance may be available. A sample CSV template for custom HMIS data exchange is located in Appendix C.

To request technical assistance please visit www.hudexchange.info.

## **Document Format**

This document defines CSV files and fields required for data exchange of all data elements defined in the HMIS Data Dictionary, basic rules and assumptions for HMIS export and import processes, and general descriptions of terms used.

Appendix A lists all FY 2026 HMIS Data Standards data elements and the CSV file in which they appear.

Appendix B includes response categories and associated data exchange values for all option list fields defined in the FY 2026 HMIS Data Standards.

## **File Definitions**

For each file defined by the HMIS CSV Specifications, this document includes a description of general requirements for the file and a table listing each field with basic requirements for the field.

Files are grouped into the following sections based on the informational entity to which the data pertains: Export, Project Descriptor, Client, and Enrollment.

The references to data elements defined in the HMIS Data Dictionary are in bold type (e.g., **3.03.01 Date of Birth** ) and references to specific fields in both the Data Dictionary and the CSV format are italicized ( _Date of Birth_ ).  The tables include the columns described below:
|**Column**|**Description**||
|---|---|---|
|**DE#**|This is the data standards identification of fields; it includes the data element number and field identifier (numbers for primary fields||
||and letters for dependent fields) as listed in the HMIS Data Dictionary.||
||For example, the data quality indicator for a client’s date of birth is part of data element||
||**3.03 Date of Birth**; the field for data quality is listed as Field 2. Accordingly, the DE# for the field is 3.03.2.||
||Data that are repeated in multiple files only have a DE# identified in the file where they originate. For example,**5.08 Personal ID**||
||serves as a unique identifier (primary key) in||
||Client.csv and its DE# is listed there. The same identifier is used to associate data in other CSV files with a client (foreign key), but||
||the DE# is not listed when it appears in other files.||
|**Name**|This lists the CSV field name for each field defined. While field names are intended to be recognizable when compared to those in the||
||HMIS Data Dictionary, many have been shortened. For example, field 3.03.01 is listed as_Date of Birth_in the HMIS Data Dictionary, but||
||when detailed in the Client.csv table its name is shortened to_DOB_.||
||Beginning with the FY2024 HMIS CSV Specifications, column headers are case-sensitive and must appear exactly as defined in the||
||HMIS CSV Specifications. No column header uses an underscore (_) and all column headers must utilize a Pascal case naming||
||convention where the first letter of each compound word in a variable is capitalized.||
|**Type**|The data type for the field. The types included are defined in the Data Types section.||
|**List**|Fields that have response categories defined in the HMIS Data Dictionary or in this document will have a list number in this column.||
||List numbers are hyperlinked to Appendix B,which includes all lists by number with data exchange values and text equivalents.||
||Lists that are specific to the HMIS CSV export have two-part list numbers that begin with 1; the second part is sequential. For||
||example, the list for_ExportPeriodType_, which is used in Export.csv, has a list number of 1.1.||
||Frequently used lists such as (No/Yes/Missing) and (No/Yes/Client doesn’t know/Client Prefers Not to Answer/Missing) are numbered||
||following a 1.X pattern rather than re- defining them for each field in which they appear.||
||Other lists are numbered to correspond to the DE# for the field in which they first appear and have three-part list numbers (e.g., the||
||list for the date of birth data quality field is numbered 3.03.2).||
**Column Description**

**Null** Fields that may be null are identified with a Y (for Yes). Any field not specifically permitted to be null should have an exported value of the appropriate data type; for non-nullable fields with response categories defined in the HMIS Data Dictionary, 99 (Data not collected) should be exported for blank fields/missing data unless otherwise specified.

**Notes** Includes definitions, specific validation requirements, and other relevant information. Regular expressions are included for some fields as a supplement to descriptions of validation requirements; they are included as a convenience only and there is no requirement to use them.

## **Fields Not Defined in the HMIS Data Dictionary**

### Unique Identifiers
Based on a need expressed by HMIS vendors, every file includes a field that serves as a unique identifier for each record in the file. In some cases, these unique identifiers are defined in the HMIS Data Dictionary. For example, the unique identifier for Project.csv is **2.02 Project Information** _Project ID_ . In other cases, the unique identifier is not defined in the HMIS Data Dictionary but is assumed to exist in the exporting database.

Values exported in these fields should correspond to actual values in the exporting database. Where a single file (such as IncomeBenefits.csv) includes multiple data elements and requires combining multiple records, each of which has its own unique identifier, the lowest value should be used.

### Date Deleted
Based on a need expressed by HMIS vendors, every file includes a _DateDeleted_ field. This metadata is not defined by the HMIS Data Dictionary but will be necessary for any system participating in data exchange that updates instead of completely replaces previously transmitted data.

### Data Types
Data types and maximum field lengths defined here apply to unhashed data. When data in one or more fields are hashed – and the receiver requires or has agreed to accept hashed data – the data types and validation processes for those fields may differ depending
## on the hashing parameters.

## The HMIS CSV specifications include the following data types:

|**Type**||**ID**|**Definition**|
|---|---|---|---|
|**Date**||D|A date in the format YYYY-MM-DD|
|**Datetime**||T|A date and time in the format YYYY-MM-DD hh:mm:ss|
|**Integer**||I|A non-negative whole number. For fields with a list number in the_List_column,|
||||valid values are limited to those defined for the field by the HMIS Data Dictionary|
||||or in this document.|
|**Money**||M|Number with two decimal places (no commas and no currency symbol);|
||||numbers may be negative|
|**Money**||M+|Non-negative number with two decimal places (no commas and no currency|
||||symbol)|
|**String**||S#|A combination of letters, numbers, and standard punctuation (see list of|
||||characters permitted in string fields below); the number following the ‘S’|
||||identifies the maximum number of characters permitted for a given field. For|
||||example, fields with a data type of S50 are limited to 50 characters. String fields|
||||must be padded with double-quotes.|


1 In CSV files opened with MS Excel, date and datetime data are automatically reformatted. Even if a user makes no other changes, saving the file will save the dates in the Excel format. It is tedious but possible to reset the dates to the CSV format using “Format Cells/Custom” menu options so that the file will pass validation checks.
## **Characters Permitted in String Fields**

Double-quotes must be exported as "" (two double-quote characters) if a double-quote character is part of the data; alternatively, they may be replaced by a single-quote character in the export process. As of October 1, 2025, HMIS CSV exports must allow for the export of all UTF-8 characters as entered by users, with the exception of the following: < > [ ] { }

If any of these six characters are part of data entered by a user, the characters should be stripped out in the export process.

## **General Rules and Assumptions**

As noted earlier, the HMIS CSV may be extended to include additional files and fields by agreement, as long as the HMIS software is still able to produce an HMIS CSV export that aligns with the HMIS CSV Specifications in addition to the extended export. The rules and assumptions defined here may also be relaxed or modified – also by agreement – to facilitate the exchange of non-standard data (e.g., service records not associated with an _EnrollmentID_ ). Non-standard data should not be included in exported files without prior agreement. Beginning with the FY2024 HMIS CSV

Specifications, column headers are case-sensitive and must appear exactly as defined in the HMIS CSV Specifications. No column header uses an underscore (_) and all column headers must utilize a Pascal case naming convention where the first letter of each compound word in a variable is capitalized.

## **Export**

1. The first row in each file must include the field names as they are listed in this document.

2. Official HMIS CSV files may not contain additional fields.

3. It should be possible to export, in a standard format, all data entered into an HMIS for any data element defined by the HMIS Data Dictionary, regardless of whether a given data element is required based on project type or funder.

4. If response categories in an HMIS instance differ from those defined in the data standards, they must be exported with the value of the most appropriate response category defined in the HMIS Data Dictionary. For example, if the response categories for _Relationship to Head of Household_ have been expanded to include ‘Husband or wife’ and ‘Unmarried partner,’ both must be exported as ‘Head of household’s spouse or partner’ with a value of 3.

5. Unless a field is specifically identified as allowing null values, all fields must contain data. For fields with response categories defined in the data standards, blank/missing values will be
exported with a value of 99, which is defined by the HMIS Data Dictionary as ‘Data not collected’.

6. Dependent fields will be null unless the parent field contains the value defined by the HMIS Data Dictionary.

7. Values stored as placeholders in an exporting database that have no informational value must be exported as if they were null. For example, if the stored value for a Social Security Number is ‘000000000’ because the database does not permit a null value for the field, the zeroes may not be exported in the SSN field; the value in the SSN field in the exported file should be null unless a value was entered by an HMIS end user.

8. Export processes must use parameters entered by an HMIS end user to identify data required for export.    Required parameters include Export Start Date, Export End Date, Project(s), and CoC Code.

9. Export parameters are referenced in this document as ExportStart, ExportEnd, Projects, and CoCCode.

10. All files required for a given export will be generated as part of a single process to minimize the possibility of inconsistent or partial data caused by HMIS end users adding or editing records as the files are being created.

11. To facilitate data exchange, reporting, and analytics across CoCs, HMIS implementations or instances, and service delivery areas, Export.csv is required to identify the generating HMIS or comparable database through the _ImplementationID_ field. Vendors may assign a unique ID to each HMIS or comparable database implementation, based on GUID, customer account numbers, or other information that is unique to the implementation. Each implementation should include a consistent _ImplementationID_ in every export produced and should not change over time.

## **Import**

1. Import validation processes may (but are not required to) reject a data set in whole or in part if any part of the data set is inconsistent with the specifications contained in this document.

2. Import processes may skip validation for files and/or fields which are not relevant.
## **Export Characteristics**

## **Export Period Types**

## **Reporting Period**

‘Reporting period’ exports include all records needed for reporting on clients and enrollments active in the export period. This will include all records in enrollment files (regardless of _Date Created_ , _Date Updated_ , etc.), client files, and project descriptor files associated with an _EnrollmentID_ where:

- _Project Start Date_ is on or before the Export End Date;

- _Project Exit Date_ is null OR Project Exit Date is on or after the Export Start Date;

- _Information Date_ is on or before the Export End Date (i.e., data “from the future” relative to the export range is **not** included, just as it is not included in standard HMIS reporting). Data prior to the export range should be included so long as it is attached to an enrollment which is active in the range.

- _ProjectID_ (s) are associated with one or more projects selected by a user for export  OR the user did not choose to filter the export by Project;

- A _CoC Code_ associated with the _EnrollmentID_ (s) matches one or more _CoC Code_ (s) selected by a user for export OR the user did not choose to filter the export by _CoC Code_ .

## **Updated**

Exported data sets with an _ExportPeriodType_ of ‘updated’ will include all records with a _Date Created_ , _Date Updated_ , or _Date Deleted_ that fall between the Export Start Date and the Export End Date.

## **Other**

The ‘Other’ _ExportPeriodType_ is used to identify exports in which records were selected based upon parameters mutually agreed upon by the sender and recipient of the CSV data.

## **Export Directive Types**

### Delta refresh
Exported data sets with an _ExportDirective_ of ‘Delta refresh’ (1) are intended to be synchronized with an existing data set/previously transmitted data in the receiving database and include only information that is new or different since the last time data were synchronized.
### Full refresh
Exported data sets with an _ExportDirective_ of ‘Full refresh’ (2) are intended to completely replace any previously transmitted data in the receiving database.

### Other
The ‘Other’ (3) _ExportDirective_ is used to identify exports in which records were selected based upon parameters mutually agreed upon by the sender and recipient of the CSV data.

## **Hash Status**

### Unhashed
Data sets with a _HashStatus_ of ‘Unhashed’ (1) data are expected to conform to data type and field length parameters defined in this document.

### SHA-1
Note: For federal data exchange purposes, this is a legacy methodology. RHY requires use of SHA256 (see below). The SHA-1 algorithm produces a 40-character string of letters and numbers. Data sets with a _HashStatus_ of ‘SHA-1 RHY’ (2) will be exported consistent with the specifications of this document with the exception that the following fields in Client.csv (and no others) will be hashed using the SHA-1 standard algorithm and data types for these four fields will differ as noted:

- _FirstName_ (S40)– SHA-1 hash of the SOUNDEX of the value for first name;

- _MiddleName_ (S40) – SHA-1 hash of the SOUNDEX of the value for middle name;

- _LastName_ (S40) – SHA-1 hash of the SOUNDEX of the value for last name; and

- _SSN_ (S44) – concatenation of the unhashed last 4 digits of the SSN followed by SHA-1 hash of the full SSN. In the case of a partial SSN, use a lower-case letter x to replace any missing digits. The resultant 9-character string will be hashed in the same manner as a complete SSN.

### Hashed – other
The ‘Other’ (3) _HashStatus_ is used to identify exports in which data are hashed based on parameters mutually agreed upon by the sender and recipient of the CSV data.

### SHA-256
The SHA-256 algorithm produces a 64-character string of letters and numbers. Data sets with a _HashStatus_ of ‘SHA-256’ (4) will be exported consistent with the specifications of this document
with the exception that the following fields in Client.csv (and no others) will be hashed using the SHA-256 standard algorithm and data types for these four fields will differ as noted:

- _FirstName_ (S64)– SHA-256 hash of the SOUNDEX of the value for first name;

- _MiddleName_ (S64) – SHA-256 hash of the SOUNDEX of the value for middle name;

- _LastName_ (S64) – SHA-256 hash of the SOUNDEX of the value for last name; and

- _SSN_ (S68) – concatenation of the unhashed last 4 digits of the SSN followed by SHA-256 hash of the full SSN. In the case of a partial SSN, use a lower-case letter x to replace any missing digits. The resultant 9-character string will be hashed in the same manner as a complete SSN.
## **Export File**

## **Export.csv**

Export.csv includes information about the export itself and is always required. For each export, there must be one and only one record in Export.csv. The _ExportID_ in this file should be unique to the exporting application – i.e., a new _ExportID_ should be created each time data are exported – and will be used to identify all CSV files generated as a part of the same export process.

|**Name**|**Type**| **List**| **Null**| **Notes**|
|---|---|---|---|---|
|**ExportID**|S32|||Unique identifier|
|**SourceType**|I|1.9||Identifies whether the source database is a continuum-operated HMIS (1), an agency-specific database (2), a data warehouse (3), or other (4).|
|**SourceID**|S350||Y|If_SourceType_= 1, this field may not be null and must identify the HUD CoC Code/s of|
|||||the HMIS implementation from which data are being exported in the format of two|
|||||letters, a dash, and 3 numbers.|
|||||^[a-zA-Z]{2}-[0-9]{3}$|
|||||If more than one CoC Code was selected by the user for export, all selected CoC|
|||||Codes should be included here in a semicolon-separated list|
|||||(ex. “XX-501;XX-502”)|
|||||If_SourceType_<> 1, this field may be null or used to specify other characteristics, as|
|||||agreed upon by sender and receiver.|
|**SourceName**|S50||Y|If the source database is not an HMIS implementation (if_SourceType_<> 1), this field|
|||||may not be null and must identify the organization responsible for the database.|
|**SourceContactFirst**|S50||Y|The first name of the user generating the export.|
|**SourceContactLast**|S50||Y|The last name of the user generating the export.|
|**SourceContactPhone**|S10||Y|The phone number of the user generating the export. Limited to 10 digits/no|
|||||punctuation.|
|||||[2-9][0-9]{2}[2-9][0-9]{2}[0-9]{4}|
|**Name**||**Type**|**List**| **Null**| **Notes**||
|---|---|---|---|---|---|---|
|**SourceContactExtension**||S5||Y|The phone extension of the user generating the export, if available. Limited to 5||
||||||digits/no punctuation.||
||||||[0-9]{1,5}||
|**SourceContactEmail**||S320||Y|The email address of the user generating the export, if available.||
||||||Valid email addresses only||
|**ExportDate**||T|||The date and time that the export process was initiated.||
|**ExportStartDate**||D|||The user-entered start date for the export period.||
|**ExportEndDate**||D|||The user-entered end date for the export period; the_ExportEnd_should be the same||
||||||as the_ExportStart_for exports of HIC data.||
|**SoftwareName**||S50|||The name of the software generating the export.||
|**SoftwareVersion**||S50||Y|The version number of the software, if applicable.||
|**CSVVersion**||S50||Y|The version number of the CSV Specification. Format is required to be [year]||
||||||v[version|number]. For example, version 1.0 of the FY2026 CSV specifications would|
||||||be "2026|v1.0"|
|**ExportPeriodType**||I|1.1||||
|**ExportDirective**||I|1.2||||
|**HashStatus**||I|1.5||||
|**ImplementationID**||S200|||A vendor-generated ID that is unique to every source database, regardless of the||
||||||number of CoCs participating in the implementation.||


## **Project Descriptor Files**

## **Organization.csv**

The unique identifier for Organization.csv is _2.01.1 Organization ID_ , which is used in Project.csv to associate a project with a specific organization.

Organization.csv includes all the fields from data element **2.01 Organization Information.**
This file includes a field that is referenced but not defined in the HMIS Data Dictionary:

_OrganizationCommonName_ . Use of this field is entirely optional.

There must be one record in Organization.csv for each _OrganizationID_ in Project.csv.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
|**2.01.1**|OrganizationID|S32|||Unique identifier|
|**2.01.2**|OrganizationName|S200||||
|**2.01.3**|VictimServiceProvider|I|1.10|||
||OrganizationCommonName|S200||Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match record in Export.csv|


## **User.csv**

The unique identifier for User.csv is **5.07.1 UserID** ; the _UserID_ in this file is used to associate data in other CSV files with a specific user, whether active or inactive at the time of the export. User.csv must include user information for all users included in other tables in the same CSV files. Additional export protocols may be established locally. User.csv includes the metadata element **5.07 User Identifier** .

This file includes fields that are not defined in the HMIS Data Dictionary: _UserFirstName, UserLastName,  UserPhone, UserExtension, UserEmail._
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
|**5.07.01**|UserID|S32|||Unique Identifier|
||UserFirstName|S50||Y|The first name of the user if available|
||UserLastName|S50||Y|The last name of the user if available|
||UserPhone|S10||Y|The phone number of the user if available. Limited to 10 digits/no|
||||||punctuation.|
||||||[2-9][0-9]{2}[2-9][0-9]{2}[0-9]{4}|
||UserExtension|S5||Y|The phone extension of the user, if available. Limited to 5 digits/no|
||||||punctuation.|
||||||[0-9]{1,5}|
||UserEmail|S320||Y|The email address of the user, if available.|
||||||Valid email addresses only|
||DateCreated|T||||
||DateUpdated|T||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match record in Export.csv|


## **Project.csv**

The unique identifier for Project.csv is _2.02.1 Project ID_ **;** the _ProjectID_ in this file is used to associate data in other CSV files with a specific project.

Project.csv includes all the fields from data element **2.02 Project Information.**

Project.csv includes two fields that are not defined in the HMIS Data Dictionary: _ProjectCommonName_ and _PITCount_ . Use of both fields is optional.

For data sets that include client data, there must be one and only one record in Project.csv for each _ProjectID_ in  Enrollment.csv.

Project.csv must include records for all projects selected by the user for inclusion in the export and for any _ResProjectID_ in Affiliation.csv.
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
|**2.02.1**|ProjectID|S32|||Unique identifier|
|**2.01.1**|OrganizationID|S32|||Must match a record in Organization.csv|
|**2.02.2**|ProjectName|S200||||
||ProjectCommonName|S200||Y||
|**2.02.3**|OperatingStartDate|D||||
|**2.02.4**|OperatingEndDate|D||Y||
|**2.02.5**|ContinuumProject|I|1.10|||
|**2.02.6**|ProjectType|I|2.02.6|Y|May be null if_ContinuumProject_<>|
||||||1|
|**2.02.D**|HousingType|I|2.02.D|Y||
|**2.02.A**|RRHSubType|I|2.02.A|Y|Non-null if_ProjectType = 13_|
|**2.02.B**|ResidentialAffiliation|I|1.10|Y|Non-null if_ProjectType_= 6 or (_ProjectType_= 13|
||||||and_RRHSubType_= 1)|
|**2.02.7**|TargetPopulation|I|2.02.7|Y||
|**2.02.8**|HOPWAMedAssistedLivingFac|I|2.02.8|Y||
||PITCount|I||Y|Used for the HIC; a count of active clientson the|
||||||date of the PIT Count|
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|


> 2 Refer to the HMIS Standard Reporting Terminology Glossary for logic associated with counting active clients.
## **Funder.csv**

Funder.csv includes data from data element **2.06 Funding Sources** .

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||FunderID|S32|||Unique identifier|
||ProjectID|S32|||Must match a record in Project.csv|
|**2.06.1**|Funder|I|2.06.1|||
|**2.06.A**|OtherFunder|S100||Y|Required if 2.06.1 = 46|
|**2.06.2**|GrantID|S100||Y||
|**2.06.3**|StartDate|D||||
|**2.06.4**|EndDate|D||Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match the_ExportID_in Export.csv|
## **ProjectCoC.csv**

ProjectCoC.csv includes data for data element 2.03 Continuum of Care Code.  There may be, but do not have to be, multiple records in ProjectCoC.csv for each record in Project.csv where ContinuumProject is equal to 1 (Yes).

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||ProjectCoCID|S32|||Unique identifier|
||ProjectID|S32|||Must match a_ProjectID_in Project.csv|
|**2.03.1**|CoCCode|S6|||Two letters, a dash, and 3 numbers|
||||||^[a-zA-Z]{2}-[0-9]{3}$|
|**2.03.2**|Geocode3|S6||Y|Limited to six digits|
||||||^[0-9]{6}$|
|**2.03.3**|Address1|S100||Y||
|**2.03.4**|Address2|S100||Y||
|**2.03.5**|City|S50||Y||
|**2.03.6**|State|S2||Y|Limited to USPS-defined two-letter abbreviations4|
||||||^[a-zA-Z]{2}$|
|**2.03.7**|ZIP|S5||Y|Limited to five digits|
||||||^[0-9]{5}$|
|**2.03.8**|GeographyType|I|2.03.4|Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match the_ExportID_in Export.csv|


> 3 Note that _Geocode_ and _ZIP_ both have a data type of string and must be exported as such/padded with double- quotes so that leading zeroes are not omitted. If ZIP codes are collected with a four-digit suffix, only the first five digits should be exported.

4 A complete list of valid US states, territories, and military duty areas is available athttps://pe.usps.com/text/pub28/28apb.htm.
## **Inventory.csv**

Inventory.csv includes data for **2.07 Bed and Unit Inventory Information** .

There may be multiple records in Inventory.csv:

- For each combination of ProjectID and CoCCode in ProjectCoC.csv where ProjectType in Project.csv is equal to 0, 1, 2, 3, 8, 9, 10, or 13 and RRHSubType =2;

- For each CoCCode, _Household Type,_ and/or _ES Bed Type_ in a single project;

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||InventoryID|S32|||Unique identifier|
||ProjectID|S32|||Must match a_ProjectID_in ProjectCoC.csv|
|**2.07.3**|CoCCode|S6||Y|Must match a_CoCCode_in ProjectCoC.csv for the same|
||||||_ProjectID_|
|**2.07.4**|HouseholdType|I|2.07.4|||
|**2.07.6**|Availability|I|2.07.6|Y|Null unless Project.csv|
||||||_ProjectType_= 0 or 1|
|**2.07.15**|UnitInventory|I||||
|**2.07.14**|BedInventory|I||||
|**2.07.7**|CHVetBedInventory|I||Y||
|**2.07.8**|YouthVetBedInventory|I||Y||
|**2.07.9**|VetBedInventory|I||Y||
|**2.07.10**|CHYouthBedInventory|I||Y||
|**2.07.11**|YouthBedInventory|I||Y||
|**2.07.12**|CHBedInventory|I||Y||
|**2.07.13**|OtherBedInventory|I||Y||
|**2.07.5**|ESBedType|I|2.07.5|Y|Null unless Project.csv|
||||||_ProjectType_= 0 or 1|
|**DE#**|**Name**|**Type**|List|**Null**|**Notes**|
|---|---|---|---|---|---|
|**2.07.1**|InventoryStartDate|D||||
|**2.07.2**|InventoryEndDate|D||Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match the_ExportID_in Export.csv|


## **Affiliation.csv**

Affiliation.csv includes information from **2.02.C** about associations between projects with a project type of 6 (Services Only) or project type 13 subtype 1 (RRH Services Only) and lodging projects.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||AffiliationID|S32|||Unique identifier|
||ProjectID|S32|||Must match a_ProjectID_in Project.csv where|
||||||_(ProjectType_= 6) or (_ProjectType_= 13 and_RRHSubType_= 1)|
|**2.02.C**|ResProjectID|S32|||Must match a record in Project.csv where|
||||||_ProjectType_= 0, 1, 2, 3, 8, 9, 10, or 13. If_ProjectType_= 13,|
||||||_RRHSubType_must be 2.|
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S|||Must match the_ExportID_in Export.csv|
## **HMISParticipation.csv**

HMISParticipation.csv includes information from 2.08 HMIS Participation Status. There may be, but do not have to be, multiple records in HMISParticipation.csv for each record in Project.csv.

|**DE#**|**Name**||**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|---|
||HMISParticipationID||S32|||Unique identifier|
||ProjectID||S32|||Must match a_ProjectID_in Project.csv|
|**2.08.1**|HMISParticipationType||I|2.08.1|||
|**2.08.2**|HMISParticipationStatusStartDate||D||||
|**2.08.3**|HMISParticipationStatusEndDate||D||Y||
||DateCreated||T||||
||DateUpdated||T||||
||UserID||S32||||
||DateDeleted||T||Y||
||ExportID||S|||Must match the_ExportID_in Export.csv|


## **CEParticipation.csv**

CEParticipation.csv includes information from 2.09 CE Participation. There may be, but do not have to be, multiple records in CEParticipation.csv for each record in Project.csv.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||CEParticipationID|S32|||Unique identifier|
||ProjectID|S32|||Must match a_ProjectID_in Project.csv|
|**2.09.1**|AccessPoint|I|1.10|||
|**2.09.A**|PreventionAssessment|I|1.10|Y|Non-null if 2.09.1 = 1. If option not selected, should be set|
||||||to 0|
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**2.09.A**|CrisisAssessment|I|1.10|Y|Non-null if 2.09.1 = 1. If option not selected, should be set|
|---|---|---|---|---|---|
||||||to 0|
|**2.09.A**|HousingAssessment|I|1.10|Y|Non-null if 2.09.1 = 1. If option not selected, should be set|
||||||to 0|
|**2.09.A**|DirectServices|I|1.10|Y|Non-null if 2.09.1 = 1. If option not selected, should be set|
||||||to 0|
|**2.09.2**|ReceivesReferrals|I|1.10|||
|**2.09.3**|CEParticipationStatusStartDate|D||||
|**2.09.4**|CEParticipationStatusEndDate|D||Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S|||Must match the_ExportID_in Export.csv|
## **Client File**

The Client file includes data for which there is one and only one value for each client record.

## **Client.csv**

The unique identifier for Client.csv is **5.08 Personal Identifier** _(PersonalID)_ , which is used to associate data in other CSV files with a specific person.

Other data elements included in Client.csv are:

- **3.01 Name**

- **3.02 Social Security Number**

- **3.03 Date of Birth**

- **3.04 Race and Ethnicity**

- **4.21 Sex**

- **3.07 Veteran Status**

## • **V1 Veteran’s Information**

V1 responses are expected to be null for clients where Veteran Status is not equal to 1.

For each _PersonalID_ in Enrollment.csv, there must be one and only one record in Client.csv. Client.csv should not include records for any _PersonalID_ that does not have at least one record in Enrollment.csv.

While the HMIS Data Standards require metadata for each individual data element, the HMIS CSV includes only a single set of metadata for the client record.

- _DateCreated_ should be the earliest _DateCreated_ associated with the _PersonalID_ for any of the included data elements.

- _DateUpdated_ should be the latest _DateUpdated_ associated with the _PersonalID_ for any of the included data elements.

- _UserID_ should be the _UserID_ associated with the record with the latest _DateUpdated_ for any of the included data elements.
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
|**5.08**|PersonalID|S32|||Unique identifier|
|**3.01.1**|FirstName|S50||Y|See notes in Hash Statussection re: field|
||||||sizes for hashed data.|
|**3.01.2**|MiddleName|S50||Y|See notes in Hash Statussection re: field|
||||||sizes for hashed data.|
|**3.01.3**|LastName|S50||Y|See notes in Hash Statussection re: field|
||||||sizes for hashed data.|
|**3.01.4**|NameSuffix|S50||Y||
|**3.01.5**|NameDataQuality|I|3.01.5|||
|**3.02.1**|SSN|S9||Y|See notes in Hash Statussection re: field sizes for hashed|
||||||data.|


The letter x is the only permissible non- numeric character and should be used to indicate the position of omitted digits ^[0-9xX]{9}$5F[6]

|**3.02.2**|SSNDataQuality|I|3.02.2||
|---|---|---|---|---|
|**3.03.1**|DOB|D||Y|
|**3.03.2**|DOBDataQuality|I|3.03.2||
|**4.21**|Sex|I|4.21|Y|
|**3.04.1**|AmIndAKNative|I|1.10||
|**3.04.1**|Asian|I|1.10||
|**3.04.1**|BlackAfAmerican|I|1.10||


1 = American Indian, Alaska Native, or Indigenous

0 = (This race not selected.)

1 = Asian or Asian American

0 = (This race/ethnicity not selected.)

1 = Black, African American, or African

0 = (This race/ethnicity not selected.)

5 SSN is a string field; values MUST be enclosed in double-quotes so that leading zeroes are not omitted.

> 6 Although this regular expression allows for the use of either a lower- or upper-case ‘x’ for unhashed exports, a RHY export specifically requires that missing digits be replaced with a lower-case ‘x’ prior to hashing.
|**DE#**|**Name**||**Type**|**List**|**Null**|**Notes**||
|---|---|---|---|---|---|---|---|
|**3.04.1**|HispanicLatinao||I|1.10||1 = Hispanic/Latina/o||
|||||||0 = (This race/ethnicity not selected.)||
|**3.04.1**|MidEastNAfrican||I|1.10||1 = Middle Eastern or North African||
|||||||0 = (This race/ethnicity not selected.)||
|**3.04.1**|NativeHIPacific||I|1.10||1 = Native Hawaiian or|Pacific Islander|
|||||||0 = (This race/ethnicity not selected.)||
|**3.04.1**|White||I|1.10||1 = White||
|||||||0 = (This race/ethnicity not selected.)||
|**3.04.1**|RaceNone||I|1.6|Y|Non-null only if all other race fields = 0||
|**3.04.2**|AdditionalRaceEthnicity||S100||Y|||
|**3.07.1**|VeteranStatus||I|1.8||Export 99 (Data not collected) for all clients, including||
|||||||minors, for whom there is no Veteran Status data.||
|**V1.1**|YearEnteredService||I||Y|Values between 1920|and the current year|
|||||||^(19[2-8][0-9]|199[0-||
|||||||9]|20[01][0-9]|202[0-6])$||
|**V1.2**|YearSeparated||I||Y|Values between 1920|and the current year|
|||||||^(19[2-8][0-9]|199[0-||
|||||||9]|20[01][0-9]|202[0-6])$$||
|**V1.3**|WorldWarII||I|1.8|Y|||
|**V1.4**|KoreanWar||I|1.8|Y|||
|**V1.5**|VietnamWar||I|1.8|Y|||
|**V1.6**|DesertStorm||I|1.8|Y|||
|**V1.7**|AfghanistanOEF||I|1.8|Y|||
|**V1.8**|IraqOIF||I|1.8|Y|||
|**V1.9**|IraqOND||I|1.8|Y|||
|**V1.10**|OtherTheater||I|1.8|Y|||
|**DE#**|**Name**||**Type**|**List**|**Null**|**Notes**||


> 7 This regular expression will validate for any year between 1920 and 2026. Data quality checks in import processes  may flag future dates as errors.
|**V1.11**|MilitaryBranch|I|V1.11|Y|
|---|---|---|---|---|
|**V1.12**|DischargeStatus|I|V1.12|Y|
||DateCreated|T|||
||DateUpdated|T|||
||UserID|S32|||
||DateDeleted|T||Y|
||ExportID|S32|||


Must match the _ExportID_ in Export.csv

## **Enrollment Files**

An enrollment is the period in which a person is considered a client of a project. An enrollment begins on the date specified in **3.10 Project Start Date** ( _EntryDate_ ) and ends on the date specified in **3.11 Project Exit Date** ( _ExitDate_ ). Both are universal data elements required for all clients of all projects participating in an HMIS, regardless of project type or funder.

As defined by the HMIS Data Dictionary, all data elements in these files must be associated with **5.06 EnrollmentID** metadata. While an HMIS software may permit users to create records for some of these data elements without associating the records with a specific _EnrollmentID_ , these data would fall outside of the scope of data collection defined by HUD, HHS, and VA in the data standards.

_Enrollment.csv_ is the core for all enrollment data; the _EnrollmentID_ in Enrollment.csv is used in all other enrollment-related files to link records to a specific enrollment. _PersonalID_ is also repeated in each of the enrollment-related files.

Other enrollment-related files may capture transactions that occur within enrollments at different data collection stages. Files that include a data collection stage should have no more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 1 (project entry) or 3 (project exit). There may be multiple records for the same _EnrollmentID_ where the data collection stage is 2 (project update) or 5 (annual assessment).
## **Enrollment.csv**

The unique identifier for Enrollment.csv is **5.06 EnrollmentID** , which is used to associate data in other CSV files with a specific enrollment.

Data elements included in Enrollment.csv have one and only one value per enrollment and are collected prior to project exit:

- **3.08 Disabling Condition**

- **3.917 Prior Living Situation**

- **3.10 Project Start Date**

- **3.15 Relationship to Head of Household**

- **3.20 Housing Move-In Date**

- **4.13 Date of Engagement**

- **P3 PATH Status**

- **R1 Referral Source**

- **R2 RHY-BCP Status**

- **R11 Formerly a Ward of Child Welfare/Foster Care Agency**

- **R12 Formerly a Ward of Juvenile Justice System**

- **R13 Family Critical Issues**

- **V4 Percent of AMI**

- **V6 VAMC Station Number**

- **V7 SSVF HP Targeting Criteria**

## • **V10 Mental Health Consultation**

While the HMIS Data Standards require metadata for each individual data element, the HMIS CSV includes only a single set of metadata for the data elements included in Enrollment.csv.

- _ProjectID_ and _EnrollmentID_ should be the metadata values associated with **3.10 Project Start Date** ; other fields should be populated using data associated with the same
## _EnrollmentID_ .

- _EntryDate_ is considered the information date for the other fields in Enrollment.csv except for the following data elements:

  - **4.13 Date of Engagement -** _DateOfEngagement_

- **3.20 Housing Move-In Date -** _MoveInDate_

- **P3 PATH Status -** _DateOfPATHStatus_

  - **R2 RHY-BCP Status** - _DateOfBCPStatus_

- _DateCreated_ should be the _DateCreated_ associated with **3.10 Project Start Date** ( _EntryDate_ ) for the same EnrollmentID.

- _DateUpdated_ should be the latest _DateUpdated_ associated with any of the included data elements for the same _EnrollmentID_ .

- _UserID_ should be the _UserID_ associated with the record with the latest _DateUpdated_ for any of the included data elements.

Because each record in Enrollment.csv corresponds to data elements where only one value per enrollment is required, there may be no more than one record for any _PersonalID_ with the same _EnrollmentID_ . If there is more than one record for the same _PersonalID_ with the same _EnrollmentID_ , this represents an error in the CSV export algorithm. If there is more than one record for the same _PersonalID_ with the same _EntryDate_ but with different _EnrollmentIDs_ , this is allowable but may represent an error in data entry (same record typed in twice) or error in CSV export algorithm.

The HMIS Data Dictionary requires identification of one and only one individual for whom _RelationshipToHoH_ = 1 (“Self (Head of Household)”) for each project entry. Receiving systems may reject a data set in whole or in part if data are not consistent with this requirement.
|**DE#**||**Name**|**Type**||**List**|**Null**|**Notes**|
|---|---|---|---|---|---|---|---|
|**5.06.1**||EnrollmentID|S32||||Unique identifier|
|**5.08.1**||PersonalID|S32|||||
|**2.02.1**||ProjectID|S32||||Must match a_ProjectID_in|
||||||||Project.csv|
|**3.10.1**||EntryDate|D|||||
|**5.09.1**||HouseholdID|S32|||||
|**3.15.1**||RelationshipToHoH|I||3.15.1|||
|**3.16.1**||EnrollmentCoC|S6|||Y|Must match a record in ProjectCoC.csv  with|
||||||||the same_ProjectID_|
||||||||^[A-Za-z]{2}-(0-9){3}$|
|**3.917.1**||LivingSituation|I||3.12.1|Y||
|**3.917.A**||RentalSubsidyType|I||3.12.A|Y|Null unless 3.917.1 = 435|
|**3.917.2**||LengthOfStay|I||3.917.2|Y||
|**3.917.2A &**|**2B**|LOSUnderThreshold|I||1.7|Y||
|**3.917.2C**||PreviousStreetESSH|I||1.7|Y||
|**3.917.3**||DateToStreetESSH|D|||Y||
|**3.917.4**||TimesHomelessPastThreeYears|I||3.917.4|Y||
|**3.917.5**||MonthsHomelessPastThreeYears|I||3.917.5|Y||
|**3.08**||DisablingCondition|I|1.8|||Export 99 (Data not collected) for any|
||||||||project entry where there is no|
||||||||response.|
|**4.13.1**||DateOfEngagement|D|||Y||
|**3.20.1**||MoveInDate|D|||Y||
|**P3.1**||DateOfPATHStatus|D|||Y||
|**P3.2**||ClientEnrolledInPATH|I||1.7|Y||
|**P3.A**||ReasonNotEnrolled|I|P3.A||Y|Null unless P3.2 = 0|
|**V4.1**||PercentAMI|I|V4.1||Y||
|**R1.1**||ReferralSource|I|R1.1||Y||
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
|**R1.A**|CountOutreachReferralApproaches|I||Y||
|**R2.1**|DateOfBCPStatus|D||Y||
|**R2.2**|EligibleForRHY|I|1.7|Y||
|**R2.A**|ReasonNoServices|I|R2.A|Y|Null unless R2.2 = 0|
|**R2.B**|RunawayYouth|I|1.8|Y|Null unless R2.2 = 1|
|**R11.1**|FormerWardChildWelfare|I|1.8|Y||
|**R11.A**|ChildWelfareYears|I|R11.A|Y||
|**R11.B**|ChildWelfareMonths|I||Y||
|**R12.1**|FormerWardJuvenileJustice|I|1.8|Y||
|**R12.A**|JuvenileJusticeYears|I|R11.A|Y||
|**R12.B**|JuvenileJusticeMonths|I||Y||
|**R13.9**|UnemploymentFam|I|1.8|Y||
|**R13.11**|MentalHealthDisorderFam|I|1.8|Y||
|**R13.15**|PhysicalDisabilityFam|I|1.8|Y||
|**R13.21**|AlcoholDrugUseDisorderFam|I|1.8|Y||
|**R13.22**|InsufficientIncome|I|1.8|Y||
|**R13.24**|IncarceratedParent|I|1.8|Y||
|**V6.1**|VAMCStation|S5|V6.1|Y|List includes non-integer values;|
||||||data type is still a string.|
|**V7.1**|TargetScreenReqd|I|1.7|Y||
|**V7.A**|TimeToHousingLoss|I|V7.A|Y||
|**V7.B**|AnnualPercentAMI|I|V7.B|Y||
|**V7.C**|LiteralHomelessHistory|I|V7.C|Y||
|**V7.D**|ClientLeaseholder|I|1.7|Y||
|**V7.E**|HOHLeaseholder|I|1.7|Y||
|**V7.F**|SubsidyAtRisk|I|1.7|Y||
|**V7.G**|EvictionHistory|I|V7.G|Y||
|**V7.H**|CriminalRecord|I|1.7|Y||
|**V7.I**|IncarceratedAdult|I|V7.I|Y||
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**V7.J**|PrisonDischarge|I|1.7|Y||
|---|---|---|---|---|---|
|**V7.K**|SexOffender|I|1.7|Y||
|**V7.L**|DisabledHoH|I|1.7|Y||
|**V7.M**|CurrentPregnant|I|1.7|Y||
|**V7.N**|SingleParent|I|1.7|Y||
|**V7.O**|DependentUnder6|I|V7.O|Y||
|**V7.P**|HH5Plus|I|1.7|Y||
|**V7.Q**|CoCPrioritized|I|1.7|Y||
|**V7.R**|HPScreeningScore|I||Y||
|**V7.S**|ThresholdScore|I||Y||
|**V10**|MentalHealthConsultation|I|V10|Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S|||Must match the_ExportID_in Export.csv|
## **Exit.csv**

Exit.csv includes data from:

- **3.11 Project Exit Date**

- **3.12 Destination**

- **W5 Housing Assessment at Exit**

- **R15 Commercial Sexual Exploitation/Sex Trafficking**

- **R16 Labor Exploitation/Trafficking**

- **R17 Project Completion Status**

- **R18 Counseling**

- **R19 Safe and Appropriate Exit**

- **R20 Aftercare Plans**

## • **V9 HUD-VASH Exit Information**

These data are not included in Enrollment.csv to preserve metadata such that it is possible to evaluate the timeliness of data entry for exit information.

There may be no more than one record in Exit.csv for any _EnrollmentID_ . EnrollmentIDs that do not have a corresponding Exit Date will not have a record in the Exit.csv file.

_ExitID_ is the unique identifier for Exit.csv. The _ExitID_ may be the unique identifier associated with

_Project Exit Date_ in the exporting database or it may be the same as the _EnrollmentID_ .

While the HMIS Data Standards require metadata for each individual data element, the HMIS CSV includes only a single set of metadata for the data elements included in the file.

- _DateCreated_ should be the _DateCreated_ associated with **3.11 Project Exit Date** ( _ExitDate)._

- _ExitDate_ is considered the information date for all fields in Exit.csv.

- _DateUpdated_ should be the latest _DateUpdated_ associated with any of the included data elements for the same _EnrollmentID_ .

- _UserID_ should be the _UserID_ associated with the record with the latest _DateUpdated_
associated with any of the included data elements for the same _EnrollmentID_ .

In the HMIS Data Dictionary, **R20 Aftercare Plans** is structured such that the four methods of providing aftercare are in a single option list field (Dependent A) with instructions to allow users to select as many options as apply in a single field _or_ to allow multiple records to be created. In the CSV, there is a separate Yes/No field for each method. Regardless of how the data element is implemented in HMIS:

- All R20 fields must be null in the CSV unless there is a record in HMIS:

   - With a user entered R20 Field 1 _Information Date_ that is between the _ExitDate_ and the _ExitDate + 180 days;_ AND

   - A user-entered response for R20 Field 2 _Aftercare was provided._

- If there are multiple records in the appropriate date range, _AftercareDate_ should reflect the most recent date in the range.

- If there are multiple records in the appropriate date range and responses to _Aftercare was provided_ are different, populate the _AftercareProvided_ field using the first of the following values that occurs in any record:

   - Yes (1)

   - Client Prefers Not to Answer (9)

   - No (0)

- If _AftercareProvided_ = 1, then:

   - The value for the field for any method of provision identified on a record in the appropriate date range must be 1.

   - The value for the field for any method not identified must be 0.

- If _AftercareProvided_ <> 1, all fields for methods of provision must be null.
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||ExitID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**3.11.1**|ExitDate|D||||
|**3.12.1**|Destination|I|3.12.1|||
|**3.12.A**|DestinationSubsidyType|I|3.12.A|Y|Null unless_Destination_= 435|
|**3.12.B**|OtherDestination|S50||Y|Null unless_Destination_= 17|
|**W5.1**|HousingAssessment|I|W5.1|Y||
|**W5.A &**|SubsidyInformation|I|W5.AB|Y|Includes data for W5.A and W5.B.|
|**.B**||||||
|**R17.1**|ProjectCompletionStatus|I|R17.1|Y||
|**R17.A**|EarlyExitReason|I|R17.A|Y|Null unless R17.1 = 3|
|**R15.1**|ExchangeForSex|I|1.8|Y||
|**R15.A**|ExchangeForSexPastThreeMonths|I|1.8|Y|Null unless R15.1 = 1|
|**R15.B**|CountOfExchangeForSex|I|R15.B|Y|Null unless R15.1 = 1|
|**R15.C**|AskedOrForcedToExchangeForSex|I|1.8|Y|Null unless R15.1 = 1|
|**R15.D**|AskedOrForcedToExchangeForSexPastThreeMonths|I|1.8|Y|Null unless R15.C = 1|
|**R16.1**|WorkplaceViolenceThreats|I|1.8|Y||
|**R16.2**|WorkplacePromiseDifference|I|1.8|Y||
|**R16.A**|CoercedToContinueWork|I|1.8|Y|Null unless R16.1 or R16.2 = 1|
|**R16.B**|LaborExploitPastThreeMonths|I|1.8|Y|Null unless R16.1 or R16.2 = 1|
|**R18.1**|CounselingReceived|I|1.10|Y||
|**R18.A**|IndividualCounseling|I|1.10|Y|Null unless R18.1 = 1|
|**R18.A**|FamilyCounseling|I|1.10|Y|Null unless R18.1 = 1|
|**R18.A**|GroupCounseling|I|1.10|Y|Null unless R18.1 = 1|
|**R18.B**|SessionCountAtExit|I||Y|Null unless R18.1 = 1|
||||||Integer >0|
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**R18.3**|PostExitCounselingPlan|I|1.10|Y||
|---|---|---|---|---|---|
|**R18.2**|SessionsInPlan|I||Y|Integer >0|
|**R19.1**|DestinationSafeClient|I|1.8|Y||
|**R19.2**|DestinationSafeWorker|I|R19.A|Y||
|**R19.3**|PosAdultConnections|I|R19.A|Y||
|**R19.4**|PosPeerConnections|I|R19.A|Y||
|**R19.5**|PosCommunityConnections|I|R19.A|Y||
|**R20.1**|AftercareDate|D||Y|Null unless date is between|
||||||_ExitDate_and_ExitDate_+ 180 days AND|
||||||_AftercareProvided_is not null|
|**R20.2**|AftercareProvided|I|R20.2|Y|Null unless_AftercareDate_is between|
||||||_ExitDate_and_ExitDate_+ 180 days|
|**R20.A**|EmailSocialMedia|I|1.10|Y|Null unless R20.2 = 1|
|**R20.A**|Telephone|I|1.10|Y|Null unless R20.2 = 1|
|**R20.A**|InPersonIndividual|I|1.10|Y|Null unless R20.2 = 1|
|**R20.A**|InPersonGroup|I|1.10|Y|Null unless R20.2 = 1|
|**V9.1**|CMExitReason|I|V9.1|Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|
## **IncomeBenefits.csv**

IncomeBenefits.csv includes data from:

- **4.02 Income and Sources**

- **4.03 Non-Cash Benefits**

- **4.04 Health Insurance**

- **P4 Connection with SOAR**

- **W3 Medical Assistance**

This file may include:

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 1 (entry). The

_InformationDate_ should match the entry date.

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 3 (exit). The

_InformationDate_ should match the exit date.

- Multiple records per _EnrollmentID_ with a _DataCollectionStage_ of 2 (update) or 5 (annual assessment7F[8] ).

Data for individual data elements that share the same data collection stage and information date should be combined into a single record in which:

8 Records for W3 Medical Assistance with a data collection stage of 2 may be combined with records for data elements 4.02, 4.03, and 4.04 with a data collection stage of 5, as long as the information date is the same. The _DataCollectionStage_ for the exported record should be 5.
- _IncomeBenefitsID_ is the lowest value associated with any of the included data elements in the exporting database.

- _DateCreated_ is the earliest _DateCreated_ associated with the included data elements for the given _InformationDate_ and _DataCollectionStage_ .

- _DateUpdated_ is the latest _DateUpdated_ associated with the included data elements for the given _InformationDate_ and _DataCollectionStage_ .

- _UserID_ is the _UserID_ associated with the record with the latest _DateUpdated_ for the included data elements.

- Fields associated with data elements for which there is no data with the same data collection stage and information date are left null.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||IncomeBenefitsID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|*|InformationDate|D||||
|**4.02.2**|IncomeFromAnySource|I|1.8|Y||
|**4.02.18**|TotalMonthlyIncome|M+||Y|Should match aggregation of 4.02.2|
|**4.02.3**|Earned|I|1.7|Y||
|**4.02.A**|EarnedAmount|M+||Y||
|**4.02.4**|Unemployment|I|1.7|Y||
|**4.02.B**|UnemploymentAmount|M+||Y||
|**4.02.5**|SSI|I|1.7|Y||
|**4.02.C**|SSIAmount|M+||Y||
|**4.02.6**|SSDI|I|1.7|Y||
|**4.02.D**|SSDIAmount|M+||Y||
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**4.02.7**|VADisabilityService|I|1.7|Y||
|**4.02.E**|VADisabilityServiceAmount|M+||Y||
|---|---|---|---|---|---|
|**4.02.8**|VADisabilityNonService|I|1.7|Y||
|**4.02.F**|VADisabilityNonServiceAmount|M+||Y||
|**4.02.9**|PrivateDisability|I|1.7|Y||
|**4.02.G**|PrivateDisabilityAmount|M+||Y||
|**4.02.10**|WorkersComp|I|1.7|Y||
|**4.02.H**|WorkersCompAmount|M+||Y||
|**4.02.11**|TANF|I|1.7|Y||
|**4.02.I**|TANFAmount|M+||Y||
|**4.02.12**|GA|I|1.7|Y||
|**4.02.J**|GAAmount|M+||Y||
|**4.02.13**|SocSecRetirement|I|1.7|Y||
|**4.02.K**|SocSecRetirementAmount|M+||Y||
|**4.02.14**|Pension|I|1.7|Y||
|**4.02.L**|PensionAmount|M+||Y||
|**4.02.15**|ChildSupport|I|1.7|Y||
|**4.02.M**|ChildSupportAmount|M+||Y||
|**4.02.16**|Alimony|I|1.7|Y||
|**4.02.N**|AlimonyAmount|M+||Y||
|**4.02.17**|OtherIncomeSource|I|1.7|Y||
|**4.02.O**|OtherIncomeAmount|M+||Y||
|**4.02.P**|OtherIncomeSourceIdentify|S50||Y|Null unless 4.02.17 = 1|
|**4.03.2**|BenefitsFromAnySource|I|1.8|Y||
|**4.03.3**|SNAP|I|1.7|y||
|**4.03.4**|WIC|I|1.7|Y||
|**4.03.5**|TANFChildCare|I|1.7|Y||
|**4.03.6**|TANFTransportation|I|1.7|Y||
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**4.03.7**|OtherTANF|I|1.7|Y||
|**4.03.8**|OtherBenefitsSource|I|1.7|Y||
|**4.03.A**|OtherBenefitsSourceIdentify|S50||Y|Null unless 4.03.8 = 1|
|---|---|---|---|---|---|
|**4.04.2**|InsuranceFromAnySource|I|1.8|Y||
|**4.04.3**|Medicaid|I|1.7|Y||
|**4.04.3A**|NoMedicaidReason|I|4.04.A|Y|Null unless 4.04.3 = 0|
|**4.04.4**|Medicare|I|1.7|Y||
|**4.04.4A**|NoMedicareReason|I|4.04.A|Y|Null unless 4.04.4 = 0|
|**4.04.5**|SCHIP|I|1.7|Y||
|**4.04.5A**|NoSCHIPReason|I|4.04.A|Y|Null unless 4.04.5 = 0|
|**4.04.6**|VHAServices|I|1.7|Y||
|**4.04.6A**|NoVHAReason|I|4.04.A|Y|Null unless 4.04.6 = 0|
|**4.04.7**|EmployerProvided|I|1.7|Y||
|**4.04.7A**|NoEmployerProvidedReason|I|4.04.A|Y|Null unless 4.04.7 = 0|
|**4.04.8**|COBRA|I|1.7|Y||
|**4.04.8A**|NoCOBRAReason|I|4.04.A|Y|Null unless 4.04.8 = 0|
|**4.04.9**|PrivatePay|I|1.7|Y||
|**4.04.9A**|NoPrivatePayReason|I|4.04.A|Y|Null unless 4.04.9 = 0|
|**4.04.10**|StateHealthIns|I|1.7|Y||
|**4.04.10A**|NoStateHealthInsReason|I|4.04.A|Y|Null unless 4.04.10 = 0|
|**4.04.11**|IndianHealthServices|I|1.7|Y||
|**4.04.11A**|NoIndianHealthServicesReason|I|4.04.A|Y|Null unless 4.04.11 = 0|
|**4.04.12**|OtherInsurance|I|1.7|Y||
|**4.04.12A**|OtherInsuranceIdentify|S50||Y|Null unless 4.04.12 = 1|
|**W3.3**|ADAP|I|1.8|Y||
|**W3.B**|NoADAPReason|I|W3|Y|Null unless W3.3 = 0|
|**W3.4**|RyanWhiteMedDent|I|1.8|Y||
|**W3.C**|NoRyanWhiteReason|I|W3|Y|Null unless W3.4 = 0|
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**P4.1**|ConnectionWithSOAR|I|1.8|Y||
||DataCollectionStage|I|5.03.1|||
||DateCreated|T||||
DateUpdated T UserID S32 DateDeleted T Y ExportID S32 Must match _ExportID_ in Export.csv

*InformationDate has multiple data element numbers to which it applies for purposes of this table.

## **HealthAndDV.csv**

HealthAndDV.csv includes data from:

- **4.11 Domestic Violence**

- **R7 General Health Status**

- **R8 Dental Health Status**

- **R9 Mental Health Status**

- **R10 Pregnancy Status**

For each _EnrollmentID_ this file may include:

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 1 (entry). The

_InformationDate_ should match the entry date.

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 3 (exit). The

_InformationDate_ should match the exit date.

- Multiple records per _EnrollmentID_ with a _DataCollectionStage_ of 2 (update).
Data for individual data elements that share the same data collection stage and information date should be combined into a single record in which:

- _HealthAndDVID_ is the lowest value associated with any of the included data elements in the exporting database.

- _DateCreated_ is the earliest _DateCreated_ associated with the included data elements for the given _InformationDate_ and _DataCollectionStage_ .

- _DateUpdated_ should be the latest _DateUpdated_ associated with the included data elements for the given _InformationDate_ and _DataCollectionStage_ .

- _UserID_ should be the _UserID_ associated with the record with the latest _DateUpdated_ for the included data elements.

- Fields associated with data elements for which there is no data with the same data collection stage and information date are left null.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||HealthAndDVID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**4.11.1**|InformationDate|D||||
|**4.11.2**|DomesticViolenceSurvivor|I|1.8|Y||
|**4.11.A**|WhenOccurred|I|4.11.A|Y|Null unless 4.11.2 = 1|
|**4.11.B**|CurrentlyFleeing|I|1.8|Y|Null unless 4.11.2 = 1|
|**R7.1**|GeneralHealthStatus|I|R7.1|Y||
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|**R8.1**|DentalHealthStatus|I|R7.1|Y||
|**R9.1**|MentalHealthStatus|I|R7.1|Y||
|**R10.1**|PregnancyStatus|I|1.8|Y||
|**R10.A**|DueDate|D||Y|Null unless R10.1 = 1|
DataCollectionStage I 5.03.1 DateCreated T DateUpdated T UserID S32 DateDeleted T Y ExportID S32 Must match _ExportID_ in Export.csv

## **EmploymentEducation.csv**

EmploymentEducation.csv includes data from:

- **R4 Last Grade Completed**

- **R5 School Status**

- **R6 Employment Status**

This file may include:

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 1 (entry). The

_InformationDate_ should match the entry date.

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 3 (exit). The

_InformationDate_ should match the exit date.

- Multiple records per _EnrollmentID_ with a _DataCollectionStage_ of 2 (update) or 5 (annual assessment).

Data for individual data elements that share the same data collection stage and information date should be combined into a single record in which:

- _EmploymentEducationID_ is the lowest value associated with any of the included data elements in the exporting database.
- _DateCreated_ is the earliest _DateCreated_ associated with the included data elements for the given _InformationDate_

   - and _DataCollectionStage_ .

- _DateUpdated_ should be the latest _DateUpdated_ associated with the included data elements for the given _InformationDate_ and _DataCollectionStage_ .

- _UserID_ should be the _UserID_ associated with the record with the latest _DateUpdated_ for the included data elements.

- Fields associated with data elements for which there is no data with the same data collection stage and information date are left null.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||EmploymentEducationID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**R6.1**|InformationDate|D||||
|**R4.1**|LastGradeCompleted|I|R4.1|Y||
|**R5.1**|SchoolStatus|I|R5.1|Y||
|**R6.2**|Employed|I|1.8|Y||
|**R6.A**|EmploymentType|I|R6.A|Y|Null unless R6.2 = 1|
|**R6.B**|NotEmployedReason|I|R6.B|Y|Null unless R6.2 = 0|
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
||DataCollectionStage|I|5.03.1|||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match record in Export.csv|
## **Disabilities.csv**

Disabilities.csv includes data from:

- **4.05 Physical Disability** ( _DisabilityType_ 5)

- **4.06 Developmental Disability** ( _DisabilityType_ 6)

- **4.07 Chronic Health Condition** ( _DisabilityType_

- **4.08 HIV/AIDS** ( _DisabilityType_ 8)

- **4.09 Mental Health Disorder** ( _DisabilityType_ 9)

- **4.10 Substance Use Disorder** ( _DisabilityType_ 10)

- **W4 T-Cell (CD4) and Viral Load**

- **W6 Prescribed Anti-Retroviral**

The _DisabilityType_ field is used to identify the data element for each record; values correspond to the second part of the data element number. For example, the _DisabilityType_ for a **4.10 Substance Use** record is 10.

_DisabilitiesID_ is the unique identifier for Disabilities.csv. In the event that data for multiple disabilities share the same unique identifier in the exporting database, append the first letter of the data element name (e.g., ‘P’ for Physical disability) to the identifier in order to ensure that they are unique as required in the exported file.

For each distinct _DisabilityType_ , this file may include:

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 1 (entry). The _InformationDate_ should match the entry date.

- No more than one record per _EnrollmentID_ with a _DataCollectionStage_ of 3 (exit). The

## _InformationDate_ should match the exit date.

- Multiple records per _EnrollmentID_ with a _DataCollectionStage_ of 2 (update) or 5 (annual assessment).
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||DisabilitiesID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
||InformationDate|D||||
||DisabilityType|I|1.3|||
||DisabilityResponse|I|(see note)||For_DisabilityType_|
||||||• 10 (Substance Use Disorder) – list 4.10.2|
||||||Any other – list1.8|
||IndefiniteAndImpairs|I|1.8|Y||
|**W4.2**|TCellCountAvailable|I|1.8|Y|Null unless_DisabilityType_= 8|
||||||AND DisabilityResponse=1|
|**W4.A**|TCellCount|I||Y|Null unless W4.2 = 1|
|**W4.B**|TCellSource|I|W4.B|Y|Null unless W4.A is not null|
|**W4.3**|ViralLoadAvailable|I|W4.3|Y|Null unless_DisabilityType_= 8|
||||||AND DisabilityResponse=1|
|**W4.C**|ViralLoad|I||Y|Null unless W4.3 = 1|
|**W4.D**|ViralLoadSource|I|W4.B|Y|Null unless W4.C is not null|
|**W6.2**|AntiRetroviral|I|1.8|Y|Null unless_DisabilityType_= 8|
||||||AND DisabilityResponse=1|
||DataCollectionStage|I|5.03.1|||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|
## **Services.csv**

Services.csv includes data from:

- **4.14 Bed Night** ( _RecordType_ 200)

- **P1 Services Provided – PATH** ( _RecordType_ 141)

- **P2 Referrals Provided – PATH** ( _RecordType_ 161)

- **R14 RHY Service Connections** ( _RecordType_ 142)

- **W1 Services Provided – HOPWA** ( _RecordType_ 143)

- **W2 Financial Assistance – HOPWA** ( _RecordType_ 151)

- **V2 Services Provided – SSVF** ( _RecordType_ 144)

- **V3 Financial Assistance – SSVF** ( _RecordType_ 152)

- **V8 HUD-VASH Voucher Tracking** ( _RecordType_ 210)8F[9]

- **C2 Moving On Assistance Provided** _(RecordType 300)_

This file may include a theoretically unlimited number of records per _EnrollmentID_ . The _DateProvided_ is considered the information date for all records in this file.

The _RecordType_ field is used to identify the data element for each record; values are in parentheses after each of the data elements listed above. For example, the _RecordType_ for a PATH referral is 161.

_ServicesID_ is the unique identifier for Services.csv. The structure is based on the data elements as they are defined in the HMIS Data Dictionary and assumes that each record in the exporting database includes one service. In the event that data for multiple services share the same unique identifier in the exporting database, the export process must ensure that the value in _ServicesID_ is unique as required in the exported file.

When systems that permit multiple services per record are engaged in ongoing data exchange in which the export directive is ‘Delta,’ the exporting database must ensure that:

- a. Each separate service is associated with the same unique ServicesID every time it is exported; and

> 9 Data element defined in the HMIS Data Dictionary; relevant only in communities exporting HUD-VASH OTHdata from HMIS for upload to the VA Repository.
- b. In the event that a user edits a record to delete one or more (but not all) previously transmitted services associated with the same unique ID in the exporting database, a record will be included in the export that reflects the deletion.

Records of bed nights should only be present for _EnrollmentIDs_ in emergency shelters where 2.02.6 ProjectType = 1 (“Emergency Shelter – Night-by-Night”). For these shelters:

- There should be a record of a bed night with a _DateProvided_ that corresponds to the _EntryDate_

in Enrollment.csv.

- Any record of a bed night should have a _DateProvided_ that is between the _EntryDate_ and the day before the _ExitDate_ (if there is one) for the _EnrollmentID_ in the Services.csv record.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||ServicesID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
||DateProvided|D||||
||RecordType|I|1.4|||
||TypeProvided|I|(see notes)||For_RecordType_|
||||||• 141 – listP1.2|
||||||• 142 – listR14.2|
||||||• 143 – listW1.2|
||||||• 144 – listV2.2|
||||||• 151 – list W2.2|
||||||• 152 – listV3.4|
||||||• 161 – listP2.2|
||||||• 200 – list4.14|
||||||• 210 – list V8.2|
||||||• 300 – listC2.2|
|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
|**V2.D & V8.A**|OtherTypeProvided|S50||Y|Null unless_RecordType_= 144 and|
||||||_TypeProvided_= 6|
||||||Or_RecordType_= 210 and|
||||||_TypeProvided_= 12|
|**C2.A**|MovingOnOtherType|S50||Y|Null unless_RecordType_= 300|
||||||and_TypeProvided_= 5|
|**V2.A**|SubTypeProvided|I|(see note)|Y|Null unless_RecordType_= 144 and|
|**V2.B**|||||_TypeProvided_= 3, 4, or 5.  For|
|**V2.C**|||||_TypeProvided_:|
||||||• 3 – listV2.A|
||||||• 4 – listV2.B|
||||||• 5 – listV2.C|
|**W2 & V3.3**|FAAmount|M||Y|Null unless_RecordType_= 151 or|
||||||152|
|**V3.2**|FAStartDate|D||Y|Null unless_RecordType_= 152|
|**V3.5**|FAEndDate|D||Y|Null unless_RecordType_= 152|
|**P2**|ReferralOutcome|I|P2.A|Y|Null unless_RecordType_= 161|
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in|
||||||Export.csv|
## **CurrentLivingSituation.csv**

CurrentLivingSituation.csv contains data exclusively for element 4.12 which was previously reported as contact events in Services.csv. This element now contains additional information and therefore requires a separate file.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||CurrentLivingSitID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**4.12.1**|InformationDate|D||||
|**4.12.2**|CurrentLivingSituation|I|3.12|||
|**4.12.A**|CLSSubsidyType|I|3.12.A|Y|Null unless_CurrentLivingSItuation_= 435|
|**4.12.3**|VerifiedBy|S200||Y|Null unless_ProjectType_= 14|
|**4.12.B**|LeaveSituation14Days|I|1.8|Y|Null unless_CurrentLivingSituation_in 215, 206, 207, 225, 204, 205, 302, 329, 314, 332, 336, 335, 410, 435, 421, 411|
|**4.12.C**|SubsequentResidence|I|1.8|Y|Null unless_LeaveSituation14Days_= 1|
|**4.12.D**|ResourcesToObtain|I|1.8|Y|Null unless_LeaveSituation14Days_= 1|
|**4.12.E**|LeaseOwn60Day|I|1.8|Y|Null unless_LeaveSituation14Days_= 1|
|**4.12.F**|MovedTwoOrMore|I|1.8|Y|Null unless_LeaveSituation14Days_= 1|
|**4.12.4**|LocationDetails|S250||Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|
## **Assessment.csv**

Assessment.csv contains _part_ of data element 4.19, Coordinated Entry Assessment. Because each assessment has some standard information exported in this file, but also any number of non-standard questions, responses, and results, the latter data are reported separately in AssessmentQuestions.csv and AssessmentResults.csv.  This allows for the number of questions/responses and results to be a variable number, though there must be at least 1 row each in AssessmentQuestions.csv and AssessmentResults.csv for each row in Assessment.csv.

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||AssessmentID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**4.19.1**|AssessmentDate|D||||
|**4.19.2**|AssessmentLocation|S250||Y||
|**4.19.3**|AssessmentType|I|4.19.3|Y||
|**4.19.4**|AssessmentLevel|I|4.19.4|Y||
|**4.19.7**|PrioritizationStatus|I|4.19.7|Y||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|
## **AssessmentQuestions.csv**

For each row in Assessment.csv, there may be 1 or more rows in AssessmentQuestions.csv. If there is at least one row in AssessmentQuestions.csv, there must be at least one “AssessmentQuestion.” There are no standard options for questions or answers, so the fields in this file are primarily text. AssessmentQuestionGroup is optional and can be used to group questions together, e.g. “Housing history” or “Family status”. AssessmentQuestionOrder is also optional and can be used to preserve the sequence of questions. Two parties exchanging CSV data should understand what will be communicated in the file and how it will be stored in the target system.

|**DE#**|**Name**|**Type**|**List**||**Null**|**Notes**|
|---|---|---|---|---|---|---|
||AssessmentQuestionID|S32||||Unique identifier|
||AssessmentID|S32|||||
||EnrollmentID|S32|||||
||PersonalID|S32|||||
||AssessmentQuestionGroup|S250|||Y|Locally determined|
||AssessmentQuestionOrder|I|||Y|Locally determined|
|**4.19.5**|AssessmentQuestion|S250||*||Cannot be NULL if AssessmentQuestions.csv|
|||||||is populated|
|**4.19.A**|AssessmentAnswer|S500||*|Y|Locally determined|
||DateCreated|T|||||
||DateUpdated|T|||||
||UserID|S32|||||
||DateDeleted|T|||Y||
||ExportID|S32||||Must match_ExportID_in Export.csv|


*Will be defined locally as needed
## **AssessmentResults.csv**

For each row in Assessment.csv, there may be 1 or more rows in AssessmentResults.csv. If there is at least one row in AssessmentResults.csv, there must be at least one “AssessmentResultType.” There are no standard options for results, so the field in this file is simply text. Two parties exchanging CSV data should understand what will be communicated in the file and how it will be stored in the target system.

|**DE#**|**Name**|**Type**|**List**||**Null**|**Notes**|
|---|---|---|---|---|---|---|
||AssessmentResultID|S32||||Unique identifier|
||AssessmentID|S32|||||
||EnrollmentID|S32|||||
||PersonalID|S32|||||
|**4.19.6**|AssessmentResultType|S250||*||Cannot be NULL if AssessmentResult.csv is|
|||||||populated|
|**4.19.B**|AssessmentResult|S250||*|Y|Locally determined|
||DateCreated|T|||||
||DateUpdated|T|||||
||UserID|S32|||||
||DateDeleted|T|||Y||
||ExportID|S32||||Must match_ExportID_in Export.csv|


*Will be defined locally as needed
## **Event.csv**

Event.csv contains data exclusively for element 4.20, Coordinated Entry Event

|.**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||EventID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**4.20.1**|EventDate|D||||
|**4.20.2**|Event|I|4.20.2|||
|**4.20.A**|ProbSolDivRRResult|I|1.7|Y||
|**4.20.B**|ReferralCaseManageAfter|I|1.7|Y||
|**4.20.C**|LocationCrisisOrPHHousing|S250||Y||
|**4.20.D**|ReferralResult|I|4.20.D|Y||
|**4.20.E**|ResultDate|D||Y|Null unless_ReferralResult_not null|
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|
## **YouthEducationStatus.csv**

YouthEducationStatus.csv contains data exclusively for element C3, Youth Education Status

|**DE#**|**Name**|**Type**|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||YouthEducationStatusID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
|**C3.1**|InformationDate|D||||
|**C3.2**|CurrentSchoolAttend|I|C3.2|Y||
|**C3.A**|MostRecentEdStatus|I|C3.A|Y|Null unless C3.2 = 0|
|**C3.B**|CurrentEdStatus|I|C3.B|Y|Null unless C3.2 = 1 or C3.2 = 2|
||DataCollectionStage|I|5.03.1|||
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in|
||||||Export.csv|
## **Appendix A –– List of Data Elements and Associated CSV Files**

|**#**||**Data Element Name**|**File Location**||
|---|---|---|---|---|
|2.01|Organization Information||Organization.csv||
|2.02|Project Information||Project.csv, Affiliation.csv,||
|2.03|Continuum of Care|Information|ProjectCoC.csv||
|2.06|Funding Sources||Funder.csv||
|2.07|Bed and Unit Inventory Information||Inventory.csv||
|2.08|HMIS Participation||HMISParticipation.csv||
|2.09|CE Participation||CEParticipation.csv||
|3.01|Name||Client.csv||
|3.02|Social Security Number||Client.csv||
|3.03|Date of Birth||Client.csv||
|3.04|Race and Ethnicity||Client.csv||
|3.07|Veteran Status||Client.csv||
|3.08|Disabling Condition||Enrollment.csv||
|3.10|Project Start Date||Enrollment.csv||
|3.11|Project Exit Date||Exit.csv||
|3.12|Destination||Exit.csv||
|3.15|Relationship to Head of Household||Enrollment.csv||
|3.16|Enrollment CoC||Enrollment.csv||
|3.20|Housing Move-In Date||Enrollment.csv||
|3.917|Prior Living Situation||Enrollment.csv||
|4.02|Income and Sources||IncomeBenefits.csv||
|4.03|Non-Cash Benefits||IncomeBenefits.csv||
|4.04|Health Insurance||IncomeBenefits.csv||
|4.05|Physical Disability||Disabilities.csv||
|4.06|Developmental Disability||Disabilities.csv||
|4.07|Chronic Health Condition||Disabilities.csv||
|4.08|HIV/AIDS||Disabilities.csv||
|4.09|Mental Health Problem||Disabilities.csv||
|4.10|Substance Use Disorder|Disabilities.csv||
|---|---|---|---|
|**#**|**Data Element Name**|**File Location**||
|4.11|Domestic Violence|HealthAndDV.csv||
|4.12|Current Living Situation|CurrentLivingSituation.csv||
|4.13|Date of Engagement|Enrollment.csv||
|4.14|Bed Night Date|Services.csv||
|4.19|Coordinated Entry Assessment|Assessment.csv AssessmentQuestions.csv||
|||AssessmentResults.csv||
|4.20|Coordinated Entry Event|Event.csv||
|4.21|Sex|Client.csv||
|C2|Moving On Assistance Provided|Services.csv||
|C3|Youth Education Status|YouthEducationStatus.csv||
|P1|Services Provided – PATH Funded|Services.csv||
|P2|Referrals Provided – PATH|Services.csv||
|P3|PATH Status|Enrollment.csv||
|P4|Connection with SOAR|IncomeBenefits.csv||
|R1|Referral Source|Enrollment.csv||
|R10|Pregnancy Status|HealthAndDV.csv||
|R11|Formerly a Ward of Child Welfare/Foster Care Agency|Enrollment.csv||
|R12|Formerly a Ward of Juvenile Justice System|Enrollment.csv||
|R13|Family Critical Issues|Enrollment.csv||
|R14|RHY Service Connections|Services.csv||
|R15|Commercial Sexual Exploitation/Sex Trafficking|Exit.csv||
|R16|Labor Exploitation/Trafficking|Exit.csv||
|R17|Project Completion Status|Exit.csv||
|R18|Counseling|Exit.csv||
|R19|Safe and Appropriate Exit|Exit.csv||
|R2|RHY-BCP Status|Enrollment.csv||
|R20|Aftercare Plans|Exit.csv||
|R4|Last Grade Completed|EmploymentEducation.csv||
|R5|School Status|EmploymentEducation.csv||
|R6|Employment Status|EmploymentEducation.csv||
|R7|General Health Status|HealthAndDV.csv||
|R8|Dental Health Status|HealthAndDV.csv||
|R9|Mental Health Status|HealthAndDV.csv||
|**#**|**Data Element Name**|**File Location**||
|---|---|---|---|
|V1|Veteran’s Information|Client.csv||
|V2|Services Provided – SSVF|Services.csv||
|V3|Referrals Provided – SSVF|Services.csv||
|V4|Percent of AMI|Enrollment.csv||
|V6|VAMC Station Code|Enrollment.csv||
|V7|SSVF HP Targeting Criteria|Enrollment.csv||
|V8|HUD-VASH Voucher Tracking|Services.csv||
|V9|HUD-VASH Exit Information|Exit.csv||
|V10|Mental Health Consultation|Enrollment.csv||
|W1|Services Provided – HOPWA|Services.csv||
|W2|Financial Assistance – HOPWA|Services.csv||
|W3|Medical Assistance|IncomeBenefits.csv||
|W4|T-Cell (CD4) and Viral Load|Disabilities.csv||
|W5|Housing Assessment at Exit|Exit.csv||
|W6|Prescribed Anti-Retroviral|Disabilities.csv||
## **Appendix B – Lists**

## **Notes**

These lists are included as a reference for values considered valid in the HMIS CSV and text ‘translations.’ As such, they are presented in order of the numeric export value; the order may differ from that shown in the HMIS Data Dictionary, which shows HUD’s preferred order in an HMIS user interface. Additionally, some values are no longer valid for ongoing collection, such as funding sources that have ended; these lists contain an additional column called “Retired” with X marks by those elements that should no longer be collected. It is expected that the system does not provide these options for selection to end users, but they should continue to be stored in the database as they reflect accurate historical information.

Aside from the order and any retired elements, valid values are intended to match the HMIS Data Dictionary, which is the definitive authority on HMIS data collection requirements. Except for items explicitly outlined in this Notes section and in list W5.A, any difference between the Dictionary values and  the values included here should be resolved in favor of the Dictionary. Discrepancies may be reported via Ask A Question on the HUD Exchange.

The HMIS Data Dictionary explicitly includes a ‘Data not collected’ response for most option list fields. In addition, the HMIS Data Dictionary requires that an HMIS must allow users to record ‘Data not collected’ in any field that forces a user to select a value from a list to be able to “move forward in the system.” Consistent with that requirement, the lists in this document include 99 (Data not collected) as a valid value for some fields defined in the Universal and Program-Specific Data Elements even in cases where it was not specifically included in the HMIS Data Dictionary.

The ‘Data not collected’ option has not been included and is not considered valid in the HMIS CSV in instances where a record would not exist in the absence of a valid response.

- For example, the list of PATH Services in list 4.14A does not include a ‘Data not collected’ response because a record of a service that does not identify the service is meaningless.

### 1.1 ExportPeriodType
|**Value**|**Text**|
|---|---|
|**1**|Updated|
|**3**|Reporting period|
|**4**|Other|


### 1.2 ExportDirective
|**Value**|**Text**|
|---|---|
|**1**|Delta refresh|
|**2**|Full refresh|
|**3**|Other|
### 1.3 DisabilityType
|**Value**|**Text**|
|---|---|
|**5**|Physical disability|
|**6**|Developmental disability|
|**7**|Chronic health condition|
|**8**|HIV/AIDS|
|**9**|Mental health disorder|
|**10**|Substance use disorder|


_1.4 RecordType_

|**Value**|**Text**|**Text**|**Corresponding DE#**|
|---|---|---|---|
|**141**|PATH service||P1|
|**142**|RHY service connections||R14|
|**143**|HOPWA service||W1|
|**144**|SSVF service||V2|
|**151**|HOPWA financial assistance||W2|
|**152**|SSVF financial assistance||V3|
|**161**|PATH referral||P2|
|**200**|Bed night||4.14|
|**210**|HUD-VASH OTH voucher tracking||V8|
|**300**|Moving On assistance provided||C2|
|_1.5_|_HashStatus_|||
|**Value**||**Text**||
|**1**||Unhashed||
|**2**||SHA-1 (no longer used for federal|purposes)|
|**3**||Hashed – other||
|**4**||SHA-256||
|_1.6_|_RaceNone_|||
|**Value**||**Text**||
|**8**||Client doesn’t know||
|**9**||Client prefers not to answer||
|**99**||Data not collected||
|_1.7_|_No/Yes/Missing_|||
|**Value**||**Text**||
|**0**||No||
|**1**||Yes||
|**99**||Data not collected||
_1.8_

_No/Yes/Reasons for Missing Data_

|**Value**|**Text**|
|---|---|
|**0**|No|
|**1**|Yes|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


_1.9 SourceType_

|**Value**|**Text**|
|---|---|
|**1**|CoC HMIS|
|**2**|Standalone/agency-specific application|
|**3**|Data warehouse|
|**4**|Other|
|_1.10_ _No/Yes_||
|**Value**|**Text**|
|**0**|No|
|**1**|Yes|


### 2.02.6 ProjectType
|**Value**|**Text**|
|---|---|
|**0**|Emergency Shelter – Entry Exit|
|**1**|Emergency Shelter – Night-by-Night|
|**2**|Transitional Housing|
|**3**|PH – Permanent Supportive Housing|
|**4**|Street Outreach|
|**6**|Services Only|
|**7**|Other|
|**8**|Safe Haven|
|**9**|PH – Housing Only|
|**10**|PH – Housing with Services (no disability required for entry)|
|**11**|Day Shelter|
|**12**|Homelessness Prevention|
|**13**|PH – Rapid Re-Housing|
|**14**|Coordinated Entry|


### 2.02.A   RRHSubType
**Value Text 1** RRH: Services Only **2** RRH: Housing with or without services

### 2.02.D  HousingType
**Value Text**
**1** Site-based – single site **2** Site-based – clustered / multiple sites **3** Tenant-based – scattered site

### 2.06.1  FundingSource
|**Value**|**Text**|**Retired**|
|---|---|---|
|**1**|HUD: CoC – Homelessness Prevention (High Performing Comm. Only)||
|**2**|HUD: CoC – Permanent Supportive Housing||
|**3**|HUD: CoC – Rapid Re-Housing||
|**4**|HUD: CoC – Supportive Services Only||
|**5**|HUD: CoC – Transitional Housing||
|**6**|HUD: CoC – Safe Haven||
|**7**|HUD: CoC – Single Room Occupancy (SRO)||
|**8**|HUD: ESG – Emergency Shelter (operating and/or essential services)||
|**9**|HUD: ESG – Homelessness Prevention||
|**10**|HUD: ESG – Rapid Rehousing||
|**11**|HUD: ESG – Street Outreach||
|**13**|HUD: HOPWA – Hotel/Motel Vouchers||
|**14**|HUD: HOPWA – Housing Information||
|**15**|HUD: HOPWA – Permanent Housing (facility based or TBRA)||
|**16**|HUD: HOPWA – Permanent Housing Placement||
|**17**|HUD: HOPWA – Short-Term Rent, Mortgage, Utility assistance||
|**18**|HUD: HOPWA – Short-Term Supportive Facility||
|**19**|HUD: HOPWA – Transitional Housing (facility based or TBRA)||
|**20**|HUD: HUD/VASH||
|**21**|HHS: PATH – Street Outreach & Supportive Services Only||
|**22**|HHS: RHY – Basic Center Program (prevention and shelter)||
|**23**|HHS: RHY – Maternity Group Home for Pregnant and Parenting Youth||
|**24**|HHS: RHY – Transitional Living Program||
|**25**|HHS: RHY – Street Outreach Project||
|**26**|HHS: RHY – Demonstration Project||
|**27**|VA: CRS Contract Residential Services||
|**30**|VA: Community Contract Safe Haven Program||
|**33**|VA: Supportive Services for Veteran Families||
|**34**|N/A||
|**35**|HUD: Pay for Success||
|**36**|HUD: Public and Indian Housing (PIH) Programs||
|**37**|VA: Grant Per Diem – Bridge Housing||
|**38**|VA: Grant Per Diem – Low Demand||
|**39**|VA: Grant Per Diem – Hospital to Housing||
|**40**|VA: Grant Per Diem – Clinical Treatment||
|**41**|VA: Grant Per Diem – Service Intensive Transitional Housing||
|**42**|VA: Grant Per Diem – Transition in Place||
|**43**|HUD: CoC – Youth Homeless Demonstration Program (YHDP)||
|**44**|HUD: CoC – Joint Component TH/RRH||
|**45**|VA: Grant Per Diem – Case Management/Housing Retention||
|---|---|---|
|**46**|Local or Other Funding Source (Please Specify)||
|**47**|HUD: ESG – CV|X|
|**48**|HUD: HOPWA – CV|X|
|**50**|HUD: HOME||
|**51**|HUD: HOME (ARP)||
|**52**|HUD: PIH (Emergency Housing Voucher)||
|**53**|HUD: ESG – RUSH||
|**54**|HUD: Unsheltered Special NOFO||
|**55**|HUD: Rural Special NOFO||
|**56**|HUD: CoC Builds||


### 2.07.4 HouseholdType
**Value Text 1** Households without children **3** Households with at least one adult and one child **4** Households with only children

### 2.07.5 BedType
|**Value**|**Text**|
|---|---|
|**1**|Facility-based beds|
|**2**|Voucher beds|
|**3**|Other beds|


### 2.07.6 Availability
**Value Text 1** Year-round **2** Seasonal **3** Overflow

### 2.02.7 TargetPopulation
**Value Text 1** DV: Survivor of Domestic Violence **3** HIV: Persons with HIV/AIDS **4** NA: Not applicable

### 2.02.8 HOPWAMedAssistedLivingFac
**Value Text 0** No **1** Yes **2** Non-HOPWA Funded Project

### 2.03.4 GeographyType
**Value Text**
**1** Urban **2** Suburban **3** Rural **99** Unknown / data not collected

### 2.08.1   HMISParticipationType
|**Value**|**Text**|
|---|---|
|**0**|Not Participating|
|**1**|HMIS Participating|
|**2**|Comparable Database Participating|


### 3.01.5   NameDataQuality
|**Value**|**Text**|
|---|---|
|**1**|Full name reported|
|**2**|Partial, street name, or code name reported|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


### 3.02.2  SSNDataQuality
|**Value**|**Text**|
|---|---|
|**1**|Full SSN reported|
|**2**|Approximate or partial SSN reported|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


### 3.03.2  DOBDataQuality
|**Value**|**Text**|
|---|---|
|**1**|Full DOB reported|
|**2**|Approximate or partial DOB reported|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|
### 3.12.1   Living Situation Option List
This common option list is used by elements 3.12, 3.917, and 4.12. The columns at the right indicate which options are applicable to each element. Beige header rows do not indicate selectable values; they are only provided here for context.

|**Value**|||||
|---|---|---|---|---|
|||**Prior Living** |**Current Living** |**Destination** |
||**Text**||||
||| **Situation (3.917)**| **Situation (4.12)**|**(3.12)**|
||||||
|**Header**|**Homeless Situations(100-199)**||||
|**116**|Place not meant for habitation (e.g., a vehicle, an abandoned building, bus/train/subway station/airport or anywhere outside)|X|X|X|
|**101**| Emergency shelter, including hotel or motel paid for with emergency shelter voucher, Host Home shelter|X|X|X|
|**118**|Safe Haven|X|X|X|
|**Header**|**Institutional Situations(200-299)**||||
|**215**|Foster care home or foster caregrouphome|X|X|X|
|**206**|Hospital or other residential non-psychiatric medical facility|X|X|X|
|**207**|Jail, prison,orjuvenile detention facility|X|X|X|
|**225**|Long-term care facilityor nursinghome|X|X|X|
|**204**|Psychiatric hospital or otherpsychiatric facility|X|X|X|
|**205**|Substance abuse treatment facilityor detox center|X|X|X|
|**Header**|**Temporary Housing Situations(300-399)**||||
|**302**|Transitional housingfor homelesspersons(includinghomelessyouth)|X|X|X|
|**329**|Residentialproject or halfwayhouse with no homeless criteria|X|X|X|
|**314**|Hotel or motelpaid for without emergencyshelter voucher|X|X|X|
|**332**|Host Home(non-crisis)|X|X|X|
|**312**|Staying or living with family, temporary tenure (e.g. room, apartment, or house)|||X|
|**313**|Staying or living with friends, temporary tenure (e.g. room, apartment, or house)|||X|
|**327**|Moved from one HOPWA fundedproject to HOPWA TH|||X|
|**336**|Stayingor livingin a friend’s room,apartment,or house|X|X||
|**335**|Staying or living in a family member’s room, apartment, or house|X|X||
|**Header**|**Permanent Housing Situation(400 -499)**||||
|**422**|Stayingor livingwith family,permanent tenure|||X|
|||||||
|---|---|---|---|---|---|
||**Value**||**Prior Living** **Situation** **(3.917)**|**Current Living** **Situation** **(4.12)**|**Destination** **(3.12)**|
|||**Text**||||
|||||||
||**423**|Stayingor livingwith friends, permanent tenure|||X|
||**426**|Moved from one HOPWA fundedproject to HOPWA PH|||X|
||**410**|Rental byclient,no ongoinghousingsubsidy|X|X|X|
||**435**|Rental byclient,with ongoinghousingsubsidy|X|X|X|
||**421**|Owned byclient, with ongoinghousingsubsidy|X|X|X|
||**411**|Owned byclient, no ongoinghousingsubsidy|X|X|X|
||**Header**|**Other(1-99)**||||
||**30**|No exit interview completed|||X|
||**17**|Other||X|X|
||**24**|Deceased|||X|
||**37**|Worker unable to determine||X||
||**8**|Client doesn’t know|X|X|X|
||**9**|Clientprefers not to answer|X|X|X|
||**99**|Data not collected|X|X|X|


### 3.12.A   RentalSubsidyTypes
|**Value**|**Text**|
|---|---|
|**428**|GPD TIP housing subsidy|
|**419**|VASH housing subsidy|
|**431**|RRH or equivalent subsidy|
|**433**|HCV voucher (tenant or project based) (not dedicated)|
|**434**|Public housing unit|
|**420**|Rental by client, with other ongoing housing subsidy|
|**436**|Housing Stability Voucher|
|**437**|Family Unification Program Voucher (FUP)|
|**438**|Foster Youth to Independence Initiative (FYI)|
|**439**|Permanent Supportive Housing|
|**440**|Other permanent housing dedicated for formerly homeless persons|
### 3.15.1   RelationshipToHoH
|**Value**|**Text**|
|---|---|
|**1**|Self (Head of Household)|
|**2**|Head of household’s child|
|**3**|Head of household’s spouse or partner|
|**4**|Head of household’s other relation member|
|**5**|Other: non-relation member|
|**99**|Data not collected|


### 3.917.2  LengthOfStay
|**Value**|**Text**|
|---|---|
|**2**|One week or more, but less than one month|
|**3**|One month or more, but less than 90 days|
|**4**|90 days or more but less than one year|
|**5**|One year or longer|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**10**|One night or less|
|**11**|Two to six nights|
|**99**|Data not collected|


### 3.917.4 TimesHomelessPastThreeYears
|**Value**|**Text**|
|---|---|
|**1**|One time|
|**2**|Two times|
|**3**|Three times|
|**4**|Four or more times|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


### 3.917.5 MonthsHomelessPastThreeYears
|**Value**|**Text**|
|---|---|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|
|**101**|1|
|**102**|2|
|**103**|3|
|**104**|4|
|**105**|5|
|**106**|6|
|**Value**|**Text**|
|**107**|7|
|**108**|8|||
|---|---|---|---|
|**109**|9|||
|**110**|10|||
|**111**|11|||
|**112**|12|||
|**113**|More than|12|months|


### 4.04.A    ReasonNotInsured
|**Value**|**Text**|
|---|---|
|**1**|Applied; decision pending|
|**2**|Applied; client not eligible|
|**3**|Client did not apply|
|**4**|Insurance type n/a for this client|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


### 4.10.2   DisabilityResponse
Used in Disabilities.csv if _DisabilityType_ = 10 (Substance Use).

|**Value**|**Text**|
|---|---|
|**0**|No|
|**1**|Alcohol use disorder|
|**2**|Drug use disorder|
|**3**|Both alcohol and drug use disorders|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


### 4.11.A   WhenDVOccurred
|**Value**|**Text**|
|---|---|
|**1**|Within the past three months|
|**2**|Three to six months ago (excluding six months exactly)|
|**3**|Six months to one year ago (excluding one year exactly)|
|**4**|One year or more|
|**8**|Client doesn’t know|
|**9**|Client prefers not to answer|
|**99**|Data not collected|


### 4.14  BedNight
|**Value**|**Text**|
|---|---|
|**200**|BedNight|
### 4.19.3 AssessmentType
|**Value**|**Text**|
|---|---|
|**1**|Phone|
|**2**|Virtual|
|**3**|In Person|


### 4.19.4 AssessmentLevel
|**Value**|**Text**|
|---|---|
|**1**|Crisis Needs Assessment|
|**2**|HousingNeeds Assessment|


### 4.19.7  PrioritizationStatus
|**Value**|**Text**|
|---|---|
|**1**|Placed onprioritization list|
|**2**|Notplaced onprioritization list|


### 4.20.2  Event
|**Value**|**Text**|
|---|---|
|**1**|Referral to Prevention Assistanceproject|
|**2**|Problem Solving/Diversion/Rapid Resolution intervention or service|
|**3**|Referral to scheduled Coordinated EntryCrisis Needs Assessment|
|**4**|Referral to scheduled Coordinated EntryHousingNeeds Assessment|
|**5**|Referral to Post-placement/follow-upcase management|
|**6**|Referral to Street Outreachproject or services|
|**7**|Referral to HousingNavigationproject or services|
|**8**|Referral to Non-continuum services: Ineligible for continuum services|
|**9**|Referral to Non-continuum services: No availabilityin continuum services|
|**10**|Referral to EmergencyShelter bed opening|
|**11**|Referral to Transitional Housingbed/unit opening|
|**12**|Referral to Joint TH-RRHproject/unit/resource opening|
|**13**|Referral to RRHproject resource opening|
|**14**|Referral to PSHproject resource opening|
|**15**|Referral to Other PHproject/unit/resource opening|
|**16**|Referral to emergencyassistance/flex fund/furniture assistance|
|**18**|Referral to a HousingStabilityVoucher|


### 4.20.D  ReferralResult
|**Value**|**Text**|
|---|---|
|**1**|Successful referral: client accepted|
|**2**|Unsuccessful referral: client rejected|
|**3**|Unsuccessful referral:provider rejected|
|_4.21     Sex_||
|**Value** **Text**||
|**0** Female||
**1** Male **8** Client doesn’t know **9** Client prefers not to answer **99** Data not collected

### 5.03.1  DataCollectionStage
|**Value**|**Text**|
|---|---|
|**1**|Project entry|
|**2**|Update|
|**3**|Project exit|
|**5**|Annual assessment|
|**6**|Post-exit (not used in CSV)|


### P1.2 PATHServices
Used in Services.csv when RecordType = 141 (PATH service).

|**Value**|**Text**|
|---|---|
|**1**|Re-engagement|
|**2**|Screening|
|**3**|Habilitation/rehabilitation|
|**4**|Communitymental health|
|**5**|Substance use treatment|
|**6**|Case management|
|**7**|Residential supportive services|
|**8**|Housingminor renovation|
|**9**|Housingmovingassistance|
|**10**|Housingeligibilitydetermination|
|**11**|Securitydeposits|
|**12**|One-time rent for evictionprevention|
|**14**|Clinical assessment|


### P2.2    PATHReferral
Used in Services.csv when RecordType = 161 (PATH referral).

|**Value**|**Text**|
|---|---|
|**1**|Communitymental health|
|**2**|Substance use treatment|
|**3**|Primaryhealth/dental care|
|**4**|Job training|
|**5**|Educational services|
|**6**|Housingservices|
|**7**|Permanent housing|
|**8**|Income assistance|
|**9**|Employment assistance|
|**10**|Medical insurance|
|**11**|Temporaryhousing|
### P2.A   PATHReferralOutcome
|**Value**|**Text**|
|---|---|
|**1**|Attained|
|**2**|Not attained|
|**3**|Unknown|


### P3.A   ReasonNotEnrolled
|**Value**|**Text**|
|---|---|
|**1**|Client was found ineligible for PATH|
|**2**|Client was not enrolled for other reason(s)|
|**3**|Unable to locate client|


### R1.1    ReferralSource
|**Value**|**Text**|
|---|---|
|**1**|Self-Referral|
|**2**|Individual: Parent/Guardian/Relative/Friend/Foster Parent/Other Individual|
|**7**|Outreach Project|
|**11**|TemporaryShelter|
|**18**|Residential Project|
|**28**|Hotline|
|**30**|Child Welfare/CPS|
|**34**|Juvenile Justice|
|**35**|Law Enforcement/Police|
|**37**|Mental Hospital|
|**38**|School|
|**39**|Other Organization|
|**8**|Client doesn’t know|
|**9**|Client Prefers Not to Answer|
|**99**|Data not collected|


### R2.A  ReasonNoServices
|**Value**|**Text**|
|---|---|
|**1**|Out of age range|
|**2**|Ward of the state|
|**3**|Ward of the criminal justice system|
|**4**|Other|
|**99**|Data not collected|


### R4.1 LastGradeCompleted
|**Value**|**Text**|
|---|---|
|**1**|Less thangrade 5|
|**2**|Grades 5-6|
|**3**|Grades 7-8|
|**4**|Grades 9-11|
||||
|---|---|---|
||**5**|Grade 12|
||**6**|Schoolprogram does not havegrade levels|
||**7**|GED|
||**8**|Client doesn’t know|
||**9**|Clientprefers not to answer|
||**10**|Some college|
||**11**|Associate’s degree|
||**12**|Bachelor’s degree|
||**13**|Graduate degree|
||**14**|Vocational certification|
||**99**|Data not collected|


### R5.1 SchoolStatus
|**Value**|**Text**|
|---|---|
|**1**|Attendingschool regularly|
|**2**|Attendingschool irregularly|
|**3**|Graduated from high school|
|**4**|Obtained GED|
|**5**|Dropped out|
|**6**|Suspended|
|**7**|Expelled|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|


### R6.A   EmploymentType
|**Value**|**Text**|
|---|---|
|**1**|Full-time|
|**2**|Part-time|
|**3**|Seasonal/sporadic(includingdaylabor)|
|**99**|Data not collected|


### R6.B   NotEmployedReason
|**Value**|**Text**|
|---|---|
|**1**|Lookingfor work|
|**2**|Unable to work|
|**3**|Not lookingfor work|
|**99**|Data not collected|


### R7.1    HealthStatus
|**Value**|**Text**|
|---|---|
|**1**|Excellent|
|**2**|Very good|
|**3**|Good|
|**4**|Fair|
|**5**|Poor|
||||
|---|---|---|
||**8**|Client doesn’t know|
||**9**|Clientprefers not to answer|
||**99**|Data not collected|


### R11.A  RHYNumberofYears
|**Value**|**Text**|
|---|---|
|**1**|Less than oneyear|
|**2**|1 to 2years|
|**3**|3 to 5 or moreyears|


### R14.2 RHYServices
Used in Services.csv when RecordType = 142 (RHY service).

|**Value**|**Text**|
|---|---|
|**2**|Communityservice/service learning (CSL)|
|**5**|Education|
|**6**|Employment and/or trainingservices|
|**7**|Criminaljustice/legal services|
|**8**|Life skills training|
|**10**|Parentingeducation foryouth with children|
|**12**|Post-natal care for client(person whogave birth)|
|**13**|Pre-natal care|
|**14**|Health/medical care|
|**17**|Substance use disorder treatment|
|**18**|Substance use disorder Ed/Prevention Services|
|**Value**|**Text**|
|**26**|Home-based Services|
|**27**|Post-natal newborn care(wellness exams;immunizations)|
|**28**|STD Testing|
|**29**|Street-based Services|


### R15.B CountExchangeForSex
|**Value**|**Text**|
|---|---|
|**1**|1-3|
|**2**|4-7|
|**3**|8-11|
|**4**|12 or more|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|


### R17.1 ProjectCompletionStatus
|**Value**|**Text**|
|---|---|
|**1**|Completedproject|
|**2**|Client voluntarilyleft early|
|**3**|Client was expelled or otherwise involuntarilydischarged fromproject|
### R17.A ExpelledReason
|**Value**|**Text**|
|---|---|
|**1**|Criminal activity/destruction ofproperty/violence|
|**2**|Non-compliance withproject rules|
|**3**|Non-payment of rent/occupancycharge|
|**4**|Reached maximum time allowed by project|
|**5**|Project terminated|
|**6**|Unknown/disappeared|


### R19.A WorkerResponse
|**Value**|**Text**|
|---|---|
|**0**|No|
|**1**|Yes|
|**2**|Worker does not know|


### R20.2 AftercareProvided
|**Value**|**Text**|
|---|---|
|**0**|No|
|**1**|Yes|
|**9**|Clientprefers not to answer|


### V1.11 MilitaryBranch
|**Value**|**Text**|
|---|---|
|**1**|Army|
|**2**|Air Force|
|**3**|Navy|
|**4**|Marines|
|**6**|Coast Guard|
|**7**|Space Force|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|


### V1.12 DischargeStatus
|**Value**|**Text**|
|---|---|
|**1**|Honorable|
|**2**|General under honorable conditions|
|**4**|Bad conduct|
|**5**|Dishonorable|
|**6**|Under other than honorable conditions(OTH)|
|**7**|Uncharacterized|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|
### V2.2 SSVFServices
Used in Services.csv when RecordType = 144 (SSVF service)

|**Value**|**Text**|
|---|---|
|**1**|Outreach services|
|**2**|Case management services|
|**3**|Assistance obtainingVA benefits|
|**4**|Assistance obtaining/coordinatingotherpublic benefits|
|**5**|Directprovision of otherpublic benefits|
|**6**|Other(non-TFA)supportive service approved byVA|
|**7**|Shallow Subsidy|
|**8**|ReturningHome|
|**9**|Rapid Resolution|
|**10**|Healthcare navigation|


### V2.A   SSVFSubType3
Used in Services.csv when RecordType = 144 (SSVF service) and TypeProvided = 3 (Assistance obtaining VA benefits).

|**Value**|**Text**|
|---|---|
|**1**|VA vocational and rehabilitation counseling|
|**2**|Employment and trainingservices|
|**3**|Educational assistance|
|**4**|Health care services|


### V2.B   SSVFSubType4
Used in Services.csv when RecordType = 144 (SSVF service) and TypeProvided = 4 (Assistance obtaining/coordinating other public benefits).

|**Value**|**Text**|
|---|---|
|**1**|Health care services|
|**2**|Dailylivingservices|
|**3**|Personal financialplanningservices|
|**4**|Transportation services|
|**5**|Income support services|
|**6**|Fiduciaryand representativepayee services|
|**7**|Legal services - child support|
|**8**|Legal services - evictionprevention|
|**9**|Legal services - outstandingfines andpenalties|
|**10**|Legal services - restore/acquire driver’s license|
|**11**|Legal services – other|
|**12**|Child care|
|**13**|Housingcounseling|


### V2.C   SSVFSubType5
Used in Services.csv when RecordType = 144 (SSVF service) and TypeProvided = 5.

**Value Text**
||||
|---|---|---|
||**1**|Personal financialplanningservices|
||**2**|Transportation services|
||**3**|Income support services|
||**4**|Fiduciaryand representativepayee services|
||**5**|Legal services - child support|
||**6**|Legal services - evictionprevention|
||**7**|Legal services - outstandingfines andpenalties|
||**8**|Legal services - restore/acquire driver’s license|
||**9**|Legal services – other|
||**10**|Child care|
||**11**|Housingcounseling|


### V3.4   SSVFFinancialAssistance
Used in Services.csv when RecordType = 152 (SSVF financial assistance).

|**Value**|**Text**|
|---|---|
|**1**|Rental assistance|
|**2**|Securitydeposit|
|**3**|Utilitydeposit|
|**4**|Utilityfeepayment assistance|
|**5**|Movingcosts|
|**8**|Transportation services: tokens/vouchers|
|**9**|Transportation services: vehicle repair/maintenance|
|**10**|Child care|
|**12**|General housingstabilityassistance|
|**14**|Emergencyhousingassistance|
|**15**|Shallow Subsidy–Financial Assistance|
|**16**|Food assistance|
|**17**|Landlord Incentive|
|**18**|Tenant Incentive|


### V4.1   PercentAMI
|**Value**|**Text**|
|---|---|
|**1**|30% or less|
|**2**|31% to 50%|
|**3**|51% to 80%|
|**4**|81% orgreater|
|**99**|Data not collected|


### V6.1 VAMCStationNumber
Note: This is the only list of response categories in the HMIS CSV with non-integer values

|**Value (Site Code)**|**Text (Site Code / Facility Name)**|
|---|---|
|**402**|(402)Togus, ME|
|**405**|(405) White River Junction, VT|
|**436**|(436) Montana HCS|
|**437**|(437) Fargo, ND|
|**438**|(438)Sioux Falls, SD|
|---|---|
|**442**|(442) Cheyenne, WY|
|**459**|(459) Honolulu, HI|
|**460**|(460) Wilmington, DE|
|**463**|(463) Anchorage, AK|
|**501**|(501) New Mexico HCS|
|**502**|(502)Alexandria, LA|
|**503**|(503) Altoona, PA|
|**504**|(504) Amarillo, TX|
|**506**|(506) Ann Arbor, MI|
|**Value (Site Code)**|**Text (Site Code / Facility Name)**|
|**508**|(508) Atlanta, GA|
|**509**|(509) Augusta, GA|
|**512**|(512)Baltimore HCS, MD|
|**515**|(515) Battle Creek, MI|
|**516**|(516) BayPines, FL|
|**517**|(517) Beckley, WV|
|**518**|(518) Bedford, MA|
|**519**|(519) BigSpring, TX|
|**520**|(520) Gulf Coast HCS, MS|
|**521**|(521) Birmingham, AL|
|**523**|(523) VA Boston HCS, MA|
|**526**|(526) Bronx, NY|
|**528**|(528) Western New York, NY|
|**529**|(529) Butler, PA|
|**531**|(531) Boise, ID|
|**534**|(534) Charleston, SC|
|**537**|(537) Jesse Brown VAMC (Chicago), IL|
|**538**|(538) Chillicothe, OH|
|**539**|(539) Cincinnati, OH|
|**540**|(540) Clarksburg, WV|
|**541**|(541) Cleveland, OH|
|**542**|(542) Coatesville, PA|
|**544**|(544) Columbia, SC|
|**546**|(546) Miami, FL|
|**548**|(548) West Palm Beach, FL|
|**549**|(549) Dallas, TX|
|**550**|(550) Danville, IL|
|**552**|(552) Dayton, OH|
|**553**|(553) Detroit, MI|
|**554**|(554) Denver, CO|
|**556**|(556) Captain James A Lovell FHCC|
|**557**|(557) Dublin, GA|
||||
|---|---|---|
||**558**|(558) Durham, NC|
||**561**|(561) New JerseyHCS, NJ|
||**562**|(562) Erie, PA|
||**564**|(564) Fayetteville, AR|
||**565**|(565) Fayetteville, NC|
||**568**|(568) Black Hills HCS, SD|
||**570**|(570) Fresno, CA|
||**573**|(573) Gainesville, FL|
||**575**|(575) Grand Junction, CO|
||**578**|(578) Hines, IL|
||**Value (Site Code)**|**Text (Site Code / Facility Name)**|
||**580**|(580) Houston, TX|
||**581**|(581) Huntington, WV|
||**583**|(583) Indianapolis, IN|
||**585**|(585) Iron Mountain, MI|
||**586**|(586) Jackson, MS|
||**589**|(589) Kansas City, MO|
||**590**|(590) Hampton, VA|
||**593**|(593) Las Vegas, NV|
||**595**|(595) Lebanon, PA|
||**596**|(596) Lexington, KY|
||**598**|(598) Little Rock, AR|
||**600**|(600) LongBeach, CA|
||**603**|(603) Louisville, KY|
||**605**|(605) Loma Linda, CA|
||**607**|(607) Madison, WI|
||**608**|(608) Manchester, NH|
||**610**|(610) Northern Indiana HCS, IN|
||**612**|(612) N. California, CA|
||**613**|(613) Martinsburg, WV|
||**614**|(614) Memphis, TN|
||**618**|(618) Minneapolis, MN|
||**619**|(619) Central Alabama Veterans HCS, AL|
||**620**|(620) VA Hudson ValleyHCS, NY|
||**621**|(621) Mountain Home, TN|
||**623**|(623) Muskogee, OK|
||**626**|(626) Middle Tennessee HCS, TN|
||**629**|(629) New Orleans, LA|
||**630**|(630) New York Harbor HCS, NY|
||**631**|(631) VA Central Western Massachusetts HCS|
||**632**|(632) Northport, NY|
||**635**|(635) Oklahoma City, OK|
||**636**|(636) Nebraska-W Iowa, NE|
||||
|---|---|---|
||**637**|(637) Asheville, NC|
||**640**|(640) Palo Alto, CA|
||**642**|(642) Philadelphia, PA|
||**644**|(644) Phoenix, AZ|
||**646**|(646) Pittsburgh, PA|
||**648**|(648) Portland, OR|
||**649**|(649) Northern Arizona HCS|
||**650**|(650) Providence, RI|
||**652**|(652) Richmond, VA|
||**653**|(653) Roseburg, OR|
||**Value (Site Code)**|**Text (Site Code / Facility Name)**|
||**654**|(654) Reno, NV|
||**655**|(655) Saginaw, MI|
||**656**|(656) St. Cloud, MN|
||**657**|(657) St. Louis, MO|
||**658**|(658) Salem, VA|
||**659**|(659) Salisbury, NC|
||**660**|(660) Salt Lake City, UT|
||**662**|(662) San Francisco, CA|
||**663**|(663) VA Puget Sound, WA|
||**664**|(664) San Diego, CA|
||**666**|(666) Sheridan, WY|
||**667**|(667) Shreveport, LA|
||**668**|(668) Spokane, WA|
||**671**|(671) San Antonio, TX|
||**672**|(672) San Juan, PR|
||**673**|(673) Tampa, FL|
||**674**|(674) Temple, TX|
||**675**|(675) Orlando, FL|
||**676**|(676) Tomah, WI|
||**678**|(678) Southern Arizona HCS|
||**679**|(679) Tuscaloosa, AL|
||**687**|(687) Walla Walla, WA|
||**688**|(688) Washington, DC|
||**689**|(689) VA Connecticut HCS, CT|
||**691**|(691) Greater Los Angeles HCS|
||**692**|(692) White City, OR|
||**693**|(693) Wilkes-Barre, PA|
||**695**|(695) Milwaukee, WI|
||**740**|(740) VA Texas ValleyCoastal Bend HCS|
||**756**|(756) El Paso, TX|
||**757**|(757) Columbus, OH|
||**459GE**|(459GE) Guam|
||||
|---|---|---|
||**528A5**|(528A5) Canandaigua, NY|
||**528A6**|(528A6) Bath, NY|
||**528A7**|(528A7) Syracuse, NY|
||**528A8**|(528A8) Albany, NY|
||**589A4**|(589A4) Columbia, MO|
||**589A5**|(589A5) Kansas City, MO|
||**589A6**|(589A6) Eastern KS HCS, KS|
||**589A7**|(589A7) Wichita, KS|
||**636A6**|(636A6) Central Iowa, IA|
||**636A8**|(636A8) Iowa City, IA|
||**Value (Site Code)**|**Text (Site Code / Facility Name)**|
||**657A4**|(657A4) Poplar Bluff, MO|
||**657A5**|(657A5) Marion, IL|
||**99**|Data not collected|


### V7.A TimeToHousingLoss
|**Value**|**Text**|
|---|---|
|**0**|1-6 days|
|**1**|7-13 days|
|**2**|14-21 days|
|**3**|More than 21 days|
|**99**|Data not collected|


### V7.B AnnualPercentAMI
|**Value**|**Text**|
|---|---|
|**0**|$0(i.e.,not employed,not receivingcash benefits,no other current income)|
|**1**|1-14% of Area Median Income(AMI)for household size|
|**2**|15-30% of AMI for household size|
|**3**|More than 30% of AMI for household size|
|**99**|Data not collected|


### V7.G  EvictionHistory
|**Value**|**Text**|
|---|---|
|**0**|Noprior rental evictions|
|**1**|1prior rental eviction|
|**2**|2 or moreprior rental evictions|
|**99**|Data not collected|


### V7.C LiteralHomelessHistory
|**Value**|**Text**|
|---|---|
|**0**|Most recent episode occurred in the lastyear|
|**1**|Most recent episode occurred more than oneyear ago|
|**2**|None|
|**99**|Data not collected|
### V7.I    IncarceratedAdult
|**Value**|**Text**|
|---|---|
|**0**|Not incarcerated|
|**1**|Incarcerated once|
|**2**|Incarcerated two or more times|
|**99**|Data not collected|


### V7.O    DependentUnder6
|**Value**|**Text**|
|---|---|
|**0**|No|
|**1**|Youngest child is under 1year old|
|**2**|Youngest child is 1 to 6 years old and/or one or more children (any age) require significantcare|
|||
|**99**|Data not collected|


### V8.2 VoucherTracking
|**Value**|**Text**|
|---|---|
|**1**|Referralpackage forwarded to PHA|
|**2**|Voucher denied byPHA|
|**3**|Voucher issued byPHA|
|**4**|Voucher revoked or expired|
|**5**|Voucher in use – veteran moved into housing|
|**6**|Voucher wasported locally|
|**7**|Voucher was administrativelyabsorbed bynew PHA|
|**8**|Voucher was converted to HousingChoice Voucher|
|**9**|Veteran exited – voucher was returned|
|**10**|Veteran exited – familymaintained the voucher|
|**11**|Veteran exited –prior to ever receivinga voucher|
|**12**|Other|


### V9.1 CMExitReason
|**Value**|**Text**|
|---|---|
|**1**|Accomplishedgoals and/or obtained services and no longer needs CM|
|**2**|Transferred to another HUD/VASHprogram site|
|**3**|Found/chose other housing|
|**4**|Did not complywith HUD/VASH CM|
|**5**|Eviction and/or other housingrelated issues|
|**6**|Unhappywith HUD/VASH housing|
|**7**|No longer financiallyeligible for HUD/VASH voucher|
|**8**|No longer interested inparticipatingin thisprogram|
|**9**|Veteran cannot be located|
|**10**|Veteran too ill toparticipate at this time|
|**11**|Veteran is incarcerated|
|**12**|Veteran is deceased|
|**13**|Other|
### V10 MentalHeathConsultation
|**Value**|**Text**|
|---|---|
|**1**|Mental health consultation completed|
|**2**|Mental health consultation beingcoordinated/arranged with VAprovider|
|**3**|Mental health consultation beingcoordinated/arranged with otherprovider|
|**4**|Offer declined|


### W1.2 HOPWAServices
Used in Services.csv when RecordType = 143 (HOPWA service).

|**Value**|**Text**|
|---|---|
|**1**|Adult daycare andpersonal assistance|
|**2**|Case management|
|**3**|Child care|
|**4**|Criminaljustice/legal services|
|**5**|Education|
|**6**|Employment and trainingservices|
|**7**|Food/meals/nutritional services|
|**8**|Health/medical care|
|**9**|Life skills training|
|**10**|Mental health care/counseling|
|**11**|Outreach and/or engagement|
|**12**|Substance use services/treatment|
|**13**|Transportation|
|**14**|Other HOPWA funded service|


### W2.2 HOPWAFinancial Assistance
Used in Services.csv when RecordType = 151 (HOPWA financial assistance).

|**Value**|**Text**|
|---|---|
|**1**|Rental assistance|
|**2**|Securitydeposits|
|**3**|Utilitydeposits|
|**4**|Utility payments|
|**7**|Mortgage assistance|


### W3 NoAssistanceReason
|**Value**|**Text**|
|---|---|
|**1**|Applied;decisionpending|
|**2**|Applied;client not eligible|
|**3**|Client did not apply|
|**4**|Insurance type not applicable for this client|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|
### W4.3 ViralLoadAvailable
|**Value**|**Text**|
|---|---|
|**0**|Not available|
|**1**|Available|
|**2**|Undetectable|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|


### W4.B TCellSource / ViralLoadSource
|**Value**|**Text**|
|---|---|
|**1**|Medical Report|
|**2**|Client Report|
|**3**|Other|


### W5.1 HousingAssessmentAtExit
|**Value**|**Text**|
|---|---|
|**1**|Able to maintain the housingtheyhad atproject entry|
|**2**|Moved to new housingunit|
|**3**|Moved in with family/friends on a temporarybasis|
|**4**|Moved in with family/friends on apermanent basis|
|**5**|Moved to a transitional or temporaryhousingfacilityorprogram|
|**6**|Client became homeless – movingto a shelter or otherplace unfit for human habitation|
|**7**|Jail/prison|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**10**|Deceased|
|**99**|Data not collected|


### W5.A-B SubsidyInformation
Values from W5.A are as listed in the HMIS Data Dictionary; values from W5.B are 10 higher. The validity of a value should be assessed in combination with the value of _HousingAssessmentAtExit_ ; valid _HousingAssessmentAtExit_ values for each item are shown in the third column below.

|**Value**|**Text**|**HousingAssessmentAtExit**|
|---|---|---|
|||**Values**|
|**1**|Without a subsidy|1|
|**2**|With the subsidytheyhad atproject entry|1|
|**3**|With an on-goingsubsidyacquired sinceproject entry|1|
|**4**|But onlywith other financial assistance|1|
|**11**|With on-goingsubsidy|2|
|**12**|Without an on-goingsubsidy|2|
### C2.2 MovingOnAssistance
|**Value**|**Text**|
|---|---|
|**1**|Subsidized housingapplication assistance|
|**2**|Financial assistance for MovingOn|
|**3**|Non-financial assistance for MovingOn|
|**4**|Housingreferral/placement|
|**5**|Other(please specify)|


### C3.2 CurrentSchoolAttend
|**Value**|**Text**|
|---|---|
|**0**|Not currentlyenrolled in anyschool or educational course|
|**1**|Currentlyenrolled but NOT attendingregularly (when school or the course is in session)|
|**2**|Currentlyenrolled and attendingregularly (when school or the course is in session)|
|**8**|Client doesn’t know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|


### C3.A MostRecentEdStatus
|**Value**|**Text**|
|---|---|
|**0**|K12: Graduated from high school|
|**1**|K12: Obtained GED|
|**2**|K12: Dropped out|
|**3**|K12: Suspended|
|**4**|K12: Expelled|
|**5**|Higher education: Pursuinga credential but not currentlyattending|
|**6**|Higher education: Dropped out|
|**7**|Higher education: Obtained a credential/degree|
|**8**|Client doesn't know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|


### C3.B CurrentEdStatus
|**Value**|**Text**|
|---|---|
|**0**|Pursuinga high school diploma or GED|
|**1**|PursuingAssociate’s Degree|
|**2**|PursuingBachelor’s Degree|
|**3**|PursuingGraduate Degree|
|**4**|Pursuingotherpost-secondarycredential|
|**8**|Client doesn't know|
|**9**|Clientprefers not to answer|
|**99**|Data not collected|
## **Appendix C – Custom File Transfer Template**

## Custom*.csv

Custom.csv contains data defined by parties engaged in HMIS data exchange. The file name would change based upon the custom data exchange request. This template is provided as a suggestion for how custom data elements may be exported using the standard + custom CSV schema. This file is not designed to be a required part of standard CSV exports.

|**DE#**|**Name**|**Type **|**List**|**Null**|**Notes**|
|---|---|---|---|---|---|
||CustomQuestionID|S32|||Unique identifier|
||EnrollmentID|S32||||
||PersonalID|S32||||
||CustomQuestionGroup|S250|*|Y||
||CustomQuestionOrder|I|*|Y||
||CustomQuestion|S250|*|Y||
||CustomAnswer|S250|*|Y|*|
||CustomDetailAnswer|S250|*|Y|*|
||DateCreated|T||||
||DateUpdated|T||||
||UserID|S32||||
||DateDeleted|T||Y||
||ExportID|S32|||Must match_ExportID_in Export.csv|


* Must be defined by parties to the data exchange.

_This material is based upon work supported, in whole or in part, by Federal award number H-21-NP-VA-001 awarded to ICF by the U.S. Department of Housing and Urban Development. The substance and findings of the work are dedicated to the public. Neither the United States Government, nor any of its employees, makes any warranty, express or implied, or assumes any legal liability or responsibility for the accuracy, completeness, or usefulness of any information, apparatus, product, or process disclosed, or represents that its use would not infringe privately-owned rights. Reference herein to any individuals, agencies, companies, products, process, services, service by trade name, trademark, manufacturer, or otherwise does not constitute or imply an endorsement, recommendation, or favoring by the author(s), contributor(s), the U.S. Government or any agency thereof. Opinions contained herein are those of the author(s) and do not necessarily reflect the official position of, or a position that is endorsed by, HUD or any Federal agency._
