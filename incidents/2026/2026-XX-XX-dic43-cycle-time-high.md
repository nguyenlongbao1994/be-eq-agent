---
id: INC-2026-XX-XX-DIC43-CYCLE-TIME-HIGH
date: 2026-XX-XX
station: Automation line
machine: EQDIC00043
model: C10.5
issue_type:
  - Process
  - Automation
  - Capacity
status: Optimization ongoing
owner: IE / EQ / Vendor
---

# DIC43 – Cycle time is high

## Issue
- Machine: EQDIC00043  
- Model: C10.5  
- Problem: Cycle time higher than target  
- Impact: No quality issue but capacity impact  

---

## Symptom
- CT actual > CT target  
- UPD high  
- Automatic mode slower than manual  

---

## Data
- Load: 63.7s  
- Process: 51.3s  
- Unload: 57.3s  
- CT/panel (1 lane): 172.3s  
- CT/panel (2 lane): 86.2s  
- Target CT: 52.6  
- Actual CT: 59.6  

---

## Root Cause
1. Cleaning process time identical (manual = auto)  
2. Additional transfer in automation mode:
   - Buffer → Fixture → Mechanism → Washing  
3. Multiple motion steps increase CT  
4. Load/unload time is main contributor  

---

## Failure Mechanism
- Automatic flow:
  - Panel must travel through intermediate positions  
- Gripper movement limited per cycle  
- Extra movement distance and sequencing:  
→ increases cycle time  

---

## Actions
- Work with vendor JQ to optimize motion and program  

---

## Current Status
- Optimization ongoing  
- No quality impact  

---

## Impact
- Quality: 0  
- Production: HIGH impact (capacity loss)  
- Repeat risk: systematic issue  

---

## Next step
1. Optimize motion path  
2. Reduce idle movement  
3. Tune motor speed/acceleration  
4. Balance load-unload timing  
