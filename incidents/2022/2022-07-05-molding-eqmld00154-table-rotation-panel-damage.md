---
id: INC-2022-07-05-MOLDING-EQMLD00154-TABLE-ROTATION-DAMAGE
date: 2022-07-05
time: "13h50"
station: Molding
machine: EQMLD00154
area: Table rotation
issue_type:
  - Mechanical
  - Sensor
  - Transfer
  - Control
status: Recovered / Monitoring
owner: EQ
tags:
  - molding
  - panel-damage
  - table-rotation
  - sensor-1S12
  - leadframe-handle
  - re-initial
---

# Molding Damage Panel Analysis – EQMLD00154 Table Rotation

## Background
- Time: 13h50 (07/05)
- Station: Molding EQMLD00154 – Table rotation
- Error description: Table rotation move error => 1 panel is damage
- Failure quantity: 1 panel (23 SIP)

## Symptom
- Table rotation movement error occurred.
- One panel was damaged during the abnormal movement.

## Root Cause
- Root cause: Table rotation move error
- Signal of sensor 1S12 (detect panel at leadframe handle) was wrong.
- Table rotation moved while the panel was still hanging out of the leadframe handle.
- The panel was impacted by table rotation.

## Failure Mechanism
- Sensor 1S12 failed to detect the panel condition correctly at the leadframe handle.
- Because the sensor signal was wrong, the machine allowed table rotation to move while the panel was not yet fully released / positioned correctly.
- The still-hanging panel was then hit by the moving table rotation mechanism, resulting in panel damage.

## Actions
- EQ checked signal of sensor 1S12.
- Replaced sensor 1S12 with a new sensor.
- Re-initialized the machine.
- Machine recovered to normal condition from 15h00.

## Current Status
- Sensor was replaced.
- Machine was re-initialized.
- Machine could recover normal production from 15h00.
- Current status: recovered, continue monitoring for repeat risk.

## Impact
- Quality: 1 panel damaged
- Production: machine interruption until sensor replacement and re-initial
- Safety: not stated in the report
- Repeat risk: present until stable sensor detection is confirmed

## Open Risk / Follow-up
- Need to confirm stable panel detection at leadframe handle
- Need to monitor whether table rotation can repeat abnormal movement after sensor replacement

## Evidence
- Attached analysis report image showing:
  - damaged panel
  - table rotation / leadframe handle area
  - sensor-related inspection point
