---
id: INC-2023-12-21-MOLDING-154-EAP-SYSTEM-ISSUE-EQMLD000154
date: 2023-12-21
time: "12:05 PM"
station: Molding
machine: EQMLD000154
model: C8.5 Big
issue_type:
  - IT
  - Detection
  - Control
  - Human
status: Recovered / Preventive action added
owner: EQ
tags:
  - molding
  - eap
  - fico-vision
  - barcode
  - panel-sn
  - ttt-file
  - machine154
  - c8.5-big
---

# Molding #154 EAP System Issue – EQMLD000154

## Issue
- Issue description: Fico vision turn off, machine cannot run by EAP
- Model: C8.5 Big
- Quantity: N/A
- Machine: EQMLD000154
- Time: 12:05 PM (12/21/2023)

## Timeline
- 04:30 AM → EQ turned off Fico vision to run dry-run mode with FR4
- 06:30 AM → Dry-run finished, but EQ forgot to turn Fico vision on again
- 08:30 AM → Big cleaning process
- 12:14 PM → Run FAI and machine alarm:
  - FAI 2 (No SN)
  - Machine sent out NG data to EAP
  - Machine could not run
- 05:30 PM → ZJ and HPH EQ checked the machine together and found the problem: Fico vision was turned off

## Symptom
- Machine could not run by EAP.
- FAI alarm was related to missing serial-number information.
- The machine output data to EAP had missing panel SN.

## Root Cause
- Fico vision was turned off.
- Because Fico vision was off, the machine did not scan barcode.
- The output `.ttt` file therefore missed panel SN information.
- EAP system did not receive correct NG file / complete panel-SN content.
- As a result, the machine could not continue running by EAP.

## Failure Mechanism
- Fico vision is required for barcode reading and serial-number acquisition.
- When Fico vision was left OFF after dry-run, barcode scan did not happen during normal production flow.
- Because barcode / panel-SN data was not captured, the `.ttt` output file contained missing panel SN.
- EAP processing depends on valid product data from the machine output.
- Once panel-SN information was missing, EAP could not process the machine data correctly, and the machine could not continue run control through EAP.

## Supporting Note from Report
- The configuration screenshot indicates:
  - Value = 0 → Fico vision is turn on
  - Value = 1 → Fico vision is turn off

## Actions
- Turned on Fico vision again to continue run.
- Added training requirement for all EQ members:
  1. Must return all machine settings after finishing run test.
  2. Engineers must hand over detailed shift work content to the next shift, especially machine-related problems and abnormalities that occurred during the shift.

## Current Status
- Fico vision was turned back on.
- Machine was able to continue running again after recovery.
- Preventive action was expanded to EQ training and shift handover improvement.

## Impact
- Quality: no NG quantity stated in the slide
- Production: machine could not run under EAP until Fico vision was restored
- Safety: not stated in the report
- Repeat risk: possible if temporary test settings are not restored after dry-run or if shift handover is incomplete

## Open Risk / Follow-up
- Need to ensure all temporary test settings are restored before machine release
- Need to verify shift-to-shift handover includes machine abnormality and temporary setting changes
- Need to monitor recurrence of barcode / SN missing issue from Fico vision setting

## Evidence
- Attached report slides showing:
  - issue timeline
  - machine configuration value for Fico vision ON/OFF
  - `.ttt` file example with missing panel SN
  - action list for recovery and prevention
