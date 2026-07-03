---
id: INC-2026-07-01-SPT58-EMERGENCY-STOP-ALARM
date: 2026-07-01
time: "04:40-07:30"
station: Sputter
machine: EQSPT00058
model: C10.5
issue_type:
  - Human
  - Safety
  - Emergency
  - Operation
status: Recovered after EMO reset / CCTV check required
owner: EQ / PD / FA
tags:
  - sputter
  - spt58
  - emergency-stop
  - emo
---

# SPT#58 – Emergency Stop Alarm

## Issue
- Machine: EQSPT00058
- Model: C10.5
- Problem: Emergency alarm → machine shut down
- Time: 04:40 AM, 01 July, 2026
- Impact: 2 Sputter Trays (336 pcs)

---

## Timeline
- 30-Jun 20:20 PM  
  - Perform FAI → OK  
- 01-Jul 04:40 AM  
  - Machine shut down  
- 01-Jul 06:10 AM  
  - Found EMO button at unloader was pressed  
- 01-Jul 07:30 AM  
  - Machine recovered → run normal → PD test OK  

---

## Symptom
- Machine sudden shutdown  
- No prior equipment fault alarm  
- Electrical system still partially active  

---

## Root Cause
1. EMO (Emergency Stop) button was pressed at unloader position  
2. No electrical or mechanical failure detected  
3. Confirmed:
   - Front cabinet power disconnected  
   - Rear power still active (380V / 220V)  
4. Final conclusion:  
   → **Human operation triggered emergency stop**

---

## Failure Mechanism
- EMO button breaks control circuit immediately  
- Machine logic triggers instant shutdown  
- Because:
  - EMO circuit is safety interlock  
  - No condition checking required  
- System stops regardless of machine state  

---

## Actions
1. Verify electrical system → OK  
2. Check emergency buttons  
3. Identify pressed EMO at unloader  
4. Reset EMO  
5. Restart machine  
6. PD perform test tray → OK  

---

## Corrective Action
1. Recover machine and test  
2. Remove affected trays for inspection / rework  

---

## Preventive Action
1. Check CCTV to identify who pressed EMO  
2. Reinforce operator training:
   - EMO usage strictly controlled  
3. Add label / guard if needed to avoid accidental press  

---

## Current Status
- Machine recovered  
- Test tray OK  
- Production resumed  
- Root cause confirmed (Human error)

---

## Impact
- Quality: 2 trays impacted  
- Production: ~3 hours downtime  
- Safety: EMO function working correctly  
- Repeat risk: HIGH (if no control on operator action)

---

## Open Risk / Follow-up
- Need CCTV verification  
- Need operator training reinforcement  
- Need evaluate EMO accessibility risk  

---

## Evidence
- Timeline shows no machine fault before shutdown  
- EMO button found pressed at unloader  
- Electrical check normal  
- Restart confirmed stable operation  
