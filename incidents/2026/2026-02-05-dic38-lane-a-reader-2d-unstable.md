---
id: INC-2026-02-05-DIC38-LANE-A-READER-2D-UNSTABLE
date: 2026-02-05
station: LT Dry-ice
machine: EQDIC00038
model: C10.5
issue_type:
  - Sensor
  - Vision
  - Scanner
  - Alignment
status: Recovered after scanner retuning / Software improvement ongoing
owner: EQ / ME
tags:
  - dic38
  - scanner
  - 2d-reader
  - unstable
---

# DIC#38 – Lane A reader 2D code unstable

## Issue
- Machine: EQDIC00038  
- Model: C10.5  
- Problem: 2D reader unstable (Lane A)  
- Impact: No production impact  

---

## Timeline (từ ảnh)
- 02/05 08:10 → FAI OK  
- 10:10–10:40 (01/07) → Alarm “2D reader fault”  
- 02/05 10:45 → Adjust position / re‑tune scanner  
- 02/05 10:50–16:20 → Machine run normal  

---

## Symptom
- Scanner đọc lúc được lúc không  
- Alarm intermittent “2D reader fault”  
- Barcode image blur  

---

## Root Cause (theo slide)
1. Scanner focus fine‑tuning chưa đủ  
2. Position reader chưa tối ưu  
→ Dẫn đến:
- Image blur  
- Decode không ổn định  

---

## Failure Mechanism (giải thích BE)
- 2D reader phụ thuộc:
  - focus plane  
  - angle + distance  
- Lệch nhẹ → image blur → decode fail ngẫu nhiên  
- Không fail hoàn toàn → dạng intermittent  

---

## Actions
1. Clean scanner  
2. Readjust scanner position  
3. Fine‑tune focus  
4. Verify reading → OK  

---

## Current Status
- Scanner reading ổn định  
- Machine run normal  
- Không NG  

---

## Impact
- Quality: 0 NG  
- Production: không ảnh hưởng  
- Repeat risk: MEDIUM (dạng intermittent)  

---

## Preventive
- Add scanner tuning step sau maintain  
- Check image quality định kỳ  
- Update scanner software (ongoing)  
