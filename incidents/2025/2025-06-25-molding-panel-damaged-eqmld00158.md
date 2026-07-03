---
id: INC-2025-06-25-MOLDING-PANEL-DAMAGED-EQMLD00158
date: 2025-06-25
station: Molding
machine: EQMLD00158
model_note: "Issue bullet appears to show C10.5 Big, while slide title shows C8.5 Big damaged"
issue_type:
  - Process
  - Mechanical
  - Nozzle
  - Vacuum
  - Air path
status: Monitoring after nozzle-path cleaning
owner: EQ / ME / PD
tags:
  - molding
  - panel-damaged
  - compound-cull
  - nozzle
  - vacuum-pickup
  - break-vacuum
  - solenoid
  - eqmld00158
---

# Molding machine #158 – Issue Panel broken / Panel damaged

## Issue
- Panel PCB: Damaged
- Quantity: 1 SIP
- Machine: EQMLD00158
- Time shown in slide: 1:38 AM (21/6/2025)
- Note: slide title shows "Molding C8.5 Big damaged", but issue bullet line appears to show model "C10.5 Big"

## Symptom
- Panel PCB was damaged during molding handling sequence.
- One SIP at location 31 was reported damaged.

## Root Cause
- Compound cull remained on nozzle.
- After the panel finished mold cycle, the compound handle moved into mold chase to pick compound cull.
- The last remained compound cull touched the panel.
- Nozzle moved down and impacted the panel.
- Result: 1 SIP at location 31 was damaged.

## Failure Mechanism
- Remaining compound cull stayed on nozzle instead of being cleared correctly.
- During the follow-up nozzle / compound-handle movement, the remained cull made contact with the panel.
- Subsequent nozzle movement downward created mechanical impact to panel surface / edge.
- This interaction caused panel damage.

## Actions
1. Check solenoid valve of vacuum pickup cull (3Y2) manually
   - Function of 3Y2:
     - open vacuum when picking up remained compound
     - close vacuum when rejecting remained compound to reject box
   - Result: solenoid valve opened and closed normally

2. Check solenoid valve of break vacuum (3Y1) manually
   - Function of 3Y1:
     - supply break air to reject remained compound from nozzle to reject box
   - Result: solenoid valve opened and closed normally

3. Check all vacuum tube and break-vacuum tube
   - Result:
     - no damage
     - no leakage
     - no clogging

4. Monitor these valves in auto mode while running with bare panel

5. Take out nozzle unit to clean:
   - nozzle shaft vacuum path
   - break-air path

## Current Status
- Solenoid valves 3Y2 and 3Y1 functioned normally in manual check.
