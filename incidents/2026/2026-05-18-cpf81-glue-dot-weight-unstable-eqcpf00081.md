---
id: INC-2026-05-18-CPF81-GLUE-DOT-WEIGHT-UNSTABLE-EQCPF00081
date: 2026-05-18
station: CPF
machine: EQCPF00081
model: C10.5
issue_type:
  - Process
  - Measurement
  - Scale
  - Valve
status: Recovered after scale setup and valve verification / Follow-up ongoing
owner: EQ / PD / QMD
tags:
  - cpf81
  - glue-dot-weight
  - unstable
  - scale
  - valve
  - eqcpf00081
---

# N243 | CPF81_Glue dot weight is unstable

## Issue Description
- Issue: Dot weight is unstable
- Model: C10.5
- Station: CPFILLING
- Machine: EQCPF00081
- Impact: Output production
- Customer Impact: No impacts

## Containment Actions
- Stop machine and perform repair

## Timeline
- 18/05/2026 19:30
  - Machine running normal
- 18/05/2026 20:20
  - EQ replaced valve #18 as schedule
  - Dot weight out of spec
  - Cannot production
- After that
  - EQ replaced valves #19, #20, #17, #04 for valve #18
  - Dot weight was still unstable
- 19/05/2026 03:10–09:20
  - EQ investigated root cause and repaired
- 19/05/2026 09:30
  - Machine running normal

## FA & RC
1. Replace valves 19, 20, 17, 04 for valve 18
   - Dot weight is still unstable
2. Check air pressure: within spec
   - OK
3. Use calibration weight to setup the scale, then weigh again
   - Dot weight is stable

### Conclusion
- The scale is abnormal

## Root Cause
- Air pressure was checked and found within spec.
- Replacing valve #18 and then replacing four additional valves still did not stabilize the dot weight.
- After using calibration weight to set up the scale and weighing again, the dot weight became stable.
- Therefore the root cause was identified as abnormal scale / weighing setup rather than valve hardware only.

## Failure Mechanism
- CPF production depends on stable glue dot weight measurement to validate dispensing condition.
- When the scale setup was abnormal, measured dot weight appeared unstable and out of control.
- Because of the unstable measurement condition, valve replacement alone did not resolve the issue.
- Once the scale was set up again using calibration weight, dot weight became stable and production returned to normal.
- This indicates the main problem was measurement / scale abnormality affecting process control judgment.

## Corrective Actions
1. Remove, clean, then install back to test dot weight for valve 18, 19, 20, 17, 04
   - Dot weight is stable
   - Valve OK
2. Borrow the calibration weight from QMD and setup the scale
3. Install the valve and weigh again
   - Dot weight is stable
   - OK
4. PD redo FAI and machine running normal

## Long-Term Corrective Action
- Keep follow the machine – On going

## Current Status
- Dot weight became stable after scale setup using calibration weight.
- Valve verification after cleaning / reinstall was OK.
- PD redid FAI and machine returned to normal.
- Current status: recovered, continue follow-up.

## Impact
- Quality: customer impact stated as no impacts
- Production: output production was affected before recovery
- Safety: not stated in the slide
- Repeat risk: possible if scale setup / calibration control is not maintained

## Open Risk / Follow-up
- Need to continue following the machine
- Need to ensure scale setup remains valid
- Need to verify dot weight stability during subsequent production lots

## Evidence
- Slide title: N243 | CPF81_Glue dot weight is unstable
- Description confirms:
  - Model: C10.5
  - Station: CPFILLING
  - Machine: EQCPF00081
  - Impact: Output production
  - Customer Impact: No impacts
- FA & RC confirms:
  - replacing multiple valves still left dot weight unstable
  - air pressure within spec
  - using calibration weight to setup the scale made dot weight stable
  - conclusion: the scale is abnormal
- Corrective Actions confirm:
  - clean / reinstall valves and test
  - borrow calibration weight from QMD
  - install the valve and weigh again
  - PD redo FAI and machine running normal
