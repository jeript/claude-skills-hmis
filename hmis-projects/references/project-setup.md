# Project Setup Rules

## 2.01 Organization Information

- One OrganizationID per organization, shared across all its projects
- `VictimServiceProvider`: 0=No, 1=Yes (VSPs use comparable databases, not HMIS)
- Organization can be activated/deactivated

## 2.02 Project Information

### Key Fields

| CSV Field | Description |
|-----------|-------------|
| ProjectID | Unique, system-generated |
| OrganizationID | FK to Organization.csv |
| ProjectName | Readable, recognizable name (not GUID, not just project type) |
| ProjectType | See project type table in SKILL.md |
| HousingType | 1=Site-based single, 2=Site-based clustered, 3=Tenant-based scattered |
| RRHSubType | 1=Services Only, 2=Housing with/without services (only for type 13) |
| OperatingStartDate | First day of services/housing |
| OperatingEndDate | Last day (NULL if still operating) |
| ContinuumProject | 0=No, 1=Yes |
| TargetPopulation | 1=DV survivors, 3=HIV/AIDS, 4=N/A |
| HOPWAMedAssistedLivingFac | 0=No, 1=Yes, 9=Not applicable |

### Project Type Changes

If the nature of a project changes such that project type is no longer appropriate:
- For corrections: edit the ProjectType field
- For actual operational changes (e.g., TH → PSH): create a **new project** with the new type

### Supportive Services Only (SSO) Projects

- SSO providing services not limited to specific residential projects: `AffiliatedWithResidentialProject` = No
- SSO affiliated with residential project(s): `AffiliatedWithResidentialProject` = Yes, record the residential ProjectID(s)
- Affiliation criteria: serves subset of residential clients, serves for portion of stay, or information sharing not allowed

### RRH Subtypes

| Subtype | Code | Receives Rental Funds | Has Inventory |
|---------|------|:--------------------:|:-------------:|
| Services Only | 1 | No (housing from other source) | No |
| Housing with/without services | 2 | Yes (even if not all participants) | Yes |

If subtype changes: close project record, open new one with new subtype.

### Emergency Shelter Setup

**ES-EE (type 0):** Full record at entry and exit. Length of stay = start to exit.

**ES-NbN (type 1):** Full record at entry, then each night recorded separately. Length of stay = count of bed-nights.
- Auto-exit: community-defined absence period (e.g., 90 days from last bed-night)
- Exit date = day after last bed-night
- Destination for auto-exit = "No exit interview completed"

**Changing shelter type (EE↔NbN):**
1. Create new project with new ES type
2. Exit all clients from old project
3. Enter clients into new project
4. Deactivate old project

### Multiple Funding Sources

**Same clients served by all grants:** Single project OK, record all funding sources in 2.06.

**Different clients under different grants:** Must be possible to identify which clients served by which grant:
- Option 1: Separate projects per grant
- Option 2: Additional data collection linking enrollments to grants

## 2.03 Continuum of Care Information

- Each project associated with one or more CoC codes
- Projects operating in multiple CoCs: separate ProjectCoC record per CoC
- Geocode must be within the CoC in the same record
- Geography Type: Urban, Suburban, Rural (per HUD crosswalk, not locally defined)

## 2.06 Funding Sources

### Key Fields

| CSV Field | Description |
|-----------|-------------|
| FunderID | Unique identifier |
| ProjectID | FK to Project.csv |
| Funder | Federal partner program code (see `funding_type()` in helper functions) |
| GrantID | Grant identifier (may be shared across projects under same grant) |
| StartDate | Grant start date |
| EndDate | Grant end date (NULL if ongoing/renewed) |

### Key Funding Source Codes

| Code | Program |
|------|---------|
| 2 | HUD: CoC - PSH |
| 3 | HUD: CoC - RRH |
| 4 | HUD: CoC - SSO |
| 5 | HUD: CoC - TH |
| 6 | HUD: CoC - Safe Haven |
| 8-11 | HUD: ESG (ES, HP, RRH, SO) |
| 20 | HUD: HUD/VASH |
| 21 | HHS: PATH |
| 22-26 | HHS: RHY programs |
| 33 | VA: SSVF |
| 35 | HUD: Pay for Success |
| 43 | HUD: CoC - YHDP |
| 44 | HUD: CoC - Joint TH/RRH |
| 53 | HUD: ESG-RUSH |
| 54 | HUD: Unsheltered Special NOFO |
| 55 | HUD: Rural Special NOFO |
| 56 | HUD: CoC Builds |

Grant dates critical for:
- SPM Measure 4 (CoC-funded projects only)
- Any fund-specific reporting
- Determining which projects were active during a report period

## 2.08 HMIS Participation Status

| Code | Status |
|------|--------|
| 0 | Not Participating |
| 1 | HMIS Participating |
| 2 | Comparable Database Participating |

- Has start/end dates for each participation record
- When status changes: close old record, create new one
- When project stops participating: exit all clients, create "Not Participating" record, do NOT change inventory
- When project ceases operations: end date = OperatingEndDate

## 2.09 CE Participation Status

Tracks two things:
1. **Is the project a CE Access Point?** (Yes/No)
   - If Yes, what activities: HP assessment/screening/referral, Shelter assessment/screening/referral, or both
2. **Does the project receive CE referrals?** (Yes/No)

Has start/end dates. Both statuses can change over time independently. When project ceases operations, end date = OperatingEndDate.
