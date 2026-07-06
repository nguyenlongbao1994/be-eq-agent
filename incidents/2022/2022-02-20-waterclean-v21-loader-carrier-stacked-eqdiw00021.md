---
id: INC-2022-02-20-WATERCLEAN-V21-LOADER-CARRIER-STACKED-EQDIW00021
date: 2022-02-20
time: "15:00-15:35"
station: Water Clean
machine: EQDIW00021
area: Loader input SMT2
model: C6.5-X18189Big
issue_type:
  - Sensor
  - Transfer
  - Loader
  - Carrier stacking
status: Recovered after sensor adjustment / Weekly sensor check added
owner: EQ
tags:
  - water-clean
  - v21
  - loader
  - carrier-stacked
  - eqdiw00021
  - sensor
---

# V21 Loader Water Cleaning machine – Carrier stacked

## Issue
- Issue: Carrier stacked
- Model: C6.5-X18189Big
- Machine: Loader input SMT2 EQDIW00021
- Quantity:
  - 2 pcs Scrap
  - 6 pcs Rework
- Time: 15:00 PM
- Station: Water Cleaning machine

## Symptom
- Carrier stacked at loader input of the water cleaning machine.
- The next carrier was brought out while the previous carrier had not been correctly detected as out.

## Root Cause
- The magazine output sensor failed to detect the carrier out.
- Because the machine did not detect that the first carrier had already reached the output condition, the next carrier was brought out by the machine.
- This created carrier stacking at loader input.

## Failure Mechanism
- Loader transfer logic depends on the magazine output sensor to confirm that a carrier has cleared the output position.
- When the output sensor did not detect the carrier correctly, machine logic continued to release the next carrier.
- Since the previous carrier was still effectively in the transfer/output zone, the next carrier entered the same area.
- This caused stacked carriers and created scrap / rework impact.

## Actions

### Short action
1. Adjust light threshold on the sensor
2. Adjust carrier detection distance on the sensor
3. Reinstall sensor position
   - After repair the machine worked normally at 15:35 PM
4. Check sensor status in water clean EQDIW00022
   - Normal

### Long action
1. Check function and sensor status every week
   - before monthly sensor check

## Current Status
- Sensor threshold / detect distance were adjusted
- Sensor position was reinstalled
- Machine worked normally again after 15:35 PM
- Weekly sensor status check was added

## Impact
- Quality:
  - 2 pcs scrap
  - 6 pcs rework
- Production: temporary interruption at loader input
- Safety: not stated in the slide
- Repeat risk: possible if sensor condition drifts again and is not monitored

## Open Risk / Follow-up
- Need to keep weekly sensor function and status check
- Need to monitor carrier-out detection stability at loader input
- Need to verify no repeat carrier stacking after recovery

## Evidence
- Slide title: V21 Loader Water Cleaning machine
- Issue section states:
  - Carrier stacked
  - Model: C6.5-X18189Big
  - Machine: Loader input SMT2 EQDIW00021
  - Q’ty: 2 pcs Scrap + 6 pcs Rework
  - Time: 15:00pm
- Cause section states:
  - magazine output sensor failed to detect the carrier out
  - next carrier was brought out by the machine
- Action section states:
  - adjust light threshold
  - adjust carrier detection distance
  - reinstall sensor position
  - machine can work normal after repair (15:35pm)
  - check weekly before monthly sensor check
