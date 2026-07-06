---
id: INC-2022-09-06-WATERCLEAN-V22-LOADER-CARRIER-STACKED-EQDIW00022
date: 2022-09-06
time: "03:10-04:00"
station: Water Clean
machine: EQDIW00022
area: Loader input SMT2
model: C8.5 Big
issue_type:
  - Sensor
  - Transfer
  - Loader
  - Carrier stacking
status: Recovered after sensor sensitivity adjustment / Second sensor preventive action defined
owner: EQ
tags:
  - water-clean
  - v22
  - loader
  - carrier-stacked
  - eqdiw00022
  - sensor
---

# V22 Loader Water Cleaning machine – Carrier stacked

## Issue
- Issue: Carrier stacked
- Model: C8.5 Big
- Machine: Loader input SMT2 EQDIW00022
- NG Q’ty: ~10 pcs
- Time: 03:10 AM
- Station: Water Cleaning machine

## Symptom
- Carrier stacked at loader input of the water cleaning machine.
- The next carrier was pushed out by the machine while the previous carrier had not been correctly detected as out.

## Root Cause
- The output sensor failed to detect the carrier out.
- Because the machine did not detect that the previous carrier had already reached the output condition, the next carrier was pushed out by the machine.
- This created carrier stacking at the loader input.

## Failure Mechanism
- Loader transfer logic depends on the output sensor to confirm that a carrier has cleared the output position.
- When the output sensor signal became unstable, the machine did not receive a reliable “carrier out” status.
- Because of that, the next carrier was pushed out while the previous carrier was still effectively occupying the same transfer / output area.
- This caused carrier stacking and generated NG quantity.

## Actions

### Short action
1. Check the output sensor and carrier detection sensor on the conveyor
2. Found that the sensor signal was not stable
3. Adjust sensor threshold sensitivity
4. After repairing, the machine worked normally from 04:00 AM
5. Check sensor status in water clean EQDIW00022
   - Normal

### Long action
1. Install one more sensor
   - If the first sensor cannot detect the carrier, the second sensor will detect the carrier and send signal to start the conveyor
   - Purpose: prevent carrier stacked issue

## Current Status
- Sensor threshold sensitivity was adjusted.
- Machine worked normally again from 04:00 AM.
- Long-term action to install an additional sensor was defined.

## Impact
- Quality: ~10 pcs NG
- Production: temporary interruption at loader input
- Safety: not stated in the slide
- Repeat risk: still possible until the second-sensor preventive action is implemented

## Open Risk / Follow-up
- Need to install the second sensor as preventive control
- Need to monitor output-sensor signal stability at loader input
- Need to verify no repeat carrier stacking after second-sensor implementation

## Evidence
- Slide title: V22 Loader Water Cleaning machine
- Issue section states:
  - Carrier stacked
  - Model: C8.5 big
  - Machine: Loader input SMT2 EQDIW00022
  - NG Q’ty: ~10 pcs
  - Time: 03:10am
- Cause section states:
  - output sensor failed to detect the carrier
  - next carrier was pushed out by the machine
- Action section states:
  - sensor signal was not stable
  - adjusted sensor threshold sensitivity
  - machine worked normally from 04:00am
  - planned to install a second sensor
