---
id: INC-2026-03-12-LASER177-CORNER-SPUTTER-PEELING
date: 2026-03-12
station: Laser combine
machine: EQLAS00177
model: C10.5
issue_type:
  - Process
  - Laser
  - Surface defect
  - Unknown
status: Root cause investigation ongoing
owner: EQ / ME
tags:
  - laser
  - sputter-peeling
  - corner-defect
  - dark-corner
---

# Laser #177 – Corner sputter peeling off

## Issue
- Machine: EQLAS00177  
- Model: C10.5  
- Problem: Corner sputter peeling off (darkened corner)  
- Impact: 14 SIP NG  

---

## Timeline
- Before: Machine running normally  
- 03/12/2026 01:17 → First SIP with dark corner detected  
- 03/12/2026 14:53 → Additional 13 SIP with same issue  
- 03/13/2026 01:00 → EQ & ME investigate  

---

## Symptom
- Darkened area at SIP corner  
- Sputter layer peeling off at edge  
- Repeat defect across multiple units  

---

## Root Cause Status
❗ Root cause NOT identified  

---

## FA & RC (from slide)
1. Laser power = 32.65W (Spec 32–33W) → Stable ✅  
2. Cover area clean → no foreign object ✅  
3. Table / alignment → OK ✅  
4. Vacuum = -84.0 kPa → OK ✅  
5. Lens → clean ✅  
6. Z-focus → OK ✅  
7. Geometry (square / circle) → OK ✅  
8. Maintenance → completed, no abnormal  

👉 Conclusion:
- **Machine condition normal**
- **Not mechanical / not electrical / not setpoint issue**

---

## Failure Mechanism (BE reasoning)
- Peeling xảy ra tại **edge / corner → stress zone cao**
- Possible mechanism:
  1. Adhesion yếu giữa layer (sputter ↔ substrate)
  2. Edge heating / energy distribution không đều
  3. Residual compound / contamination từ upstream  
- Vì tất cả machine OK → nghiêng về:
  - **Process interaction**
  - **Material / upstream influence**

---

## Actions
1. Co-work with ME team to define root cause → ongoing  

---

## Current Status
- Issue under investigation  
- Machine continues with monitoring  

---

## Impact
- Quality: 14 SIP NG  
- Production: low impact nhưng có trend risk  
- Repeat risk: HIGH (unknown cause)  

---

## Open Risk / Follow-up
- Check upstream process:
  - Molding / plasma / cleaning  
- Verify material surface condition  
- DOE laser edge behavior  
- Compare lot-to-lot variation  

---

## Evidence
- Visual dark corner defect  
- Power graph stable  
- Inspection data OK  
- Machine check list normal  
