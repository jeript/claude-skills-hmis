# HMIS Skills for Claude Code

Custom [Claude Code](https://claude.com/claude-code) skills for working with HUD HMIS (Homeless Management Information System) data in R.

These skills provide Claude with the official HUD programming specifications so it can accurately assist with HMIS data analysis, report logic, and R code generation.

## Skills

| Skill | Description |
|-------|-------------|
| `hmis-foundations` | HMIS Standard Reporting Terminology Glossary - Active Clients, Age, Chronic Homelessness, Household Types, Leavers/Stayers, Income, Annual Assessment, Data Quality, and more |
| `hmis-spm` | System Performance Measures - Length of time homeless, Returns to homelessness, First-time homeless, Income growth, Successful placement/retention |
| `hmis-csv` | HMIS CSV Format Specifications - File schema, field names, data types, join keys, project type codes, plus R helper functions |

## Installation

Copy the skill folders to your global Claude Code skills directory:

```bash
# macOS/Linux
cp -r hmis-foundations hmis-spm hmis-csv ~/.claude/skills/

# Windows (PowerShell)
Copy-Item -Recurse hmis-foundations, hmis-spm, hmis-csv "$env:USERPROFILE\.claude\skills\"
```

Skills will be automatically available in all Claude Code sessions.

## Source Specifications

The skills were derived from these official HUD documents (FY 2026, released October 2025):

- `HMIS-Standard-Reporting-Terminology-Glossary MD.md` - Foundational building blocks for all HMIS reports
- `System-Performance-Measures-HMIS-Programming-Specifications MD.md` - SPM programming specs
- `HMIS-CSV-Format-Specifications_2026 MD.md` - CSV file format and data dictionary
- `HMIS-Programming-Specifications-CoC-APR-and-ESG-CAPER MD.md` - APR/CAPER specs (for reference)

## R Helper Functions

`00_helper_functions.R` contains lookup functions for translating HMIS numeric codes to labels:

- `living_situation()`, `extended_living_situation()` - Destination/living situation codes
- `project_type()`, `project_type_ext()`, `project_type_abb()` - Project type codes
- `funding_type()` - Federal funding source codes
- `disability_type()`, `household_type()`, `rel_to_hoh()` - Various HMIS enumerations
- And more - see the file for the full list

## Usage

When working with HMIS data in R, the skills trigger automatically based on context. You can also invoke them directly:

```
/hmis-foundations   # For active clients, age, CH status, etc.
/hmis-spm           # For system performance measures
/hmis-csv           # For CSV schema and field references
```

## Data Standards Alignment

All specifications align with **FY 2026 HMIS Data Standards**, effective October 1, 2025.
