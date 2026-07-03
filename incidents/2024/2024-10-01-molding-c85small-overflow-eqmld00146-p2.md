---
id: INC-2024-10-01-MOLDING-C85SMALL-OVERFLOW-EQMLD00146-P2
date: 2024-10-01
time: "12:00 PM"
station: Molding
machine: EQMLD00146
model: C8.5 Small
press: 2
issue_type:
  - Process
  - Mechanical
  - Sensor
  - Pellet Supply
status: Corrective action done / Monitoring
owner: EQ / ME
tags:
  - molding
  - c8.5-small
  - overflow
  - pellet-gripper
  - sensor-4S26
  - press2
  - moldchase
  - pellet-supply
---

# Molding C8.5 Small – Molding Overflow (Press 2)

## Issue
- Issue description: Molding overflow  
- Model: C8.5 Small  
- Machine: EQMLD00146 – Press 2  
- Panel impact: 02 panels (under ME confirm)  
- Time: 12:00 PM (10/01/2024)

## Timeline
- 10/01 → FAI OK, machine start
- 11:14 → Machine alarm: Pellet receiver not in position
- 11:18 → EQ stopped machine, cleaned pellet gripper, and restarted machine
- 11:29 → Machine alarm: Transferring pellets unexpected
  - Molding overflow happened at Press #2 (shot number 2)
- 11:40 → Removed Press #2 and sent mold chaser to maintenance
- 12:00 → Replaced new pellet gripper rubber and continued running machine with Press #1 and Press #3

## Symptom
- Molding overflow occurred at Press 2.
- The remained cull after overflow was higher than normal.
- Machine alarm showed unexpected pellet transfer behavior.

## Root Cause Analysis
### 1. Check remained cull after molding overflow
- The remained cull was higher by 8 mm than normal cull.
- This indicated that compound supply into mold chase was larger than normal.
- Normally, 02 pellets are supplied into 01 hold.
- In this case, 03 pellets were supplied into 1 hold.

### 2. Check pellet gripper
- Pellet gripper was removed and checked.
- The rubber of the pellet gripper was damaged.
- Pellet gripper could close but could not hold molding compound correctly.

## Root Cause
- Damaged rubber on the pellet gripper could not hold compound securely.
- Because the pellet gripper could not hold compound, one extra compound / pellet dropped unexpectedly.
- Sensor 4S26 sensitivity was too low to detect the dropped compound quickly enough.

## Failure Mechanism
### Normal process of supply compound to compound handle
#### Step 1
- Loading compounds at “Pellet receiver position”
- Sensor: OFF
- Pellet Gripper: Open

#### Step 2
- Checking compound length at “Top of pellet position”
- Sensor: ON
- Pellet Gripper: Close

#### Step 3
- Go home to do next step at “Home position”
- Sensor: ON
- Pellet Gripper: Close

### Abnormal process
1. One extra compound dropped because the pellet gripper rubber was damaged and could not hold compound.
2. The extra compound dropped into carrier / path when pellet receiver returned to home position.
3. Sensor sensitivity was too low, so sensor could not detect the dropped compound quickly enough.
4. Extra pellet / compound was then transferred into mold chase.
5. Overflow happened during molding at Press 2.

## Actions
1. Remove Mold chaser PR2 to maintenance – Done
2. Replace new rubber of pellet gripper
3. Add item to check pellet gripper every month
4. Replace pellet gripper rubber in half-year maintenance
5. Adjust sensitivity of Sensor 4S26 from 6 to 8

## Current Status
- Mold chaser of Press 2 was removed to maintenance.
- New pellet gripper rubber was replaced.
- Machine resumed running with Press #1 and Press #3 from 12:00 PM.
- Preventive maintenance item and sensor-sensitivity correction were added.

## Impact
- Quality: 02 panels impacted (under ME confirm)
- Production: Press 2 removed from line for maintenance; line continued with Press #1 and #3
- Safety: not stated in the report
- Repeat risk: possible if pellet gripper wear and sensor sensitivity are not controlled periodically

## Open Risk / Follow-up
- Need to monitor pellet-gripper rubber wear condition
- Need to verify monthly pellet-gripper check is sustained
- Need to verify half-year replacement is implemented
- Need to monitor whether Sensor 4S26 sensitivity setting 8 remains effective
- Need ME confirmation on final affected panel quantity

## Evidence
- Attached issue slides showing:
  - overflow timeline
  - remained cull comparison (normal vs abnormal)
  - pellet gripper process flow
  - explanation of extra pellet drop and low sensor sensitivity
