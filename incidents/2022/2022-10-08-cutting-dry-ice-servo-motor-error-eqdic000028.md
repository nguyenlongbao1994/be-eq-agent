---
id: INC-2022-10-08-CUTTING-DRY-ICE-SERVO-MOTOR-ERROR-EQDIC000028
date: 2022-10-08
station: Cutting Dry Ice
machine: EQDIC000028
model: C8.5 Small
issue_type:
  - Mechanical
  - Servo
  - Conveyor
  - Motion axis
status: Recovered after cleaning, greasing, and reset
owner: EQ
tags:
  - cutting-dry-ice
  - servo-motor-error
  - conveyor
  - width-adjust
  - motion-axis
  - eqdic000028
  - c8.5-small
---

# Cutting Dry Ice #28 – Servo Motor Error

## Issue
- Machine: Cutting Dry Ice #28
- Model: C8.5 Small
- Problem: Servo Motor Error
- Time: 23:00 at 08/10/2022 ~ 01:00 at 09/10/2022
- NG qty: 0 EA

## Symptom
- Servo motor alarm happened while machine was running.
- Conveyor could not move out to adjust conveyor width.

## Root Cause
- Checked conveyor status.
- Found the conveyor loading was stuck at the outside position.

## Failure Mechanism
- Conveyor width-adjust movement depends on smooth motion at the conveyor axis.
- When the conveyor loading became stuck at the outside position, the axis could not move normally.
- This movement abnormality caused servo motor alarm / MCB error during width-adjust function.

## Actions
1. EQ stopped machine and turned off power.
2. Cleaned dust at the motion axis.
3. Applied grease on the conveyor axis.
4. Turned on power and reset Servo Motor MCB #120.
5. Machine recovered and worked normally from 01:00 AM (09/10/2022).

## Current Status
- Machine recovered after axis cleaning, greasing, and servo reset.
- Current status: recovered.

## Impact
- Quality: 0 EA NG reported
- Production: temporary interruption from 23:00 to 01:00
- Safety: not stated in the slide
- Repeat risk: possible if dust accumulates again on motion axis and periodic lubrication is not maintained

## Open Risk / Follow-up
- Need to monitor conveyor width-adjust movement after restart
- Need to maintain cleaning and lubrication condition of the motion axis
- Need to watch if Servo Motor MCB #120 error repeats during conveyor movement

## Evidence
- Issue report slide titled "Cutting Dry Ice #28 issue Report"
- Analysis section stating conveyor could not move out to adjust width conveyor
- Root cause note stating conveyor loading was stuck at outside position
- Action section stating dust cleaning, grease application, and reset Servo Motor MCB #120
