---
id: INC-2026-01-13-CPF80-VALVE-BLOCKAGE-GLUE-WEIGHT-OUT-OF-SPEC-EQCPF00080
date: 2026-01-13
station: CPF
machine: EQCPF00080
model: C10.5 Small
issue_type:
  - Process
  - Dispense
  - Valve
  - Nozzle clogging
status: Recovered after valve replacement and calibration / Monitoring
owner: EQ / ME
tags:
  - cpf80
  - valve-blockage
  - glue-weight
  - nozzle-clogging
  - eqcpf00080
---

# CPF80 Issue – Valve Blockage and Glue Weight Out of Spec

## Issue
- Model: C10.5 Small
- Station: Cpfilling
- Machine: EQCPF00080
- Impact: output production

## Timeline
- 20:30 12/01/2026
  - EQ replaced valve
  - Machine ran normal
- 00:30 13/01/2026
  - The valve was clogged
  - Glue balance was out of spec
- 00:35–01:25 13/01/2026
  - EQ replaced new valve
  - ME adjusted program
- 01:30 13/01/2026
  - Machine running normal

## Symptom
- Glue balance became out of spec.
- Valve could not dispense glue normally.
- Issue affected output production.

## Root Cause
- EQ checked the valve to detect whether glue was not flowing out.
- Result: nozzle was clogged.
- Because the nozzle was clogged, the valve did not dispense glue correctly.
- Glue measurement became out of spec.
- Conclusion: nozzle is clogged.

## Failure Mechanism
- The dispense valve depends on a clear nozzle to allow stable glue flow.
- When the nozzle became clogged, glue flow was restricted or blocked.
- Because glue could not be dispensed normally, glue balance / measurement went out of spec.
- This created valve blockage behavior and glue weight abnormality.

## Actions
1. EQ replaced a new valve and calibrated the valve → OK
2. ME adjusted program → OK
3. Machine running normal → OK
4. EQ removed the nozzle for cleaning and maintaining the valve body → OK

## Current Status
- Valve was replaced.
- Valve calibration was completed.
- Program adjustment was completed.
- Nozzle was removed for cleaning and valve-body maintenance.
- Machine recovered and was running normal at 01:30 on 13/01/2026.

## Impact
- Quality: not explicitly stated in the slide
- Production: output production impacted during the issue window
- Safety: not stated in the report
- Repeat risk: possible if nozzle clogging and valve-body maintenance are not controlled

## Open Risk / Follow-up
- Need to monitor glue weight balance after replacement and calibration
- Need to continue nozzle cleaning and valve-body maintenance control
- Need to observe repeat valve blockage tendency on EQCPF00080

## Evidence
- Slide title: CPF80 Issue_Valve Blockage and Glue Weight Out of Spec
- Root cause text confirms:
  - EQ checks the valve to detect if the glue is not flowing out
  - Nozzle is clogged
  - The valve isn't dispensing glue
  - The glue measurement is out of spec
- Action section confirms:
  - replace new valve and calibrate valve
  - ME adjust program
  - machine running normal
  - remove nozzle for cleaning and maintaining the valve body
