---
id: INC-2023-05-22-WATERCLEAN22-DROP-C85SMALL-PANEL-EQDIW00022
date: 2023-05-22
time: "05:40"
station: Water Clean
machine: EQDIW00022
model: C8.5 Small
issue_type:
  - Process
  - Carrier
  - Handling
  - Water Clean
status: Root cause confirmed / Sensor detect top cover action defined
owner: EQ / PD / ME / PT
tags:
  - water-clean
  - waterclean22
  - drop-panel
  - missing-top-cover
  - carrier
  - c8.5-small
  - eqdiw00022
---

# Water clean #22 – Drop C8.5 Small panel issue

## Issue
- Issue: Drop C8.5 Small panel issue
- Model: C8.5 Small
- NG Q’ty: 01 panel
- Machine: Water clean #22
- Reference machine code used in this incident file: EQDIW00022
- Time: 05:40 AM, 22nd May 2023

## Symptom
- PD team found the C8.5 Small carrier came out of the Water clean machine without PCB panel at 05:40 AM.
- The dropped PCB was found on the conveyor at the output.
- One panel was broken / dropped.

## Root Cause Analysis
- EQ and PD checked CCTV and found:
  - there was a carrier with panel input into Water clean machine **without top cover** at 05:40 AM
- When the carrier with panel was cleaned by water and air in the Water clean machine:
  - panel was dropped out of the carrier

### Additional checks
1. Check loader, conveyor, and water clean machine during the happened issue time
   - no abnormal
2. Check the pusher position when pushing carrier out of magazine
   - the pusher contacted the center of carrier
   - the pusher did not impact the top cover of carrier
3. Co-work with PD and ME to check CCTV and confirm:
   - the carrier already did not have top cover before input to the water clean machine
   - during the issue time, machine had no alarm and no abnormal

## Root Cause
- The carrier entered the Water clean machine without top cover.
- Without the top cover, the panel was not held securely inside the carrier.
- During water and air cleaning, the unsecured panel dropped out of the carrier.

## Failure Mechanism
- The carrier top cover is required to fully cover the side gap and hold the panel securely during Water Clean process.
- If the carrier has no top cover, the panel retention condition becomes abnormal.
- Under water and air cleaning force inside the machine, the panel can drop out of the carrier.
- Because the machine originally had no sensor to confirm top cover presence, the carrier without top cover could still enter the machine and continue process.
- This caused the drop panel issue.

## Actions
1. Check loader, conveyor, and water clean machine during issue time
   - no abnormal
2. Check pusher position when pushing carrier out of magazine
   - pusher contacted center of carrier
   - did not impact top cover
3. Co-work with PD and ME to review CCTV
4. Stop Water clean #22 to find the dropped panel

## Next Action / Preventive Action
1. EQ contacts vendor to study how to install sensor to detect top cover
   - Checkpoint: 5/30

## Sensor Detect Top Cover Improvement Logic
- EQ checked SMT1 and SMT2 carrier design and confirmed there is a side space
- When top cover is installed, the top cover fully covers this space
- There is already a sensor to detect carrier and panel on the conveyor
- Plan:
  - set the detected position of this sensor to the position where the top cover fully covers the gap / space
- Expected control:
  - if carrier has no top cover, this sensor will not detect carrier + top cover correctly
  - machine will alarm and stop

## Current Status
- Root cause was confirmed by CCTV: carrier had no top cover before input.
- Machine itself had no abnormal alarm during the event.
- Preventive action was defined to install / modify sensor logic for top-cover detection.

## Impact
- Quality: 01 panel NG / dropped
- Production: machine had to stop for finding the dropped panel and verification
- Safety: not stated in the slide
- Repeat risk: high until top-cover detection control is implemented

## Open Risk / Follow-up
- Need PT / vendor support to complete sensor detect top cover modification
- Need to verify both SMT1 and SMT2 carriers can be detected correctly when top cover is installed
- Need to ensure machine alarms and stops if carrier has no top cover
- Need to monitor repeat issue before sensor modification is finished

## Evidence
- Slide 1 shows:
  - issue title
  - model C8.5 Small
  - NG Q’ty 01 panel
  - machine Water clean #22
  - time 05:40 AM, 22nd May 2023
  - CCTV conclusion that carrier entered machine without top cover
- Slide 2 shows:
  - top cover fully covers the carrier side gap
  - sensor detect top cover concept
  - if carrier has no top cover, machine alarm and stop
- Slide 3 shows:
  - SMT1 test without top cover → machine alarm and stop
  - SMT2 carrier is longer, sensor frame too short, need PT team support to modify sensor frame
  - temporary hand-move test for detection position
