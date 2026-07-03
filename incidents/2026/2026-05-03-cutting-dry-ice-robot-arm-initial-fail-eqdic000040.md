---
id: INC-2026-05-03-CUTTING-DRY-ICE-ROBOT-ARM-INITIAL-FAIL-EQDIC000040
date: 2026-05-03
station: Cutting Dry Ice
machine: EQDIC000040
project: N240
issue_type:
  - Electrical
  - Control
  - Robot arm
  - Battery
status: Spare prepared / Vendor calibration ongoing
owner: EQ / Vendor / ME
tags:
  - cutting-dry-ice
  - robot-arm
  - initial-fail
  - power-on
  - epson
  - battery
  - er17330v
  - n240
---

# N240 – Cutting Dry Ice #40 Robot Arm Initial Fail

## Issue
- Station / Project: N240 / Cutting Dry Ice
- Machine: #40
- Problem statement:
  - Robot arm initial fail after turning on machine power

## Customer Impact
- LBO build delay: 2 days at Cutting Dry Ice compared with original build plan
- Shipment impact: no impact stated
  - ETD: 5/14
  - ETA: 5/18

## Containment Actions
1. 1K WIP after Cutting Dry Ice continue to input until test
2. 2.4K WIP before Cutting Dry Ice stored in Drybox
3. Recovery build plan:
   - Buy off 1x Cutting Dry Ice #28 machine from N243 for N240

## FA & RC
1. Machine was turned off on 5/1 (internal holiday) because facility power was off during maintenance, and the issue was found when machine power was turned on again on 5/3.
2. Opened the main machine interface:
   - EPSON robot arm had no power
   - initialize failed
   - machine alarm: absolute encoder power supply failure
3. Based on vendor analysis:
   - robot arm had a problem with control-board battery
   - battery type shown in slide: LITHIUM ER17330V

## Failure Mechanism
- After a long machine-off period due to facility maintenance power shutdown, the robot arm failed to initialize on machine power-on.
- The EPSON robot arm relies on stable battery-backed control / encoder condition.
- The machine showed absolute encoder power-supply failure.
- Vendor analysis linked the issue to the robot-arm control-board battery.
- Because initialization could not complete, Machine #40 could not enter normal common run condition.

## Corrective Actions
1. Prepare alternative battery spare part for replacement
   - Done
2. Continue troubleshooting and calibration of robot arm with vendor
   - On going from 5/4
3. Review spare-parts list for battery of all backend machines
   - Submit PR28162 DEV to buy battery as spare

## Next Steps
1. MBO Cutting Dry Ice #28 from N243 as temporary back-up to finish N240 LBO if Machine #40 cannot be fixed in time
   - DRI: ME
   - Checkpoint for MBO approval: 5/5 9:00 AM
2. Audit virtual line, identification label, and N240 recipe program with Cutting Dry Ice #28 before input LBO FAI
   - DRI shown in slide
   - Checkpoint shown in slide: 5/5

## Current Status
- Alternative battery spare was prepared.
- Vendor troubleshooting and calibration were still ongoing at the time of the slide.
- Backup-build plan using Cutting Dry Ice #28 from N243 was defined if Machine #40 could not recover in time.

## Impact
- Quality: no direct NG quantity shown in slide
- Production: 2-day LBO delay at Cutting Dry Ice
- Safety: not stated in the slide
- Repeat risk: possible if robot-arm battery health is not controlled after long machine-off periods

## Open Risk / Follow-up
- Need vendor to complete robot-arm troubleshooting and calibration
- Need to confirm whether battery replacement fully removes initialize fail
- Need to review other backend machines for the same battery risk
- Need backup execution plan with Cutting Dry Ice #28 ready if #40 cannot recover in time
