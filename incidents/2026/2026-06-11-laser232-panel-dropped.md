---
id: INC-2026-06-11-LASER232-PANEL-DROPPED
date: 2026-06-11
station: Automation line
machine: EQLAS00232
model: C10.5
issue_type:
  - Control
  - Interface
  - Transfer
  - Communication
status: Under SAT evaluation
owner: EQ / ME / SMD
tags:
  - laser232
  - panel-drop
  - lift
---

# Laser232 – Panel dropped inside machine

## Issue
- Machine: EQLAS00232
- Model: C10.5
- Problem: Panel dropped inside machine
- Impact: Waiting SAT result

---

## Timeline
- 14:40 → FAI OK (machine normal)
- 15:33 → Panel dropped inside machine
- 16:00 → SMD restored lift, machine continued running

---

## Symptom
- Panel dropped into Laser machine
- No immediate system block
- Machine still able to continue LBO with supervision

---

## Root Cause
1. Lift system fault occurred
2. No error signal sent to Laser
3. Laser continued transfer without interlock
4. Conveyor not running
5. Panel stuck between Laser and Lift
→ Panel fell inside machine

---

## Failure Mechanism
- Interface dependency:
  Laser → Lift must handshake

- Failure chain:
  Lift fault  
  + No signal feedback  
  → Laser assumes OK  
  → Transfer continues  
  → Conveyor stop  
  → Panel stuck  
  → Gravity drop  

---

## Actions
1. Restore lift functionality
2. Continue production under supervision

---

## Corrective Action
- Check communication cable between machines

---

## Preventive Action
1. Improve interlock between Laser & Lift
2. Add “no-run” feedback blocking transfer
3. Ensure PLC handshake validation (2-way confirm)

---

## Impact
- Quality: pending SAT
- Production: moderate risk
- Safety: medium (dropping object)
- Repeat risk: HIGH (system control gap)

---

## Open Risk
- Communication failure still exists
- No fail-safe when Lift fault occurs
