---
id: INC-2026-04-20-LASER178-PANEL-SCRAP-DURING-PM
date: 2026-04-20
station: Laser combine
machine: EQLAS00178
model: C10.5
issue_type:
  - Human
  - Process
  - PM procedure
  - Training
status: Recovered / SOP improvement implemented
owner: EQ / ME / DL
tags:
  - laser178
  - scrap
  - pm-error
  - human-error
---

# Laser #178 – Panel Scrap during Machine PM

## Issue
- Machine: EQLAS00178  
- Model: C10.5  
- Problem: Panel scrap during PM activity  
- Impact: 1 panel → 24 SIP scrap  

---

## Timeline
- 08:34 → FAI OK, machine running normal  
- 13:55 → Machine start PM  
- During PM → DL performs height test using MP panel  
- → Panel scrap triggered  
- 16:00 → Finish maintain, ME recheck OK  
- 16:30 → Redo FAI → machine normal  

---

## Symptom
- Panel scrap during PM activity  
- Occurs during height test step  
- No machine alarm  

---

## Root Cause
1. Height test procedure:
   - MUST use **bare panel only**  
2. DL incorrect operation:
   - Used **MP panel instead of bare panel**  
3. DL did not prepare bare panel  
4. No DRI / expat onsite verification  

👉 Final:
- **Human error + procedure violation**

---

## Failure Mechanism
- Height test requires:
  - controlled thickness → bare panel  
- Using MP panel:
  - thickness mismatch  
  - mechanical offset  
- Causes:
  - incorrect contact  
  - panel damage → scrap  

---

## Actions (Containment)
1. Coordinate ME team inspect product  
2. Confirm all SIP scrap  

---

## Corrective Actions
1. Retrain DL on PM procedure → Done  
2. Punishment for incorrect operation → Ongoing  

---

## Preventive Actions
1. Update SOP:
   - MUST use bare panel for height test  
2. Update Han’s Laser checklist  
3. Add DRI onsite verification for high-risk PM  
4. Control DL qualification for critical PM items  

---

## Current Status
- Machine run normal after FAI  
- SOP updated  
- Training executed  

---

## Impact
- Quality: 24 SIP scrap  
- Production: minor impact  
- Safety: low  
- Repeat risk: HIGH (if human error not controlled)  

---

## Open Risk
- DL training gap still exists  
- Need enforce DRI sign-off  
- Need audit all PM procedures  

---

## Evidence
- Timeline shows PM activity → scrap  
- SOP mismatch (bare vs MP panel)  
- Training & checklist document attached  
``
