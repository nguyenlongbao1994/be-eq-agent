---
id: INC-2023-03-16-MOLDING-C85SMALL-BOTTOM-SKIRTS-MOVE-ERROR-EQMLD00146
date: 2023-03-16
time: "03:00-04:10 AM"
station: Molding
machine: EQMLD00146
model: C8.5 Small
area: Bottom skirts
issue_type:
  - Mechanical
  - Pneumatic
  - Sensor
  - Control
status: Recovered / Monitoring
owner: EQ
tags:
  - molding
  - c8.5-small
  - bottom-skirts
  - move-error
  - cylinder
  - air-pressure
  - limit-sensor
  - shaft
---

# Molding C8.5 Small – Bottom Skirts Move Error

## Issue
- Machine: Molding EQMLD00146
- Model: C8.5 Small
- Time: 3:00–4:10 (16/03/2023)
- Machine alarm: Bottom skirts move error

## Symptom
- Machine showed bottom skirts move error.
- Bottom skirts could not move up normally.

## Root Cause
- The bottom skirts are controlled by a cylinder.
- The force of the cylinder was a little low.
- Because cylinder force was low, the cylinder shaft could not be pushed to the detected position of the limit sensor.
- As a result, the bottom skirts could not move up.

## Failure Mechanism
- Bottom-skirt movement depends on enough cylinder force to move the shaft until the limit sensor detects the correct position.
- When supply air / cylinder force was insufficient, the shaft could not reach the limit-sensor detect point.
- Because the signal condition was not achieved, bottom skirts could not move up and the machine reported bottom skirts move error.

## Actions
- Adjusted supply air valve on the cylinder to increase air pressure.
- After adjustment, cylinder force became stronger.
- The shaft could then move to the detected position of the sensor.
- Bottom skirts moved up normally.
- Machine recovered to normal condition from 04:10 AM (16/03/2023).
- EQ continued monitoring.

## Action Re-Check Cylinder
- Removed cylinder for maintenance and checked condition.
- Cleaned cylinder with WD-40.
- Cylinder condition was good and movement was smooth after maintenance.
- Manual test and auto test both showed normal machine operation with no sticking.
- No need to replace the cylinder with a new one.

## Current Status
- Air-pressure adjustment restored normal bottom-skirt movement.
- Cylinder re-check found no need for replacement.
- Machine recovered and continued running under EQ monitoring.

## Impact
- Quality: no NG quantity was stated in the slide
- Production: machine interruption during alarm and troubleshooting period
- Safety: not stated in the report
- Repeat risk: possible if air-pressure condition drifts again or cylinder movement degrades over time

## Open Risk / Follow-up
- Need to monitor stability of supply air pressure to the cylinder
- Need to confirm shaft continues reaching the limit-sensor detection position reliably
- Need to include this point in routine maintenance follow-up if repeat tendency appears

## Evidence
- Attached slides showing:
  - bottom skirts move error message
  - cylinder control area
  - supply-air valve adjustment
  - limit-sensor detection condition before and after
  - cylinder re-check note
