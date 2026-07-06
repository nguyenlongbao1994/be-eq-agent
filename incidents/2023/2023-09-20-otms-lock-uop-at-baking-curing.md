---
id: INC-2023-09-20-OTMS-LOCK-UOP-AT-BAKING-CURING
date: 2023-09-20
time: "17:35-09:30"
station: Baking / Curing
system: OTMS System
model: C8.5 Small / Big
issue_type:
  - IT
  - System
  - OTMS
  - Traceability
  - UOP Lock
status: Recovered after OTMS restore / OCAP update and IT ownership defined
owner: EQ / SMDC / IT / PD
tags:
  - otms
  - uop-lock
  - baking
  - curing
  - sfis
  - traceability
---

# OTMS system issue report

## Issue
- Problem: Lock UOP at Baking / Curing
- OTMS System: Baking and Curing Station
- Model: C8.5 Small / Big
- Time: From 17:35 (09/20/2023) to 09:30 (09/21/2023)
- Lock qty:
  - Baking 1: 3,125 pcs
  - Curing 5: 23,564 pcs

## Symptom
- OP detected OTMS system could not auto pass station after finish baking.
- S/N barcode could not auto pass Baking and Curing station.
- A large quantity of S/N was locked UOP at Baking 1 and Curing 5.
- From 17:29 to 18:22 on 20/09/2023, OTMS did not record oven machine temperature profile data.
- EQ checked actual oven condition and confirmed oven still baked / cured normally.

## Timeline
- 17:35 (09/20/2023)
  - OP detected OTMS system could not auto pass station after finish baking
- 18:00 (09/20/2023)
  - EQ contacted SMDC Engineer
  - At 18:22, EQ waited for finish baking to check result
- 20:30 (09/20/2023)
  - EQ checked status of S/N barcode and found it still could not auto pass Baking and Curing station
  - EQ contacted SMDC team, but there was no engineer working in night shift
- 09:30 (09/21/2023)
  - SMDC Engineer recovered OTMS system

## Root Cause Analysis

### 1. Why after finish baking, Baking and Curing station could not auto pass station
- EQ checked with SMDC team and found:
  - at 17:31 (09/20/2023), someone logged in to computer OTMS server
  - Server: VN1SOTMSP02.vnfs.com
  - Account name: VN1SOTMSP02
  - The login modified and changed the “auditing setting on object”
- Because that audit setting was changed:
  - OTMS system could not pass station automatically

### 2. Why S/N barcode was locked UOP at Baking station and Curing station
- PD needed to pass Baking and Curing station by Lot Packing
- At that time, all abnormal S/N barcode still remained in OTMS system
- After OTMS SFIS move-out automatic function was recovered at 09:30 (09/21/2023):
  - all remained S/N barcode on OTMS was passed through Baking and Curing station again
  - all these S/N barcode became lock UOP

## Root Cause
- The direct system problem was caused by modified audit setting on the OTMS server.
- That change blocked OTMS automatic pass function for Baking / Curing station.
- During the abnormal period, PD used Lot Packing to move lots while abnormal S/N still remained in OTMS.
- After OTMS auto function recovered, those remaining S/N were passed again in system flow and became UOP locked.
- Therefore the issue was a system / traceability control failure, not an actual oven process failure.

## Failure Mechanism
- OTMS controls the automatic move-out / pass logic for Baking and Curing station.
- When the server audit setting on object was modified, OTMS could no longer auto pass station.
- Because the traceability state in OTMS remained abnormal, PD used Lot Packing to continue station passing manually.
- Since abnormal S/N still remained in OTMS, the system state became duplicated / inconsistent.
- After auto function was recovered, OTMS passed those S/N again, which created UOP lock.
- During the same trouble window, OTMS also failed to record temperature profile data, but EQ and SMDC confirmed oven actual temperature and running status were still normal under controller setup (KP1000).
- This means the main problem was OTMS system / audit-policy / traceability logic, not actual Baking / Curing equipment process failure.

## Actions
1. Co-work with IT team to find who modified “audit policy change”
2. In case OTMS cannot auto pass station:
   - PD must output Baking and Curing by Lot Packing only after removing abnormal S/N from OTMS
   - Do not output by Lot Packing while abnormal S/N still remain in OTMS system
3. Update OCAP
   - Checkpoint: 09/23
4. SMDC team provided OTMS DRI contact window:
   - Mr. Bob
   - support contact available 24/7

## Additional Verification
- From 17:29 to 18:22 on 20/09/2023, OTMS did not record oven machine temperature profile data.
- EQ checked actual oven machine status and confirmed:
  - oven still kept baking / curing normally
  - actual indicator temperature was the same as program setup
- EQ double checked with SMDC Engineer:
  - OTMS only did not record temperature data
  - oven machine still kept running according to controller setup in Chinee KP1000

## Current Status
- SMDC Engineer recovered OTMS system at 09:30 on 09/21/2023.
- Baking / Curing equipment itself was confirmed still running normally during OTMS trouble.
- OCAP / escalation path was updated.
- IT follow-up remained necessary to identify who modified the audit-policy setting.

## Impact
- Quality:
  - Baking 1: 3,125 pcs lock UOP
  - Curing 5: 23,564 pcs lock UOP
- Production:
  - automatic pass function was blocked
  - manual pass by Lot Packing was required
- Safety:
  - not stated in the report
- Repeat risk:
  - high if OTMS audit-policy changes are not controlled and if PD passes lots manually without cleaning abnormal S/N from OTMS first

## Open Risk / Follow-up
- Need IT support to identify who modified audit policy setting
- Need to control OTMS server configuration / audit setting changes
- Need to enforce OCAP when OTMS cannot auto pass station
- Need to ensure abnormal S/N are removed from OTMS before any Lot Packing move-out action
- Need to maintain clear 24/7 contact ownership for OTMS issues

## Evidence
- Slide 1 confirms:
  - issue: Lock UOP at Baking / Curing
  - OTMS System: Baking and Curing Station
  - model: C8.5 small / big
  - time window from 17:35 (09/20/2023) to 09:30 (09/21/2023)
  - lock qty Baking 1 = 3,125 pcs and Curing 5 = 23,564 pcs
- Slide 2 confirms:
  - at 17:31 (09/20/2023), account VN1SOTMSP02 logged in to OTMS server and changed auditing setting on object
  - this blocked OTMS auto pass station
  - abnormal S/N remained on OTMS while PD passed stations by Lot Packing
  - after recovery, those S/N were locked UOP
- Slide 3 confirms:
  - OTMS did not record temperature profile data from 17:29 to 18:22
  - EQ checked actual oven status and temperature = normal
  - SMDC confirmed oven kept running by controller Chinee KP1000
