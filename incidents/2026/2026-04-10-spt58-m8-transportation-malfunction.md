---
id: INC-2026-04-10-SPT58-M8-TRANSPORTATION-MALFUNCTION
date: 2026-04-10
time: "22:00-23:30"
station: Sputter
machine: Sputter#58
model: C10.5 Small
issue_type:
  - Mechanical
  - Transport
  - Motor
  - Belt
status: Recovered after motor replacement / PM control required
owner: EQ
tags:
  - sputter
  - spt58
  - m8
  - transport
  - belt-motor
---

# SPT#58 – M8 Transportation Malfunction

## Issue
- Machine: Sputter#58
- Model: C10.5 Small
- Problem: Belt Motor error / M8 Transportation malfunction
- Alarm: ALM2670 M8 TRANSPORTATION MALFUNCT
- Time: 22:00 PM, 10 Apr, 2026
- NG Qty: 1 tray (rework → OK)

## Timeline
- Before issue:
  - Machine run normally
- 10 Apr 22:00
  - Machine alarm:
    - ALM2670 M8 TRANSPORTATION MALFUNCT
- 22:00 ~ 23:30
  - EQ manual check inner transport M8
  - Found stuck tray
  - Stop machine
  - Check around motor → Belt motor error detected
- 10 Apr 23:30
  - Replace belt motor
  - Machine run normal
  - PD do FAI OK

## Symptom
- Machine alarmed M8 transport error.
- Tray stuck inside transportation path.
- Belt motor could not drive transport.

## Root Cause
- Belt motor NG → motor jam occurred.
- Root cause from slide:
  - Machine operated continuously → belt reached service limit.
- Continuous load increased wear → led to mechanical jam.

## Failure Mechanism
- Belt-driven transport system operates continuously for tray movement.
- Over time, motor and belt components degrade.
- When wear exceeds tolerance:
  - Motor torque insufficient
  - Friction increases
  - Transport stops → tray stuck
- Control system detects no movement → triggers M8 transport alarm.

## Actions
1. Check alarm and transport path
2. Manual check inner transport M8
3. Identify stuck tray
4. Inspect motor → belt motor NG
5. Replace belt motor
6. Run machine
7. Perform FAI → OK

## Preventive Action
1. Define belt motor replacement cycle (e.g. every 3 months as suggested)
2. Monitor motor load / abnormal noise
3. Check spare belt availability
4. Add inspection item during PM

## Current Status
- Belt motor replaced
- Machine recovered at 23:30
- PD completed FAI
- Production resumed normally

## Impact
- Quality: 1 tray affected → rework OK
- Production: temporary stop
- Safety: low
- Repeat risk: high if PM not controlled

## Open Risk / Follow-up
- Need to define clear PM interval for belt motor
- Need to prepare spare parts
- Need monitor repeat M8 transport alarm

## Evidence
- Slide shows alarm ALM2670 M8 TRANSPORTATION MALFUNCT
- Manual check found stuck tray
- Motor inspection identified belt motor NG
- Replacement completed → machine normal
