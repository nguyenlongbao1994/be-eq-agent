---
id: INC-2026-05-12-SPT58-DC5-POWER-ALARM
date: 2026-05-12
time: "14:10-14:30"
station: Sputter
machine: Sputter#58
model: C10.5 Small
issue_type:
  - Electrical
  - Power
  - DC
  - Utility
status: Recovered after DC replacement / Monitor required
owner: EQ / ME / PD
tags:
  - sputter
  - spt58
  - dc5
  - power-alarm
---

# SPT#58 – DC5 Power Error Alarm

## Issue
- Machine: Sputter#58
- Model: C10.5 Small
- Problem: DC5 Power error alarm
- Time: 14:10 PM, 12 May, 2026
- NG Qty: No tray NG

---

## Timeline
- Before issue:
  - Machine run normally
- 12 May 14:10
  - Machine alarm:
    - "DC5 error: Power Alarm"
- 14:10 → 14:30
  - EQ checked DC power → DC5 error confirmed
  - Turn off DC and water pipes
  - Replace DC power
- 12 May 14:30
  - Machine continued coating next layers
  - Machine run normal
  - PD verify OK

---

## Symptom
- Machine showed DC5 power alarm during normal run
- No NG product observed
- Process temporarily interrupted

---

## Root Cause
- DC5 power module defective
- Output unstable → alarm triggered
- No issue related to product or cathode detected

---

## Failure Mechanism
- DC power unit provides electrical supply for sputtering process
- When DC5 module becomes unstable or fails:
  - Power output exceeds control limit
  - Alarm triggered by control system
- Proper shutdown required to avoid damage
- Replacement restores stable power output

---

## Actions
1. Detect DC5 Power Alarm
2. Check DC power → confirm DC5 error
3. Turn off DC and water pipes
4. Replace DC power module
5. Resume machine run
6. Continue coating process
7. Verify output → OK

---

## Preventive Action
1. Maintain spare DC modules in line
2. Monitor DC output condition regularly
3. Add DC power inspection into PM checklist
4. Prepare quick replacement SOP

---

## Current Status
- DC5 replaced
- Machine resumed normal operation
- No NG product recorded
- Process stable

---

## Impact
- Quality: No NG
- Production: short interruption (~20 min)
- Safety: low
- Repeat risk: medium if DC aging not controlled

---

## Open Risk / Follow-up
- Monitor DC5 performance after replacement
- Audit DC modules across similar machines
- Ensure spare availability for quick recovery
