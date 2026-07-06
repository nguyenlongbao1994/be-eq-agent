---
id: INC-2026-05-04-WC37-RINSE2-TANK-HEATING-SOLID-ABNORMAL-EQDIW00037
date: 2026-05-04
time: "09:50-16:00"
station: Water Clean
machine: EQDIW00037
model: C10.5
issue_type:
  - Control
  - Electrical
  - Heating
  - PLC
  - SSR
status: Recovered after moving PLC output from Y20 to Y74 and updating program / Ongoing follow-up
owner: EQ
tags:
  - wc37
  - rinse2
  - over-temperature
  - heating
  - ssr
  - plc
  - y20
  - eqdiw00037
---

# N243 | WC37_Rinse2 tank heating solid abnormal

## Issue Description
- Issue: Rinse2 tank heating solid abnormal
- Model: C10.5
- Station: Water clean
- Machine: EQDIW00037
- Impact: Output production

## Customer Impact
- No impacts

## Containment Actions
- The machine auto stopped
- EQ used manual mode to move product to WC38 and performed repair

## Timeline
- 09:50 04/05/2026
  - Machine running normal
- 09:56 04/05/2026
  - Machine alarm: Rinse2 heating solid abnormal
- 10:00–15:00 04/05/2026
  - EQ investigate root cause and repair
- 15:10 04/05/2026
  - Issue resolved and run test machine
- 16:00 04/05/2026
  - Machine running normal and handover to PD team

## Symptom
- Rinse 2 tank heating became abnormal.
- Machine alarmed and auto stopped.
- Output production was affected.

## Root Cause Analysis
1. EQ checked heater rinse 2 tank:
   - The temperature increased during heating control
   - Result: OK
2. EQ checked I/O signal PLC:
   - Result: Normal
3. EQ checked temperature sensor:
   - Can send signal to the control system
   - Result: OK
4. EQ checked solid state relay:
   - When the temperature reached the setpoint 50°C, the SSR could not turn off
   - Temperature kept continuing to rise
   - Result: NG
5. EQ checked resistance between Y20 output PLC and 0V:
   - 0.2Ω
   - Y20 was short-circuited to 0V

### Conclusion
- Due to a short circuit, the Y20 output continuously provided a signal, causing the SSR to remain ON.

## Root Cause
- PLC output Y20 was short-circuited to 0V.
- Because Y20 continuously provided a signal, the solid state relay (SSR) remained ON.
- As a result, the heating of Rinse 2 tank did not stop when the setpoint 50°C was reached.

## Failure Mechanism
- In normal operation, the heating system should stop heating once the rinse 2 tank reaches the temperature setpoint.
- Temperature sensor and PLC I/O check were normal, so sensing and basic control communication were not the root cause.
- The actual abnormality was that PLC output Y20 was short-circuited to 0V.
- This short-circuit caused a constant output signal to the SSR.
- Because the SSR stayed ON continuously, heater output did not turn off at the setpoint.
- Temperature therefore continued to rise, triggering rinse 2 over-temperature abnormal and machine auto stop.

## Corrective Actions
1. Change the PLC output from Y20 to Y74
2. Update the new program and upload it to the PLC
3. Run test machine for 1 hour and monitor for any issues

## Action Verification
- EQ turned off the machine power supply to ensure safety
- EQ replaced / updated connection and reconnected the wiring
- EQ checked the heating system after repair:
  - The heater operates when the temperature is below the setpoint
  - The heater stops when the setpoint is reached
- EQ restarted the machine and checked the parameters according to MOI:
  - temperature
  - pressure
  - concentration
  - conveyor speed
- All parameters were within spec

## Next Steps
- Keep follow the machine — On going

## Current Status
- PLC output was moved from Y20 to Y74
- Program was updated and uploaded to the PLC
- Test machine run was completed
- Machine was running normal again at 16:00 and handed over to PD team
- Current status: recovered, continue follow-up

## Impact
- Quality: no customer impact stated
- Production: output production affected during alarm / repair window
- Safety: EQ turned off machine power supply to ensure safety
- Repeat risk: possible if PLC output / SSR control path is not monitored after repair

## Open Risk / Follow-up
- Need to continue follow the machine
- Need to monitor rinse 2 heating cut-off behavior at setpoint
- Need to confirm no abnormal repeat on new PLC output Y74 control path

## Evidence
- Slide 1 confirms:
  - issue title WC37_Rinse2 tank heating solid abnormal
  - model C10.5
  - station Water clean
  - machine EQDIW00037
  - customer impact no impacts
  - timeline from 09:50 to 16:00 on 04/05/2026
- Slide 2 confirms:
  - heater rinse 2 tank check OK
  - I/O PLC normal
  - temperature sensor OK
  - SSR cannot turn off at 50°C
  - Y20 output PLC to 0V = 0.2Ω
  - conclusion: Y20 short-circuit caused SSR remain ON
- Slide 3 confirms:
  - change PLC output from Y20 to Y74
  - update and upload new program
  - run 1-hour test
  - restart and verify MOI parameters within spec
