---
id: INC-2026-03-17-DIC23-SMD-FALSE-ERROR
date: 2026-03-17
station: Trench Dry ice
machine: EQDIC00023
model: C10.5
issue_type:
  - Sensor
  - System
  - Communication
  - False detection
status: Monitoring / SMD analysis ongoing
owner: EQ / IT / ME
tags:
  - dic23
  - smd
  - false-alarm
---

# Dryice23 – SMD box shows a false error

## Issue
- Machine: EQDIC00023  
- Model: C10.5  
- Problem: SMD system shows false error  
- Impact: No production impact  

---

## Timeline
- Machine running normally → no abnormal  
- 15:07 → Alarm:
  - Runway2_Substrate 2D reader Readed Fault  
- PD handle error within 1 minute → machine normal  
- SMD system continues to record error status  
- 03/18 06:00 → SMD collected data  

---

## Symptom
- Machine working normally  
- Indicator light: GREEN  
- SMD system shows machine in error state  

---

## Root Cause
1. 2D reader read fault triggered  
2. Actual machine condition quickly recovered  
3. SMD system:
   - did not sync real-time machine state  
   - recorded incorrect alarm status  

👉 Result:
- **False alarm (system-level)**
- Not machine failure

---

## Failure Mechanism
- Signal chain:
