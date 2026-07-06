---
id: INC-2026-04-07-CPF100-PCB-CANNOT-MOVE-AUTOMATICALLY-EQCPF00100
date: 2026-04-07
time: "16:10-18:15"
station: CPF
machine: EQCPF00100
model: Attis
issue_type:
  - Control
  - Software
  - Conveyor
  - Configuration
status: Recovered after replacing FmXP file / Backup file created
owner: EQ
tags:
  - cpf100
  - pcb-cannot-move
  - conveyor
  - fmxp
  - conveyor-cpp
  - attis
---

# Attis EQCPF-100 PCB can not move automatically

## Issue
- Model: Attis
- Station: Cpfilling
- Machine: EQCPF00100
- Impact: Production output

## Timeline
- 16:10 04/07/2026
  - PCB input machine
- 16:20 04/07/2026
  - PCB cannot automatically move away from conveyor
- 16:20–18:10 04/07/2026
  - EQ found root cause and fixed issue
- 18:15 04/07/2026
  - Machine run normal

## Symptom
- PCB could not automatically move away from conveyor after dispensing.
- Production output was affected.
- Manual conveyor control could still run.

## Root Cause Analysis
1. Check conveyor operation and control signal → OK
   - Motor, belt, bearing, pulley, width: normal
   - Manual control: run normal

2. Check sensor at conveyor output → OK
   - Detect PCB normal
   - No PCB no detect

3. Check configuration file → Abnormal
   - Panel finished dispensing but program did not control conveyor to output

### Conclusion
- ACL `conveyor.cpp` file → Error

## Root Cause
- Conveyor hardware and sensor detection were normal.
- The abnormal point was the machine configuration / program file.
- After dispensing finished, the program did not command conveyor output correctly.
- Root cause was identified as ACL `conveyor.cpp` file error.

## Failure Mechanism
- The machine depends on the software configuration / ACL control file to trigger conveyor output after dispensing is completed.
- Because the ACL `conveyor.cpp` file was abnormal, the output command was not sent correctly.
- Even though:
  - conveyor mechanism was normal
  - manual control worked
  - sensor detected PCB correctly
  the program still did not move the PCB out automatically.
- This caused the PCB to remain on conveyor until EQ restored the correct file.

## Actions
1. Copy master FmXP file from another machine to CPF100 machine
2. Change SN to machine SN and run test → Machine run normal
3. Create backup FmXP file for machine

## Current Status
- Master FmXP file was copied into CPF100 machine.
- Machine SN was updated and test was completed.
- Machine ran normally again at 18:15.
- Backup FmXP file was created.

## Impact
- Quality: not stated in the slide
- Production: production output impacted until the file was restored
- Safety: not stated in the slide
- Repeat risk: possible if configuration / FmXP file becomes corrupted again and backup control is not maintained

## Open Risk / Follow-up
- Need to verify long-term stability of the restored FmXP file
- Need to keep backup FmXP file for faster recovery
- Need to monitor whether conveyor output logic repeats the same abnormality

## Evidence
- Slide title: Attis EQCPF-100 PCB can not move automatically
- Description confirms:
  - Model: Attis
  - Station: Cpfilling
  - Machine: EQCPF00100
  - Impact: Production output
- FA&RC confirms:
  - conveyor operation and control signal OK
  - manual control conveyor OK
  - output sensor OK
  - configuration file abnormal
  - conclusion: ACL conveyor.cpp file error
- Action confirms:
  - copy master FmXP file from another machine
  - change SN to machine SN and run test
  - create backup FmXP file
