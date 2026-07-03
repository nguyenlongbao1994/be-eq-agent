
---
id: INC-2021-11-04-MOLDING-EQMLD00147-TABLE-ROTATION-DAMAGE
date: 2021-11-04
time: "03h50"
station: Molding
machine: EQMLD00147
area: Table rotation
issue_type:
  - Mechanical
  - Sensor
  - Transfer
  - Control
status: Monitoring
owner: Loki Gener
tags:
  - molding
  - panel-damage
  - table-rotation
  - sensor
  - leadframe-handle
  - cassette-handle
---

# Molding Damage Panel Analysis – EQMLD00147 Table Rotation

## Background
- Time: 03h50 (11/04)
- Station: Molding EQMLD00147 – Table rotation
- Error description: Table rotation move error => 1 panel is damage
- Failure quantity: 1 panel (17 SIP)

## Symptom
- Table rotation movement error occurred.
- One panel was damaged during the abnormal movement.

## Root Cause
- Root cause: Table rotation move error
- Machine alarm: "Lift not in position" because magazine was set in the opposite direction.
- EQ solved the initial machine issue and resumed the machine, but table rotation of the leadframe handle still had movement error.
- Sensor could not detect the panel.
- Table rotation movement error then caused panel damage.

## Failure Mechanism
- Incorrect magazine direction caused the machine to report "Lift not in position."
- After the initial issue was solved and the machine resumed, the table rotation movement at the leadframe handle still had abnormal movement.
- The sensor failed to detect the panel correctly.
- Because panel detection failed, table rotation moved abnormally and damaged the panel.

## Actions
- Checked table rotation motor
- Checked stopper at Ficovision table
- Checked pusher of cassette handle
- EQ checked signal of sensor 1S12 for panel detection at vision table of cassette handle
- Replaced the sensor with a new sensor
- Re-initialized the machine
- Continued monitoring

## Current Status
- Sensor was replaced
- Machine was re-initialized
- Current action direction: keep monitoring after recovery

## Impact
- Quality: 1 panel damaged
- Production: short interruption due to movement abnormal and sensor replacement
- Safety: not stated in the report
- Repeat risk: present until monitoring confirms stable detection and normal table rotation

## Evidence
- Attached analysis report image showing damaged panel position, table rotation area, and machine-side check photos
``
