---
id: INC-2023-12-21-MOLDING-C85SMALL-CYLINDER-ERROR-EQMLD00146-P1
date: 2023-12-21
time: "12:11 PM"
station: Molding
machine: EQMLD00146
model: C8.5 Small
press: 1
issue_type:
  - Mechanical
  - Clamp
  - Cylinder
  - Control
status: Recovered / Monitoring
owner: EQ
tags:
  - molding
  - c8.5-small
  - cylinder-error
  - clamp-force
  - press1
  - left-cylinder
  - calibration
---

# Molding C8.5 Small – Cylinder Error

## Issue
- Issue description: Cylinder error
- Model: C8.5 Small
- Machine: EQMLD00146
- Time: 12:11 PM (21/12/2023)

## Timeline
- 12:11 PM → Machine alarm: Final clamping: clamp cylinder reached end position
- 12:15 PM → Checking machine:
  - Clamp force left is abnormal
  - Cannot apply high clamp force
  - Clamp force Left/Right = 13 / 344
- 12:20 PM → Stop input at Press 1, continue running with Press 2
- 06:05 AM → Replace left cylinder at Press 1, calibration after change, dry-run with FR4, result OK
  - Clamp force Left/Right after recovery = 272 / 277

## Symptom
- Machine showed cylinder-related alarm during final clamping.
- Left side clamp force was abnormal and could not apply high clamp force properly.

## Root Cause
- Manual apply-high-clamp-force test found that the left cylinder had a problem.
- The left cylinder could not apply high clamp force.
- Clamp force between left and right side was significantly different: 13 / 344.

## Failure Mechanism
- Final clamping requires sufficient clamp force from both left and right sides.
- The left clamp cylinder was unable to generate the required high clamp force.
- Because clamp force on the left side was too low, the clamp cylinder reached end position abnormally and machine reported final clamping error.
- The large force imbalance between left and right side created unstable final clamping condition.

## Actions
1. Replaced the left cylinder at Press 1.
2. Ran cylinder calibration for Press 1.
3. Manually checked balance between left and right after replacement:
   - Left / Right = 272 / 277
4. Added rule to test manual apply-high-clamp-force during weekly maintenance.
5. If clamp force difference between left and right is out of spec (>10 kN):
   - replace the cylinder with the lower value side.

## Current Status
- Left cylinder was replaced.
- Calibration was completed.
- Dry-run with FR4 result was OK.
- Clamp force balance after replacement became 272 / 277.
- Current status: machine recovered, continue monitoring.

## Impact
- Quality: no panel NG quantity stated in the slide
- Production: Press 1 input was stopped temporarily; production continued with Press 2 during containment
- Safety: not stated in the report
- Repeat risk: possible if cylinder degradation is not checked by weekly manual high-clamp-force verification

## Open Risk / Follow-up
- Need to continue weekly manual apply-high-clamp-force check
- Need to monitor left/right clamp-force gap over time
- Need to follow replacement rule if force difference exceeds >10 kN

## Evidence
- Attached slides showing:
  - final clamping alarm
  - abnormal left/right clamp force value (13 / 344)
  - recovery value after replacement (272 / 277)
  - action rule for weekly maintenance and cylinder replacement criteria
