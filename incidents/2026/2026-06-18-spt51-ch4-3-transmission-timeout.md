---
id: INC-2026-06-18-SPT51-CH4-3-TRANSMISSION-TIMEOUT
date: 2026-06-18
time: "19:34-21:00"
station: Sputter
machine: EQSPT00051
model: C10.5
issue_type:
  - Mechanical
  - Transmission
  - Motor
  - Coupling
status: Recovered after coupling reinstall & driver replacement
owner: EQ
tags:
  - sputter
  - ch4-3
  - transmission-timeout
  - coupling
  - motor-driver
---

# SPT – CH4-3 Transmission Timeout Alarm

## Issue
- Machine: EQSPT00051
- Model: C10.5
- Problem: CH4-3 transmission timeout alarm
- Time:
  - Start: 18 June 19:34 PM
  - Recovery: 18 June 21:00 PM
- Impact:
  - 1 Sputter Tray (336 pcs)

---

## Timeline
- 18 June 08:10 AM  
  - Perform FAI → OK
- 18 June 19:34 PM  
  - Alarm: CH4-3 transmission timeout
- 19:40 PM  
  - Stop machine and manual check CH4-3 conveyor
- 19:50 PM  
  - Check motor coupling position
- 21:00 PM  
  - Reinstall coupling
  - Machine run normal
  - FAI OK

---

## Symptom
- Machine alarmed CH4-3 transmission timeout
- Conveyor movement abnormal
- Motor drive communication error observed

---

## Root Cause
1. Motor coupling loosened and disengaged from conveyor shaft  
2. Cause of loosening:
   - Fixing screw damaged  
3. Long-term rubbing between coupling and shield caused:
   - Mechanical wear  
   - Detachment of coupling  

Additional effect:
- Motor Driver communication error triggered due to unstable transmission

---

## Failure Mechanism
- Coupling transmits torque from motor → conveyor
- When fixing screw loosens:
  - Coupling shifts position
  - Misalignment occurs
- Continued rubbing:
  - Weakens coupling structure
  - Eventually disengages
- Result:
  - Conveyor stops
  - Motor runs without load
  - System detects mismatch → timeout alarm
  - Communication error follows

---

## Corrective Actions
1. Reinstall motor coupling — DONE  
2. Clean sputter chamber — DONE  
3. Replace motor driver — DONE  
4. Send tray to SPT#50 for rework — DONE  

---

## Preventive Actions
1. Sort and replace all fixing screws during next maintenance  
2. Add inspection item for:
   - Coupling condition  
   - Fixing screw integrity  
3. Update MTN checklist:
   - Transmission guide coupling check  

Target:
- Implement by checkpoint 6/19

---

## Current Status
- Coupling reinstalled  
- Motor driver replaced  
- Machine recovered  
- FAI passed  
- Production resumed  

---

## Impact
- Quality: 1 tray impacted (rework needed)  
- Production: ~1.5 hour downtime  
- Safety: mechanical wear risk  
- Repeat risk: HIGH if screw integrity not controlled  

---

## Open Risk / Follow-up
- Need audit all coupling connections in Sputter machines  
- Need define torque & inspection standard for fixing screw  
- Need monitor repeat CH4-3 error  

---

## Evidence
- Alarm log: CH4-3 transmission timeout  
- Visual: coupling displacement  
- Mechanical damage on fixing screw  
- Motor driver communication error  
``
