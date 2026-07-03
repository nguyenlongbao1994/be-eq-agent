---
id: INC-2026-02-25-LASER234-COMPOUND-REMAINS-SIDE
date: 2026-02-25
station: Laser Ablation
machine: EQLAS00234
model: C10.5
issue_type:
  - Process
  - Laser
  - Material
  - Unknown
status: Root cause investigation ongoing
owner: EQ / ME / Vendor
tags:
  - laser
  - compound
  - residue
  - side-defect
---

# Attis Laser #234 – Compound remains at the side

## Issue
- Machine: EQLAS00234  
- Model: C10.5  
- Problem: Some SIPs have compound remains at the side  
- Impact: 167 SIPs require ME rework  

---

## Timeline
- 01/07:
  - EQ changed new laser head and completed calibration  
- 01/09 → 01/13:
  - ME performed MBO process  
- 01/15 → 01/16:
  - Machine control run → result OK  
- 02/25 03:25:
  - Start MP production  
- 02/25 13:30:
  - PD inspection detected compound remains  
- 02/25 14:00:
  - EQ + ME started investigation  

---

## Symptom
- Residual compound observed at panel edge  
- Appears on multiple SIP units  
- Not detected during previous FAI / MBO  

---

## Root Cause Status
- Root cause NOT confirmed yet  
- Current analysis shows:
  - Not machine parameter issue  
  - Possibly process condition or upstream factor  

---

## Checks Performed
1. FAI record → No abnormal  
2. Visual → defect confirmed (compound residue)  
3. Laser power → 32.48W (within spec 32–33W)  
4. Table / height / alignment → OK  
5. Vacuum → -82.3 kPa (within spec -60 ~ -100) → OK  
6. Lens → No contamination → OK  
7. Z-focus / geometry → OK  
8. MBO after laser head replacement → PASS  

---

## Failure Mechanism (current hypothesis)
- Laser ablation not completely removing compound at edge  
- Possible contributors:
  - edge energy distribution variation  
  - material condition inconsistency  
  - upstream molding / coating residue  
- Since all machine conditions OK → likely process/material interaction  

---

## Actions
1. Co-work with ME to define root cause → Ongoing  
2. Contact vendor (Han’s Laser) for analysis → Ongoing  

---

## Current Status
- Issue detected and contained  
- 167 SIPs held for rework  
- Machine continues under monitoring  

---

## Impact
- Quality: 167 SIPs NG (rework)  
- Production: impact limited but risk ongoing  
- Safety: none  
- Repeat risk: HIGH (root cause unknown)  

---

## Open Risk / Follow-up
- Need confirm if issue from:
  - laser energy distribution  
  - product material variation  
- Need DOE / parameter verification  
- Need vendor support to define mechanism  

---

## Evidence
- Visual inspection photos of residue  
- Laser parameter log (power, vacuum, alignment)  
- Calibration / MBO reports  
- Data logs showing stable machine condition  
