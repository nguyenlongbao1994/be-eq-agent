---
id: INC-2022-10-27-CUTTING-DRY-ICE-SIP-DAMAGED-EQDIC000028
date: 2022-10-27
time: "09:44-10:30"
station: Cutting Dry Ice
machine: EQDIC000028
model: C8.5 Small
issue_type:
  - Sensor
  - Human
  - Detection
  - Carrier handling
status: Recovered after sensor cleaning / OCAP & PM update required
owner: EQ / PD
tags:
  - cutting-dry-ice
  - sip-damaged
  - alm393
  - alm394
  - board-detection
  - clean-stage
  - double-carrier
  - eqdic000028
---

# Cutting Dry Ice #28 – SIP damaged

## Issue
- Machine: Cutting Dry Ice #28
- Model: C8.5 Small
- Problem: ALM393: CleanStageBoardDetectionError
- Time: 09:44 (10/27/2022)
- NG qty: 05 SIPs

## Timeline
- 10/27/2022 09:44
  - Machine alarm: ALM393: CleanStageBoardDetectionError
- 10/27/2022 09:45
  - PD reset alarm
  - PD did not check actual status at clean area
- 10/27/2022 09:46
  - PD restarted machine
  - Machine alarm: ALM394: CleanStage Vacuum Detection Error
- 10/27/2022 09:55
  - PD called EQ
  - EQ found 2 carriers on the clean table and some broken SIP
- 10/27/2022 09:56
  - Handling issue on original machine and running test with X-out SIP / carriers
- 10/27/2022 10:30
  - Machine returned OK for PD
  - Machine could produce normally

## Symptom
- Machine first alarmed ALM393: CleanStageBoardDetectionError.
- PD reset alarm without checking the actual clean-area condition.
- After restart, machine alarmed ALM394: CleanStage Vacuum Detection Error.
- EQ then found 2 carriers on the clean table and some broken SIP.
- Total damaged quantity: 05 SIPs.

## Root Cause
- The board-detection sensor was dusty and could not detect the carrier correctly.
- Because the sensor did not detect carrier correctly, alarm was triggered.
- PD reset the alarm and continued running without checking actual status.
- One carrier still remained in the clean area.
- This created double-carrier condition.
- Double carrier led to SIP damage.

## Failure Mechanism
- The clean-stage board-detection sensor is used to confirm carrier presence/clearance in the clean area.
- Dust contamination reduced its detection capability.
- The alarm was a valid indication that the machine state was abnormal.
- Because PD reset the alarm without checking the actual condition, one carrier remained in the clean area.
- When machine resumed, another carrier entered / overlapped, creating double-carrier condition on the clean table.
- The double-carrier condition physically damaged SIP.

## Actions
1. Clean sensor
2. Adjust sensor sensitivity from 400 to 600
3. Run test with X-out carriers
4. Verify machine can run normally
5. Add item:
   - "Clean and check boat detection sensors"
   into weekly maintenance check sheet
6. Make OCAP and add alarm list for EQ
7. Train PD to follow OCAP

## Current Status
- Sensor was cleaned
- Sensor sensitivity was adjusted from 400 to 600
- Running test with X-out carriers was completed
- Machine could produce normally at 10:30
- Preventive actions were extended to PM checklist, OCAP, and alarm-list update

## Impact
- Quality: 05 SIPs damaged
- Production: short interruption until handling issue was found and sensor was corrected
- Safety: not stated in the slide
- Repeat risk: high if clean-stage sensor is not cleaned regularly or if alarm reset is done without actual-status check

## Open Risk / Follow-up
- Need to ensure weekly PM includes clean/check of boat-detection sensor
- Need PD to follow OCAP before resetting related alarms
- Need EQ to maintain updated alarm list for this station
- Need to monitor recurrence of ALM393 / ALM394 after sensitivity adjustment

## Evidence
- Slide 1: issue summary and timeline from 09:44 to 10:30
- Slide 2: root-cause note stating dusty sensor and double carrier
- Slide 2: action note for sensor cleaning and sensitivity change (400 → 600)
- Slide 3: OCAP creation and alarm-list addition for EQ
