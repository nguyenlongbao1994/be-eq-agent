---
id: INC-2026-01-13-DIW37-EXTERNAL-TANK-LEAKING-WATER-EQDIW00037
date: 2026-01-13
station: Water Clean
machine: EQDIW00037
model: C10.5
issue_type:
  - Utility
  - Solenoid valve
  - Water level
  - Leak
status: Temporarily recovered / Waiting vendor solenoid replacement
owner: EQ / Vendor
tags:
  - diw37
  - external-tank
  - leaking-water
  - solenoid-valve
  - water-level
  - eqdiw00037
---

# DIW37_External tank leaking water

## Description
- Model: C10.5
- Station: Water clean
- Machine: EQDIW00037
- Impact: 168 pcs over Q-time

## Timeline
- 12/01/2026 20:45
  - PD replaced DI water
  - Machine ran normal
- 13/01/2026 05:10
  - The machine leaked water and alarmed
- 13/01/2026 05:15–08:45
  - EQ temporarily handled the issue
- 13/01/2026 08:45
  - The machine was operational again
  - Machine required monitoring and waiting for solenoid-valve replacement

## Symptom
- External tank leaked water.
- Machine alarmed at high-high water level.
- Impact quantity was 168 pcs over Q-time.

## Root Cause Analysis
1. Water automatically pumped into the tank up to the high level.
2. The solenoid valve did not turn off and continued pumping until the high-high water level.
3. High-high level alarm occurred.
4. Because the solenoid valve could not turn off, water was always pumped in and leaked out.

### Conclusion
- The solenoid valve was damaged.

## Root Cause
- The solenoid valve was damaged and could not turn off.
- Because the solenoid valve did not shut off, water continuously pumped into the external tank until overflow / leak condition occurred.

## Failure Mechanism
- The external tank fill system depends on the solenoid valve to stop water inflow once the required level is reached.
- In this case, water level sensor was checked and found OK, but the solenoid valve was NG.
- Since the solenoid valve did not turn off, water kept filling the tank beyond the normal high level.
- This led to high-high water level alarm and external tank water leakage.

## Actions
1. EQ checked water level sensor → OK
2. EQ checked solenoid valve → NG
3. EQ temporarily adjusted the manual valve to reduce incoming water so it matched machine water loss / consumption
   - EQ monitoring → OK
4. Waiting for vendor to send the solenoid valve for replacement
5. If the same situation occurs next time:
   - shut off the power supply to ensure safety
   - prepare / order water suction equipment
   - add a water-leak detection sensor

## Current Status
- Machine was temporarily recovered and operational again.
- Temporary containment was completed by manual-valve adjustment.
- Long-term recovery still depends on replacing the damaged solenoid valve.

## Impact
- Quality: 168 pcs over Q-time
- Production: machine leaked water and required temporary handling
- Safety: water leak risk exists; power shutdown is required if the same situation recurs
- Repeat risk: high until the solenoid valve is replaced

## Open Risk / Follow-up
- Need vendor to send and replace the solenoid valve
- Need to monitor machine until replacement is completed
- Need to add water-leak detection sensor as preventive action
- Need to prepare water suction equipment for emergency recurrence

## Evidence
- Slide title: DIW37_External tank leaking water
- Description shows:
  - Model: C10.5
  - Station: Water clean
  - Machine: EQDIW00037
  - Impact: 168 pcs over Q-time
- FA&RC confirms:
  - water automatically pumped to high level
  - solenoid valve did not turn off
  - high-high level alarm
  - conclusion: solenoid valve is damaged
- Action confirms:
  - water level sensor OK
  - solenoid valve NG
  - temporary manual-valve adjustment
  - waiting vendor replacement
