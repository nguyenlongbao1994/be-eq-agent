---
id: INC-2024-12-07-MOLDING-C85SMALL-BELT-BROKEN-EQMLD00154
date: 2024-12-07
time: "14:30 12/07 - 10:00 12/08"
station: Molding
machine: EQMLD00154
model: C8.5 Small
issue_type:
  - Mechanical
  - Sensor
  - Control
  - Handling
status: Recovered / Dry-run normal / Monitoring
owner: EQ / PD
tags:
  - molding
  - c8.5-small
  - belt-broken
  - compound-handle
  - pusher
  - belt-detection-flag
  - proximity-sensor
  - mold-chase
---

# Molding C8.5 Small – Belt Broken

## Issue
- Issue description: Belt of Pusher is Broken
- Model: C8.5 Small
- Machine: EQMLD00154
- Time range: 14:30 12/07 – 10:00 12/08

## Timeline
- 12/07 14:30 → Issue 1: Belt pusher of compound handle is broken
- 12/07 16:45 → Finished changing new belt, returned machine for PD
  - PD performed small cleaning process
- 12/07 19:50 → Issue 2: Cannot push panel out of mold chase
- 12/08 05:00 → Could not solve issue at #154
  - Changed #147 SMALL to #BIG to continue production coverage
  - EQ swapped mold chase and PR-SET
  - PD performed big cleaning process
- 12/08 11:00 → 
  - #147 finished FAI, machine production normal
  - #154 root-cause finding on handling issue completed
  - Machine recovered and dry-run test normal

## Symptom
- Compound-handle pusher belt broke.
- After belt replacement, machine still showed error when pushing panel out of mold chase.
- Panel had already moved out of mold chase, but machine still alarmed.

## Root Cause
### Issue 1
- Belt pusher of compound handle broke.
- Compound-handle pusher belt was suddenly broken on the right side.

### Issue 2
- During belt replacement, EQ set the BELT DETECTION FLAG to an incorrect position.
- When pusher ejected, BELT DETECTION FLAG did not return to original position.
- Proximity sensor for pusher-ejected 356A could not turn Light OFF.
- Panel had already moved out of mold chase, but machine still generated alarm.

## Failure Mechanism
- The first failure was a mechanical belt break at the compound-handle pusher on the right side.
- After replacing the belt, the detection flag position was not set correctly.
- Because BELT DETECTION FLAG did not return to the correct original position during pusher movement, the proximity sensor state stayed incorrect.
- The control system therefore still judged pusher-ejected condition as abnormal even though the physical panel had already moved out of mold chase.
- This created a false handling / push-out alarm after the mechanical repair.

## Actions
### Short term
1. Replace new belt pusher of compound handle
2. Switch machine #147 SMALL to #BIG to continue production
3. Adjust position of BELT DETECTION FLAG

### Long term
1. Create guideline / training for engineers on how to change the belt in order to reduce repair time
2. Night-shift DRI with 6 months experience was noted as not having enough experience / knowledge to focus on finding root cause
3. Arrange DL with 4 years experience to work at night shift to improve handling issue capability

## Current Status
- Mechanical belt issue was repaired by replacing the belt.
- Detection issue was corrected by adjusting BELT DETECTION FLAG position.
- Machine #154 recovered.
- Dry-run test for #154 was normal.
- Machine #147 finished FAI and production returned to normal for coverage.
- Current status: recovered, continue monitoring.

## Impact
- Quality: not explicitly stated as panel NG quantity in the slide
- Production: machine interruption and coverage switch from #154 to #147
- Safety: not stated in the report
- Repeat risk: possible if belt-change method and flag-position setup are not standardized and trained

## Open Risk / Follow-up
- Need to standardize belt replacement setup method
- Need to include BELT DETECTION FLAG position verification after belt change
- Need to strengthen night-shift troubleshooting capability
- Need to monitor whether false pusher-ejected detection happens again after maintenance

## Evidence
- Attached slides show:
  - broken pusher belt
  - BELT DETECTION FLAG
  - correct vs incorrect detection position
  - action direction for short-term and long-term improvement
