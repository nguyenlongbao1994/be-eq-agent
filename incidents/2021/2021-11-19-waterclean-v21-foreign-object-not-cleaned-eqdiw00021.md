---
id: INC-2021-11-19-WATERCLEAN-V21-FOREIGN-OBJECT-NOT-CLEANED-EQDIW00021
date: 2021-11-19
station: Water Clean
machine: EQDIW00021
line: SMT1
model: C6.5-X1818Sm
issue_type:
  - Process
  - Transfer
  - Utility
  - Investigation
status: No impact confirmed / Monitoring
owner: EQ
tags:
  - water-clean
  - v21
  - foreign-object
  - rail-export-jam
  - mixing-tank-pump-overload
  - eqdiw00021
---

# V21 Water Cleaning Machine – Foreign Object Cleaning Concern

## Issue
- EQ engineer received information that the machine did not clean foreign objects on the surface PCB.
- Line: SMT1
- Model: C6.5-X1818Sm
- Machine: EQDIW00021

## Timeline / Cause Window
- 20:36 PM
  - Lane 2 rail export jam
- 20:41 PM
  - PCB input
- 21:05 PM
  - PCB output
- 21:27 PM
  - Lane 3 track card mixing tank pump overload
- 21:47 PM
  - Water cleaning machine running normally

## Symptom
- Concern was raised that the machine did not clean foreign objects on PCB surface.
- During the same time window, the machine showed:
  - lane 2 rail export jam
  - lane 3 mixing tank pump overload
- The machine stopped working temporarily.

## Machine Check
1. Check concentration N600 → OK
2. Program / parameter → no change
3. Check conveyor operation → OK
4. Check the conveyor belt width behind the water clean machine → OK
5. Check transfer PCB → NG
6. Setup position conveyor → OK

## Root Cause Status
- No confirmed direct root cause was concluded in the slide for foreign-object cleaning failure.
- The available checks did not confirm abnormal concentration, parameter change, or conveyor-width abnormality.

## Failure Mechanism
- A temporary interruption happened in the same period:
  - rail export jam
  - mixing tank pump overload
- However, PCB input/output timing through the machine remained normal:
  - PCB input: 20:41
  - PCB output: 21:05
- Since concentration, program, conveyor operation, and conveyor width checks were normal, the slide conclusion did not confirm that the machine caused actual foreign-object cleaning failure on PCB.
- Therefore, this case is best treated as an investigated abnormal event with no confirmed PCB effect.

## Conclusion
- In this time, PCB input and output through the machine were normal and did not affect PCB.

## Current Status
- Machine returned to normal at 21:47 PM.
- No PCB impact was confirmed in the conclusion.
- Current status: no impact confirmed, continue monitoring.

## Impact
- Quality: no confirmed PCB impact
- Production: temporary machine stop occurred
- Safety: not stated in the slide
- Repeat risk: monitor rail export jam and mixing tank pump overload recurrence

## Open Risk / Follow-up
- Need to continue monitoring lane 2 rail export jam recurrence
- Need to monitor mixing tank pump overload recurrence
- Need to verify foreign-object cleaning performance if similar concern happens again

## Evidence
- Slide title: V21 Water Cleaning machine
- Issue section states:
  - machine did not clean foreign objects on surface PCB (reported concern)
  - line SMT1
  - model C6.5-X1818Sm
  - machine EQDIW00021
- Machine check section confirms:
  - N600 concentration OK
  - program / parameter no change
  - conveyor operation OK
  - conveyor belt width OK
  - transfer PCB NG
  - setup position conveyor OK
- Conclusion section states:
  - PCB input and output machine normal and not affect to PCB
