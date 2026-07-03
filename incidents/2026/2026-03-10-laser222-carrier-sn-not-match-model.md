---
id: INC-2026-03-10-LASER222-CARRIER-SN-NOT-MATCH-MODEL
date: 2026-03-10
time: "15:25-19:00"
station: Laser
machine: EQLAS00222
model: C10.5
issue_type:
  - IT
  - Software
  - Communication
  - Data transfer
status: Recovered after system restore / Virus control required
owner: EQ / IT / ME
tags:
  - laser
  - carrier-sn
  - data-transfer
  - virus
---

# Attis Laser #222 – Carrier SN not match with Model

## Issue
- Machine: EQLAS00222  
- Model: C10.5  
- Problem: Carrier SN not match with Model  
- Time: 03/10/2026 (15:25 ~ 19:00)  
- Impact: 0 SIP  

---

## Timeline
- Before: Machine normal (idle)  
- 15:25 → Alarm:
  - “Carrier SN not match with model”  
- 19:00 →
  - EQ restore software & data files  
  - Machine run normal  

---

## Symptom
- Alarm showing mismatch between Carrier SN and Model  
- System communication abnormal  
- Data transfer unstable  

---

## Root Cause
1. PC infected by virus  
2. Virus continuously generated new files → system overload  
3. Virus deleted executable files  
4. Result:
   - Data transfer error  
   - System mismatch → wrong SN vs model  

---

## Failure Mechanism
- Handler PC handles:
  - SN data  
  - model mapping  
- Virus impact:
  - File overload → system lag / freeze  
  - Missing executable → corrupted data logic  
- Result:
  - Wrong data mapping → mismatch alarm  
  - System cannot validate SN correctly  

---

## Actions
1. Restore Window system  
2. Restore software data files  
3. Reconnect machine to SFIS system  
4. Check machine homing and communication → OK  

---

## Current Status
- System restored  
- Data transfer normal  
- Machine running normally  

---

## Impact
- Quality: 0 SIP  
- Production: Temporary stop  
- Safety: low  
- Repeat risk: HIGH (if virus not controlled)  

---

## Preventive Action
1. Install antivirus / endpoint protection  
2. Lock software environment (no external file injection)  
3. Control USB / external access  
4. Backup system periodically  

---

## Open Risk / Follow-up
- Need audit all handler PCs  
- Need system hardening policy  
- Need monitor abnormal file generation  

---

## Evidence
- Alarm screen shows mismatch error  
- System logs show abnormal file generation  
- After restore → data transfer normal  
