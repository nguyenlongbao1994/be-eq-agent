---
id: INC-2026-03-15-MOLDING-LEFT-LEADFRAME-PUSHER-NOT-IN-POSITION-EQMLD00146
date: 2026-03-15
time: "05:28"
station: Molding
machine: EQMLD00146
model: C10.5 Small
issue_type:
  - Mechanical
  - Control
  - Motor
  - Driver
status: Recovered after motor replacement / Monitoring
owner: EQ / ME / QC
tags:
  - molding
  - c10.5-small
  - left-leadframe-pusher
  - not-in-position
  - motor
  - driver
  - timeout
  - eqmld00146
---

# Molding 146 machine – Left lead-frame pusher not in position

## Issue
- Issue description: Left lead-frame pusher not in position
- Model: C10.5 Small
- Q’ty: 10 panel (Q-time)
- Machine: EQMLD00146
- Time: 05:28 (15/03/2026)

## Timeline
- 14/03 20:00 → Big clean
- 14/03 23:12 → FAI OK
- 15/03 05:28 → Machine alarm:
  - Left lead-frame pusher not in position
  - Cmd=Move Abs Arg=17 Err=TimeOut
- 15/03 09:00 → EQ checked machine:
  - Changed driver control of left pusher
  - Changed motor of left pusher
- 15/03 12:00 → Completed dry-run test
  - Double confirmed with ME and QC

## Symptom
- Machine alarmed: Left lead-frame pusher not in position.
- Left pusher could not move to the expected position within timeout condition.
- 10 panels became Q-time affected.

## Root Cause Analysis
### 1. Check mold chase
- Bottom mold: normal
- Top mold: normal
- Area inside mold chase: normal

### 2. Check profile at the shot when issue happened
- Transfer pressure spec: 6.5–11 MPa
- Actual transfer pressure: 7.0 MPa → OK
- Transfer clamp force spec: 50–60 Ton
- Actual transfer clamp force: 55.1 Ton → OK
- Trend of pressure and clamp force: no abnormality → Normal

### 3. Check and change driver control of left pusher
- Changed T121 driver
- After changing T121 driver, dry-run test by FR4 still showed the same alarm:
  - "Left lead-frame pusher not in position"

### 4. Check and change motor of left pusher
- Replaced the motor of left pusher
- After changing pusher motor, dry-run test by FR4 for 3 hours:
  - machine ran normal
  - alarm did not occur again

## Root Cause
- Mold chase condition was normal.
- Transfer pressure and clamp-force profile were normal.
- Driver replacement did not remove the alarm.
- The left-pusher motor was the actual failure source because alarm disappeared only after motor replacement.

## Failure Mechanism
- The pusher-position timeout alarm means the left lead-frame pusher could not reach commanded position in time.
- Since mold chase, transfer pressure, and clamp force were normal, the issue did not originate from mold-side blockage or transfer abnormality.
- Driver replacement did not solve the issue, which indicates the control signal path alone was not the real source.
- After motor replacement, dry-run was stable for 3 hours with no repeated alarm.
- Therefore, the most consistent mechanism is degraded or unstable pusher motor performance, causing left pusher motion failure and timeout.

## Actions
1. Change the motor of left pusher
2. Keep monitoring machine condition after recovery
3. Order spare part to prepare for similar case in the future

## Current Status
- Machine recovered after replacing the motor of left pusher
- Dry-run by FR4 for 3 hours was normal
- Alarm did not recur during verification
