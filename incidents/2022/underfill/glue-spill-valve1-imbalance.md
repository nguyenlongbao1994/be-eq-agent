# Glue spill at PCB due to Valve 1 imbalance (UF-135#)

## Basic Info
- Date: 2022-01-11
- Station: Underfill
- Machine: UF-135#
- Issue Type: Mechanical / Process
- Impact: Quality defect, production disturbance
- Status: Closed (after needle replacement)

---

## Issue
Underfill machine UF-135# experienced glue spill at PCB location during production (12:30–15:00).  
Glue overflow observed at Valve 1 position causing contamination risk.

---

## Impact
- Quality: Glue spill → PCB contamination risk
- Production: Machine interruption during troubleshooting
- Process: Unstable dispensing condition between valves
- Risk: High repeat risk if imbalance persists

---

## Root Cause
### Confirmed
- Glue weight at Valve 1 higher +0.08 mg/dot vs Valve 2 (spec < 0.05 mg/dot)
- Needle at Valve 1 worn more severely than Valve 2

### Failure Mechanism
Needle wear → enlarged flow path → increased glue per dot → exceeding spec  
→ accumulation → glue spill on PCB

---

## Actions

### Containment
- Replace worn needle at Valve 1
- Resume production after normalization (15:00)

### Corrective
- Check valve dot weight balance before machine setup
- Verify needle condition prior to run

### Preventive
- Implement needle lifetime tracking
- Define wear limit and replacement criteria
- Add pre-run validation for multi-valve balance

---

## Risk
- High repeat risk due to gradual needle wear
- No automatic detection of valve imbalance
- Potential batch defect if not detected early

---

## Next Step / Owner
- Owner: EQ / Process Engineer (EQ/Leo)
- Deploy needle lifetime monitoring system
- Standardize checklist before production start
- Audit similar machines for same failure pattern

---

## Pattern Tag
- Glue instability
- Mechanical wear
- Multi-valve imbalance
- Process drift

---

## Lesson Learned
- Multi-valve systems must control balance, not just individual output
- Needle wear is gradual → requires proactive monitoring
- Passing FAI does not guarantee long-term process stability
