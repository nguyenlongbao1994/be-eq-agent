---
id: INC-2023-03-09-CUTTING-DRY-ICE-SIP-DAMAGED-EQDIC000028
date: 2023-03-09
station: Cutting Dry Ice
machine: EQDIC000028
model: C8.5 Small
issue_type:
  - Sensor
  - Conveyor
  - Detection
  - Handling
status: Vendor action in progress / Software improvement required
owner: EQ / Vendor
tags:
  - cutting-dry-ice
  - sip-damaged
  - broken-sip
  - carrier
  - conveyor
  - sensor-i0-24
  - sensor-i0-27
  - eqdic000028
---

# Cutting Dry Ice #28 – SIP damaged

## Issue
- Machine: Cutting Dry Ice #28
- Model: C8.5 Small
- Problem: Broken SIP
- Issue time shown in slide: 13:30 (03/08/2023)
- File date key used in this incident: 2023/03/09
- NG qty: 4 SIPs

## Timeline
- 03/08/2023 13:30
  - PD highlighted VI085 error code at FVI
- 03/08/2023 15:31
  - Analysis / simulation direction continued
- 03/08/2023 16:45
  - ME and EQ checked actual condition of machines
- 03/08/2023 18:46
  - EQ checked actual condition of machine again
- 03/08/2023 19:08
  - Made tracking data every 2 hours
- Vendor improvement checkpoint shown in slide:
  - 13th March

## Symptom
- Broken SIP happened at Cutting Dry Ice #28.
- 4 SIPs were damaged.
- Carrier transfer behavior became abnormal between carrier No.7 and carrier No.8.

## Root Cause
- Sensor `i0-24` (confirm carrier position) could not detect carrier No.7.
- Conveyor did not work to transfer carrier No.7 after carrier No.7 had already moved out of magazine.
- Magazine continued moving down and pushed carrier No.8 to the next step.
- Carrier No.7 then impacted the conveyor / carrier No.8.
- Result: SIP fell down and was damaged.

## Failure Mechanism
- Sensor `i0-24` is used to confirm carrier position.
- Detection point of sensor `i0-24` is through the hole on the carrier.
- During simulation, when using X-out SIP and manually pushing carrier out of the magazine with conveyor stopped, sensor `i0-24` could not detect the carrier correctly.
- Because the sensor signal was unstable / not detected, the conveyor did not receive the signal to run while the pusher pushed out carrier No.7.
- Magazine continued moving down and the pusher then pushed carrier No.8.
- Carrier No.7 collided with carrier No.8 and caused SIP to fall and become damaged.

## Analysis Notes
- Check log file and CCTV:
  - machine had no abnormal general alarm during issue happen
  - no abnormal operation from operator and engineer was noted
- Simulation confirmed the issue path by reproducing the carrier / sensor condition.

## Actions
1. Add more cushions into pusher to increase pusher length by approximately 9 mm
2. Increase distance between detection point of sensor `i0-24` and carrier hole
3. Check Cutting Dry Ice #27 (Big) machine for the same situation
4. Add more cushions to pusher on machine #27 as well
5. Work with Intelume vendor onsite to find the reason why conveyor did not work at the time of issue
6. Vendor action:
   - Increase sensitivity setting of sensor `i0-24` from 50 to 60
   - Provide warranty replacement for 2 new sensors `i0-24`
   - Improve software by adding more function to control conveyor with sensor `i0-27`
   - In case sensor `i0-24` is unstable, sensor `i0-27` will activate conveyor run

## Current Status
- Vendor and EQ completed re-simulation.
- Current conclusion in slide:
  - sensor `i0-24` unstable
  - sensor `i0-24` did not send signal to run conveyor during pusher push-out of carrier No.7 and No.8
  - issue therefore happened
- Vendor corrective action and software improvement were in progress.

## Impact
- Quality: 4 SIP damaged
- Production: carrier transfer abnormality / interruption occurred
- Safety: not stated in the slide
- Repeat risk: high until sensor stability and software backup logic with sensor `i0-27` are confirmed

## Open Risk / Follow-up
- Need to confirm sensor `i0-24` remains stable after increasing sensitivity
- Need to verify vendor replacement of 2 sensors `i0-24`
- Need to validate software improvement using sensor `i0-27` as backup conveyor trigger
- Need to monitor recurrence of carrier No.7 / No.8 collision during production

## Evidence
- Slide showing issue summary: machine, model, broken SIP, NG qty 4 SIPs
- Slide showing simulation and detection-point analysis on sensor `i0-24`
- Slide showing cause and action for adding pusher cushions and changing sensor relationship to carrier hole
- Slide showing vendor conclusion that sensor `i0-24` unstable and software backup with sensor `i0-27`
