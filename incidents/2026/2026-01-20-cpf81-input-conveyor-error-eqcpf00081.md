---
id: INC-2026-01-20-CPF81-INPUT-CONVEYOR-ERROR-EQCPF00081
date: 2026-01-20
time: "01:20-11:10"
station: CPF
machine: EQCPF00081
model: C10.5 Small
issue_type:
  - Control
  - Communication
  - PC
  - LPT
  - Conveyor
status: Recovered after PC replacement / PC repair or replacement follow-up
owner: EQ / ME / PD
tags:
  - cpf81
  - input-conveyor-error
  - sfis-pc
  - lpt-port
  - plc-signal
  - eqcpf00081
---

# CPF81 Issue – Input Conveyor Error

## Issue
- Model: C10.5 Small
- Station: Cpfilling
- Machine: EQCPF00081
- Impact: output production

## Timeline
- 01:20 20/01/2026
  - EQ installed new valve
- 01:30 20/01/2026
  - After scanning OK, the board should not be moved into the machine
- 01:30–11:00 20/01/2026
  - EQ investigated the cause
  - EQ detected errors in the SFIS PC
- 11:10 20/01/2026
  - EQ changed the PC
  - Machine running normal

## Symptom
- Input conveyor did not move the board into the machine after scan was already OK.
- Output production was affected.
- Machine issue was linked to signal path between SFIS PC and PLC.

## Root Cause Analysis
1. EQ checked conveyor belt → OK
2. EQ checked scan barcode → OK
3. EQ checked signal cable → OK
4. EQ measured the signal line voltage sent from the SFIS PC to the PLC:
   - Actual = 0.001V → NG
5. Conclusion:
   - PC SFIS LPT port error
   - The LPT port was unable to output the required 3V signal when scan was OK

## Root Cause
- The SFIS PC LPT port was abnormal.
- Because the LPT port could not output the normal 3V signal after scan OK, the PLC did not receive a valid trigger to move the board into the machine.
- Therefore the input conveyor did not run correctly.

## Failure Mechanism
- Normal transfer logic requires the SFIS PC to send a valid signal to the PLC after barcode scan is completed successfully.
- Conveyor belt, barcode scan, and signal cable were all confirmed normal, so the transport mechanism itself was not the cause.
- The measured signal voltage from the SFIS PC to PLC was only 0.001V instead of the expected 3V.
- Because the PLC did not receive the required logic signal, the board was not moved into the machine even though scan was OK.
- This created the input conveyor error condition.

## Actions
1. EQ temporarily used the PC from CPF94 instead of CPF81
2. EQ connected the signal wires and checked them → OK
3. Machine running normal → OK
4. EQ worked with PD to repair or replace the PC if necessary

## Current Status
- Machine recovered after changing the PC.
- Signal path became normal again.
- Machine was running normal at 11:10 on 20/01/2026.

## Impact
- Quality: not stated in the slide
- Production: output production impacted until PC was changed
- Safety: not stated in the report
- Repeat risk: possible if SFIS PC / LPT port condition is not monitored or repaired permanently

## Open Risk / Follow-up
- Need to repair or replace the original SFIS PC of CPF81 if necessary
- Need to monitor the LPT output signal stability
- Need to confirm the board input sequence remains stable after recovery

## Evidence
- Slide title: CPF81 Issue_Input conveyor error
- Machine info:
  - Model: C10.5 Small
  - Station: Cpfilling
  - Machine: EQCPF00081
- FA&RC section confirms:
  - conveyor belt OK
  - barcode scan OK
  - signal cable OK
  - signal line voltage from SFIS PC to PLC = 0.001V → NG
  - conclusion: PC SFIS LPT port error (unable to output 3V signal when scan is OK)
- Action section confirms:
  - temporarily used PC from CPF94
  - connected signal wires
  - machine running normal
