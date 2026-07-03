---
id: INC-2026-04-13-LASER152-CUTTING-SHIFT-DURING-FAI
date: 2026-04-13
station: Laser
machine: Laser#152
model: C10.5
issue_type:
  - Process
  - Control
  - Alignment
  - Communication
status: Contained / System control improvement ongoing
owner: EQ / ME / QA / PD
tags:
  - laser
  - alignment
  - fai
  - shift
  - machine-release
---

# Laser #152 – Cutting Shift During FAI

## Issue
- Machine: Laser#152  
- Model: C10.5  
- Problem: Laser cutting shift during FAI  
- Impact: Scrap during FAI (cross deviation)  

---

## Symptom
- Cutting line shifted (cross deviation) during FAI  
- Alignment lost after maintenance  
- Vision / mark / vacuum / mechanical checks → OK  
- Only X-Y alignment abnormal  

---

## Root Cause
1. Machine lost X‑Y alignment after maintenance  
2. PD ran FAI **before ME/IPQC confirmed machine status**  
3. No machine release control system  
4. Communication gap between EQ / ME / QA / PD  

👉 Key conclusion from slide:  
- FAI input too early → machine not ready  
- No mandatory verification gate  

---

## Failure Mechanism
- After maintenance, machine requires:
  - alignment verify  
  - optimization by ME  
- Without verification:
  - X-Y offset remains  
  - cutting path deviates  
- Result:
  - cross shift during FAI  
  - scrap generated  

---

## Actions
1. Engineer re-verified and realigned machine  
2. PD reminded:
   - must confirm machine status with ME/IPQC before FAI  

---

## Corrective Action
1. Enforce machine status confirmation before FAI – Done  
2. Alignment re-check after maintenance – Done  

---

## Preventive Action (System Gap)
- Build machine release control flow:
  1. EQ → Maintenance completed  
  2. ME → Optimize recipe  
  3. QA → Confirm OK  
  4. System status = **READY**  
  5. PD → Only allowed to run FAI  

- No action based on:
  - email  
  - verbal communication  

---

## Current Status
- Machine realigned  
- FAI condition stabilized  
- Process improvement (Dashboard control) → ongoing  

---

## Impact
- Quality: Scrap during FAI  
- Production: Delay due to re-alignment  
- Risk: HIGH (if release control not enforced)  

---

## Open Risk / Follow-up
- Need implement system-based release control  
- Need eliminate manual communication dependency  
- Need enforce interlock before PD input  

---

## Evidence
- Fishbone: no issue in material / environment / vacuum  
- Only software / alignment loss abnormal  
- Timeline: FAI executed before machine release  
- Slide confirms communication gap as main gap  
