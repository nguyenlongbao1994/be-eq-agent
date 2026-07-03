---
id: INC-2026-01-11-SPT51-CHB43-TRANSMISSION-TIME-OUT-ALARM
date: 2026-01-11
time: "02:00-03:30"
station: Sputter
machine: SPT#51
model: C10.5 Small
issue_type:
  - Process
  - Mechanical
  - Laser tube
  - Cathode clamp
  - DC power
status: Recovered after part replacement / Vendor cleaning control required
owner: EQ / PD / Vendor
tags:
  - sputter
  - spt51
  - chb43
  - transmission-time-out
  - laser-tube
  - cathode-clamp
  - dc-power
  - c10.5-small
---

# SPT#51 – CHB43 Transmission Time Out Alarm

## Issue
- Machine: SPT#51
- Model: C10.5 Small
- Problem: Sensor error alarm / CHB43 Transmission Time Out Alarm
- Time: 02:00 AM, 11th Jan, 2026
- NG Qty: 1 tray

## Timeline
- Before issue:
  - machine run normally
- 11 Jan 02:00
  - machine alarm:
    - "CHB42-CHB43 Transmission Time Out"
- 11 Jan 02:10 ~ 03:30
  - EQ checked CHB42 and CHB43
  - EQ checked sensor and laser tube
  - laser tube error was identified
  - machine was stopped and opened
  - changed new laser tube
- 11 Jan 03:30
  - machine run normal
  - PD did FAI

## Symptom
- Machine alarmed CHB42-CHB43 Transmission Time Out.
- 1 tray was impacted.
- During inspection, laser output appeared weak.

## Analysis – Transmission Time Out Side
1. Check alarm:
   - Machine alarm:
     - ALM 618-619: CHB42-CHB43 Transmission Time Out
2. Visual inspection:
   - laser is weak
3. Check laser tube:
   - laser tube error
4. Stop machine:
   - take out CHB42
5. Change new laser tube

### Cause from slide
- The shield surface roughness was out of specification.
- Because the shield surface roughness was not good, it became prone to peeling.
- Peeled copper layer adhered to the tip of the laser tube.

## Analysis – CHB43 / DC Power Side
1. Check alarm:
   - Machine alarm:
     - ALM 2613: CHB43 Transmission Time Out
2. Measurement:
   - cathode 8 → short circuit → error
3. Manual operate DC 8 power:
   - error
4. Stop machine and take out cathode 8:
   - peeling was detected on the cathode clamp
5. Clean chamber and replace all cathode clamps

### Cause from slide
- Cathode clamp surface roughness was not good.
- Poor surface condition made peeling easy.
- Peeling led to DC power alarm.

## Failure Mechanism
- The issue set had two linked physical failure paths inside sputter:
  1. **Laser-tube path**
     - shield surface roughness out of spec
     - copper peeling adhered to the laser-tube tip
     - laser became weak
     - CHB42-CHB43 transmission timeout alarm occurred
  2. **Cathode / power path**
     - cathode clamp surface roughness not good
     - peeling occurred on clamp
     - cathode #8 short circuit / DC power abnormality occurred
     - CHB43 transmission timeout / DC power alarm was triggered
- Both paths point to surface-quality / peeling-related contamination and conductive abnormality inside the system.

## Actions
1. Visual inspection of weak laser
2. Take out CHB42 and check laser tube
3. Change new laser tube and perform visual inspection
4. Run machine and FAI
5. Rework 1 SPT tray
6. Check cathode 8 short circuit / DC 8 power
7. Stop machine, take out cathode 8, detect peeling on cathode clamp
8. Clean chamber and replace all cathode clamps
9. Change cleaning vendor after sending part to Hanton vendor and require surface roughness reaching 20–30 micron

## Current Status
- New laser tube was installed
- Chamber was cleaned
- Cathode clamps were replaced
- Machine returned to normal run at 03:30
- PD completed FAI after recovery

## Impact
- Quality: 1 tray affected
- Production: machine stop from 02:00 until recovery at 03:30
- Safety: not stated in the slide
- Repeat risk: possible if surface roughness control and cleaning-vendor quality are not corrected

## Open Risk / Follow-up
- Need to verify surface roughness of the related shield / clamp parts meets 20–30 micron target after vendor cleaning
- Need to monitor recurrence of copper peeling on laser-tube tip
- Need to monitor recurrence of cathode-clamp peeling and DC power alarm
- Need to verify normal FAI / production stability after part replacement

## Evidence
- Slide 1: issue summary and timeline for CHB42-CHB43 Transmission Time Out alarm
- Slide 2: analysis showing weak laser, laser-tube error, peeling copper adhered to laser-tube tip, and action to change laser tube
- Slide 3: analysis showing cathode #8 short circuit / DC power alarm, peeling on cathode clamp, and action to clean chamber and replace cathode clamps
