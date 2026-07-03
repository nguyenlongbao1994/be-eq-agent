---
id: INC-2024-12-11-MOLDING-VACUUM-CHAMBER-TEST-FAIL-EQMLD000146-P3
date: 2024-12-11
time: "10:45-13:15"
station: Molding
machine: EQMLD000146
model: C8.5 Small
press: 3
issue_type:
  - Utility
  - Vacuum
  - Mechanical
  - Maintenance
status: Recovered / Preventive action defined
owner: EQ / PD
tags:
  - molding
  - c8.5-small
  - vacuum
  - chamber
  - functional-test
  - drain-separator-filter
  - press3
  - moldchase
---

# Molding EQMLD000146 Small – Functional test vacuum chamber mold failed

## Issue Summary
- EQ ID: MOLDING EQMLD000146 Small
- Issue happened time & date: 10:45 12/11/2024
- Equipment recover time & date: 13:15 12/11/2024

## Recovery Timeline
- 12/11 10:45
  - Issue: Functional test vacuum chamber mold failed – Press 3
- 12/11 11:30
  - Removed mold chase to find root cause
- 12/11 13:15
  - Swapped mold chase from #146 to #154 to continue cleaning and conditioning process
  - PD continued Big Cleaning process
- 12/11 14:30
  - #154: Finished FAI, machine production normal
  - #146: continued root-cause finding for handling issue

## Symptom
- Functional test of vacuum chamber mold failed at Press 3.
- Vacuum actual value was 459 hPa.
- Test result failed because the vacuum value exceeded the allowable range.

## Impact Area
- Down time: 2.5 hours
- Time range: 10:45 – 13:15

## Root Cause Analysis
### Issue finding
- Functional test vacuum chamber mold failed
- Vacuum actual value: 459 hPa
- Test result: fail

### Root Cause
- Air leakage caused vacuum to exceed the allowable value.
- Vacuum leak was found at the drain separator filter of Press 3.
- Cover of the filter was loose.
- Because of the leakage, vacuum functional test could not reach standard value.

## Failure Mechanism
- Vacuum system integrity depends on proper sealing of the drain separator filter assembly.
- When the filter cover became loose, air leakage occurred in the vacuum line.
- The leakage increased the measured vacuum actual value to 459 hPa, which was outside the allowable range.
- Because the system could not maintain correct vacuum condition, functional test of vacuum chamber mold failed.

## Corrective Action
1. Checked and replaced O-ring at the board and cavity of the mold chase
   - Result: no abnormality found
2. Swapped mold chase from #146 to #154 to continue production

## Preventive Action
1. Added marking on the body of the drain separator vacuum to check whether it becomes loose
2. Test vacuum functional condition after mold-chase maintenance
3. Check vacuum system of cavity and board vacuum after mold-chase maintenance

## Current Status
- Production was continued by swapping mold chase to #154
- #154 finished FAI and machine production became normal
- Preventive action was defined to strengthen loose-filter-body detection and post-maintenance vacuum checks

## Impact
- Quality: vacuum functional test failed at Press 3
- Production: 2.5 hours downtime, production moved to alternate mold chase
- Safety: not stated in the report
- Repeat risk: possible if drain separator filter body loosens again and vacuum checks are not performed after maintenance

## Open Risk / Follow-up
- Need to monitor whether drain separator filter body loosens again
- Need to verify cavity / board vacuum after every mold-chase maintenance
- Need to keep marking visible and used as quick inspection reference

## Evidence
- Attached slides show:
  - issue summary and recovery timeline
  - vacuum actual value of 459 hPa
  - loose drain separator filter area
  - corrective and preventive action photos
