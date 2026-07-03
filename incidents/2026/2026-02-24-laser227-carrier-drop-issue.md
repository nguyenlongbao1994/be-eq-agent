---
id: INC-2026-02-24-LASER227-CARRIER-DROP-ISSUE
date: 2026-02-24
time: "15:46-15:51"
station: Laser combine
machine: EQLAS00227
model: C10.5
issue_type:
  - Human
  - Mechanical
  - Transfer
  - Sensor
status: Recovered / Control improved
owner: EQ / PD
tags:
  - laser227
  - carrier-drop
  - uld
  - panel-jam
---

# Laser #227 – Carrier drop issue

## Issue
- Machine: EQLAS00227  
- Model: C10.5  
- Problem: Carrier dropped  
- Time: 15:50, 24 Feb 2026  
- NG Qty: 2 SIP scrap  

---

## Timeline
- Panel completed laser process → transfer to ULD  
- 15:46:35 → ULD panel jam alarm  
- PD reset alarm but panel not fully discharged  
- PD switched ULD from Auto → Manual  
- Conveyor stopped immediately  
- Laser table continued moving  
- 15:50 → Carrier collision → dropped  

---

## Symptom
- Carrier dropped during transfer  
- Collision between laser table and unloader conveyor  
- Panel popped out → SIP damaged  

---

## Root Cause
1. ULD panel jam occurred  
2. PD reset alarm without verifying panel clearance  
3. PD switched ULD mode Auto → Manual → conveyor stop  
4. Panel passed laser out sensor but still inside table  
5. Laser table moved → mechanical collision  

---

## Failure Mechanism
- Out sensor position too far:
  - detection triggered early (panel not fully cleared)
- Manual mode stop:
  - stops ULD immediately
- Laser logic:
  - assumes panel cleared → continues movement
- Result:
  - carrier still inside → collision  
  - safety door drop → carrier drop  

---

## Actions
1. Train PD to confirm no panel remains before restart  
2. Adjust out sensor position closer to table edge  
3. Add rule:
   - No mode change during transfer  
   - Must verify panel cleared  

---

## Current Status
- Sensor adjusted  
- Operation rule updated  
- Machine running normal  

---

## Impact
- Quality: 2 SIP NG  
- Production: short interruption  
- Safety: medium (collision risk)  
- Repeat risk: HIGH if procedure not followed  

---

## Preventive Action
1. Improve sensor coverage to avoid false clearance  
2. Add interlock: block motion if panel not fully out  
3. Enforce operator SOP for jam recovery  
4. Add double-check before reset  

---

## Evidence
- Timeline log of jam → reset → collision  
- Simulation confirming collision mechanism  
- Sensor position gap identified  
- Post-adjust → alarm protection added  
