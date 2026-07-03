---
id: INC-2025-01-13-MOLDING-C105SMALL-INCOMPLETE-MOLDING-SYS851380-P3
date: 2025-01-13
station: Molding
machine: system#851380
model: C10.5 Small
press: 3
issue_type:
  - Process
  - Transfer
  - Control
  - Vendor analysis
status: Short-term containment done / Vendor analysis pending
owner: EQ / Vendor / Helpdesk
tags:
  - molding
  - c10.5-small
  - incomplete-molding
  - press3
  - transfer-stopped
  - unexpected-transfer-error
  - system851380
  - brick-logging
---

# Molding C10.5 Small – Incomplete Molding (Press 3)

## Issue
- Issue: Incomplete Molding
- Machine / System: system#851380
- Press: 3
- Model: C10.5 Small
- Date key used in this file: 2025-01-13
- Note: a vendor slide shows "13 Dec 2025", but the local molding slides show log/time as 1/13/2025

## Symptom
- Incomplete molding happened at Press 3.
- Transfer stopped abnormally during pellet transfer.
- Incomplete fill occurred and 2 strips were rejected according to the vendor slide.

## Local Root Cause Analysis

### 1. Check log file machine
- Machine log was checked from 08:00 to 13:12 on 1/13/2025.
- There were 2 types of machine alarms in the assist list.
- All alarms were judged as common alarms and not directly related to molding corner crack / incomplete molding issue.

### 2. Check mold chase
- Bottom mold: normal
- Top mold: normal
- Area inside mold chase: no abnormality found

### 3. Check + profile shot FAI
- Transfer pressure spec: 6.5–11 MPa
- Actual transfer pressure: 6.9 MPa → OK
- Transfer clamp force spec: 50–60 Ton
- Actual transfer clamp force: 55 Ton → OK
- Trend of pressure & clamp force: no abnormality → Normal

### 4. Check cylinder – clamp force
- Clamp force Left and Right: balanced
- Slide conclusion: clamp force Left and Right is balance

### 5. Check transfer profile at shot where issue happened
- Check history input panel:
  - panel NG was input at Press 3
  - Shot 34/34 at 13:12 PM
- Slide conclusion:
  - molding incomplete happened because transfer stopped soon
  - transfer did not follow recipe
  - profile transfer was abnormal

## Root Cause
- Common machine alarms were not linked directly to the issue.
- Mold chase condition was normal.
- FAI shot profile, transfer pressure, clamp force, and clamp-force balance were normal.
- The issue shot showed abnormal transfer profile.
- Therefore, the current local conclusion is that transfer stopped too early and did not follow recipe, which caused incomplete molding.

## Failure Mechanism
- Under normal FAI condition, transfer pressure and clamp force stayed within spec.
- At the issue shot, transfer path stopped early and deviated from the normal recipe transfer profile.
- Because transfer stopped during pellet / transfer sequence, molding fill became incomplete.
- Since mold chase, clamp balance, and FAI process profile were normal, the strongest current mechanism is abnormal transfer stopping rather than mold-chase mechanical damage.

## Vendor / Advanced Analysis

### Vendor problem statement
- On the vendor slide, the case is described as:
  - system#851380 Press 3 suddenly triggered:
    - "Unexpected transfer error"
  - during transferring pellet
  - causing incomplete fill
  - 2 strips were rejected

### What vendor side knew
- This was described as the 3rd time incomplete fill happened on this press
- There was no machine error prior to the issue
- There was a "Tracking error" from log file, but not specific enough to explain the cause
- There was abnormal transfer data from -27 to -71 in 0.2 sec
- After the issue happened, the machine could still run a few dummy shots without repeating the error

### What vendor side did
1. Replaced all transfer-related spare parts:
   - transfer spindle
   - loadcell
   - transfer motor
   - transfer drive
   - transfer amplifier
2. Checked wiring connection:
   - detected untightened resolver cable
   - re-tightened resolver cable
3. Ran dummy shot for checking:
   - issue did not happen during dummy-shot validation

### Validation
- After resuming production, the issue happened again after 33 shots

### Next plan
- Brick logging was collected and submitted to helpdesk
- Goal: get more detailed evidence on why transfer stopped

## Actions from local molding slide

### Short term
1. Temporary stop Press 3
2. Change run to Press 1 and Press 2
3. Run dummy shot for checking
   - issue did not happen during dummy-shot check

### Long term
1. Send root logfile to vendor for checking and analysis
2. Continue vendor-side analysis on transfer stopping condition

## Current Status
- Short-term containment was completed:
  - Press 3 stopped
  - Press 1 & 2 used for production continuation
  - dummy-shot check initially showed no issue
- However, vendor validation later showed issue repeated again after 33 shots.
- Current status remains open:
  - vendor / helpdesk analysis pending

## Impact
- Quality: incomplete fill with 2 rejected strips in vendor statement
- Production: Press 3 required stop / containment
- Safety: not stated in the slides
- Repeat risk: high because the issue repeated even after spare-part replacement and resolver-cable tightening

## Open Risk / Follow-up
- Need vendor / helpdesk confirmation from brick logging
- Need further explanation why transfer stopped suddenly
- Need to verify whether issue is linked to hidden transfer-control logic, resolver feedback, or tracking instability
- Need stable validation before Press 3 full release

## Evidence
- Attached slides show:
  - local molding RCA: machine-log check, mold-chase check, normal FAI transfer profile, balanced clamp force, abnormal transfer profile at issue shot
  - vendor slide: problem statement, what vendor knew, what vendor did, validation repeat after 33 shots, and next-plan brick logging
