---
id: INC-2022-04-24-UNDERFILL-DISPENSE-CAN-CONNECTION-ERROR-136
date: 2022-04-24
time: "08:46-16:30"
station: Underfill
machine: 136# Dispense machine
model_line: Big model line
issue_type:
  - Control
  - Communication
  - Board
  - CAN
status: Recovered after SDHC board replacement / Yearly PM item added
owner: EQ / Leo
tags:
  - underfill
  - dispense
  - can-error
  - heater1
  - fluidmove
  - sdhc
  - pwa
  - machine136
---

# Underfill-Dispense CAN connection error issue

## Issue
- Station: Underfill – 136# Dispense machine
- Line: Underfill Big-model
- Register date key: 2022/04/24
- Issue time shown in slide: 8:46 AM, 23/04/2022
- Error description: CAN connection error
- Impact: delayed big model MP plan
- WIP: 2k

## Timeline
- Before 8:45 AM → machine running normal
- 8:46 AM → machine had CAN connection errors
- 16:30 → EQ finished changing PWA, SDHC V6 #2 board
- After 16:30 → machine running normal

## Symptom
- CAN communication error happened on the dispense machine.
- The machine could not receive CAN feedback message in the allotted time.
- Error affected Heater 1 device initialization / connection.
- Big-model MP plan was delayed.

## Root Cause
- Heater 1 device hardware check: no abnormal
- Fluidmove software and Windows 7 recovery check: no abnormal
- Logfile showed machine could not connect to CAN
- PWA SDHC V6 #2 board had error
- After changing new SDHC V6 #2 board and re-configuring parameters, machine returned to normal
- Therefore the issue root cause was abnormal PWA SDHC V6 #2 board causing CAN connection failure

## Failure Mechanism
- The dispense machine relies on CAN communication between control system and Heater 1 related device.
- The machine log indicated expected CAN reply messages were not received within the allotted time.
- Because the PWA SDHC V6 #2 board was abnormal, CAN communication could not be maintained correctly.
- As a result, Heater 1 device initialization / communication failed and the machine reported CAN connection error.
- Once the SDHC board was replaced and parameters re-configured, communication recovered and the machine ran normally again.

## Actions
1. Checked HEATER 1 device hardware → no abnormal
2. Recovered Fluidmove software and Windows 7 → no abnormal
3. Checked logfile → machine could not connect to CAN
4. Checked PWA SDHC V6 #2 board errors
5. Changed new PWA SDHC V6 #2 board
6. Re-configured parameter
7. Verified machine returned to normal

## Result
### Short-term
- After changing PWA, SDHC V6 #2 machine running normal
- Continue monitoring in line all time to reduce repeat issue

### Long-term
- Add 1 item:
  - "check all of SDHC boards status"
  into yearly maintenance

## Current Status
- Machine recovered after board replacement and parameter re-configuration
- Normal run confirmed after 16:30
- Current status: recovered, continue monitoring

## Impact
- Quality: no SIP fail quantity stated in the slide
- Production: delayed big model MP plan
- WIP impact: 2k
- Safety: not stated in the slide
- Repeat risk: possible if SDHC board health is not checked periodically

## Open Risk / Follow-up
- Need to keep monitoring CAN communication stability
- Need yearly maintenance item for all SDHC board status
- Need to watch for repeated CAN timeout / Heater 1 initialization fault

## Evidence
- Slide title: Underfill-Dispense CAN connection error issue
- Issue section shows:
  - line = Underfill Big-model
  - time = 8:46 PM / 23/04/2022
  - WIP = 2k
- Phenomenon message shows CAN did not receive feedback in allotted time
- Action section confirms SDHC V6 #2 board replacement and recovery
