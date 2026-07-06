---
id: INC-2026-03-04-WC38-RINSE2-TANK-OVER-TEMPERATURE-EQDIW00038
date: 2026-03-04
time: "03:00-10:00"
station: Water Clean
machine: EQDIW00038
model: Attis
issue_type:
  - Control
  - Utility
  - Heating
  - SSR
status: Recovered after SSR replacement and rewiring / Parameters reverified by MOI
owner: EQ
tags:
  - water-clean
  - wc38
  - rinse2
  - over-temperature
  - ssr
  - heating
  - eqdiw00038
---

# WC38_Rinse 2 tank over temperature

## Issue
- Issue description: Rinse 2 tank over temperature (100°C)
- Model: Attis
- Machine: EQDIW00038
- Station: Water clean
- Impact: Output production

## Timeline
- 04/03/2026 03:00
  - Machine running normal
- 04/03/2026 03:04
  - Rinse 2 over temperature alarm
  - Machine auto stop
- 04/03/2026 03:06–09:50
  - EQ check and repair
- 04/03/2026 10:00
  - Machine running normal

## Symptom
- Rinse 2 tank temperature increased abnormally up to 100°C.
- Machine triggered over-temperature alarm and auto stopped.
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
4. EQ checked solid state relay (SSR):
   - When the temperature reached the setpoint 50°C, the SSR could not turn off
   - Temperature continued rising
   - Result: NG

### Conclusion
- Solid state relay was out of control.

## Root Cause
- The solid state relay (SSR) could not turn off when the temperature reached the setpoint 50°C.
- Because the SSR stayed ON abnormally, heating continued and the temperature of Rinse 2 tank kept increasing until over-temperature condition occurred.

## Failure Mechanism
- The rinse 2 heating system is designed to stop heating when the temperature reaches the setpoint (50°C).
- Temperature sensor and PLC I/O were confirmed normal, so the control signal path and measurement path were not the root cause.
- The SSR remained conducting even after the setpoint was reached.
- Because the SSR could not turn off, heater power continued to be applied.
- This caused the rinse 2 tank temperature to keep rising and finally trigger the over-temperature alarm at 100°C.

## Actions
1. EQ turned off the machine power supply to ensure safety.
2. EQ replaced the SSR and reconnected the wiring.
3. EQ checked the heating system after replacement:
   - The heater operates when the temperature is below the setpoint
   - The heater stops when the setpoint is reached
4. EQ restarted the machine and checked the parameters according to MOI:
   - temperature
   - pressure
   - concentration
   - conveyor speed
   - all within spec

## Current Status
- SSR was replaced and wiring was reconnected.
- Heating control returned to normal behavior.
- Machine was restarted and all key parameters were verified within spec.
- Machine running normal again at 10:00 on 04/03/2026.

## Impact
- Quality: not explicitly stated in the slides
- Production: output production affected during machine stop and repair period
- Safety: high-temperature tank condition required immediate power shut-off for safety
- Repeat risk: possible if SSR degradation is not checked proactively

## Open Risk / Follow-up
- Need to monitor SSR behavior on rinse 2 heating circuit
- Need to confirm no repeat over-temperature on next production run
- Need to keep MOI parameter verification after replacement / restart

## Evidence
- Slide 1 confirms:
  - issue title WC38_Rinse 2 tank over temperature
  - model Attis
  - machine EQDIW00038
  - impact output production
  - timeline from 03:00 to 10:00 on 04/03/2026
- Slide 2 confirms:
  - heater rinse 2 tank check OK
  - I/O PLC normal
  - temperature sensor can send signal OK
  - SSR cannot turn off when temperature reaches setpoint 50°C
  - conclusion: solid state relay was out of control
- Slide 3 confirms:
  - turn off machine power for safety
  - replace SSR and reconnect wiring
  - verify heating system turns off at setpoint
  - restart machine and check MOI parameters within spec
