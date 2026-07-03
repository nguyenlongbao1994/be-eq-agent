---
id: INC-2026-XX-XX-SAW58-DIMENSION-FAILED-JIGSAW58
date: 2026-XX-XX
station: Jigsaw
machine: EQSAW00058
model: C10.5
issue_type:
  - Process
  - Handling
  - Vacuum
  - Positioning
status: Containment done / Handling control required
owner: EQ / PD / Operator
tags:
  - jigsaw
  - saw58
  - dimension-failed
  - overlap-panel
  - unit-picker
---

# SAW#58 – The Dimension Failed

## Issue
- Machine: EQSAW00058
- Model: C10.5
- Problem:
  - 1 panel dimension failed
  - 1 panel not finished cutting
- Impact:
  - 26 pcs scrap
  - 19 pcs waiting for rework decision

---

## Timeline
- 08:30 AM
  - Perform FAI
- 01:56 PM
  - Unit picker pickup fail
- 01:57 PM
  - EQ manual by Tenkey
- 01:59 PM
  - Alarm: Z1 spindle load upper limit
- 02:15 PM
  - Ball vision alarm
  - Found 1 panel not finished cut
- 05:15 PM
  - Check CCTV + log file (Disco & Lamino)
- 08:15 PM
  - Cutting 2 bare panels, PD measurement OK
- 11:30 PM
  - Replace blade and resume production

---

## Symptom
- Unit picker failed to pick up panel
- Panel remained on chuck table
- Next panel loaded onto previous panel
- Result:
  - One panel overlapped
  - One panel cut twice → dimension NG
  - One panel not fully cut

---

## Root Cause
1. Unit picker pickup fail (vacuum not reached)
2. Product still remained on chuck but system memory cleared
3. Next panel was placed on top of previous panel
4. Two panels overlapped during cutting
5. Result:
   - Lower panel → cut twice → dimension fail
   - Upper panel → thrown out → not finished cutting

---

## Failure Mechanism
- Unit picker vacuum failure caused incomplete removal of finished panel
- System falsely assumed product removed → next cycle continues
- Panel stacking occurred (panel on panel)
- Cutting path misalignment occurred due to incorrect panel height / position
- This leads to:
  - double cutting on lower panel
  - incomplete cutting on upper panel
- Vision alarm triggered as secondary effect

---

## Actions
1. Check CCTV to identify incorrect handling
2. Manual troubleshooting unit picker vacuum condition
3. Reset machine status
4. Replace blade for stability
5. Continue cutting with verification panels
6. Confirm OK before resume production

---

## Preventive Action
1. Monitor unit picker vacuum performance
2. Add detection check for panel remaining on chuck
3. Improve interlock: block next panel if previous not removed
4. Train operator for abnormal condition handling
5. Add verification after pickup fail before restart

---

## Current Status
- Issue contained
- Cutting verified OK with test panels
- Production resumed
- Monitoring ongoing

---

## Impact
- Quality:
  - 26 pcs scrap
  - 19 pcs under evaluation
- Production: interruption and rework
- Safety: low
- Repeat risk: high if pickup fail not controlled

---

## Open Risk / Follow-up
- Need stabilize unit picker vacuum
- Need system logic improvement (no double load)
- Need review detection gap for panel presence
- Need confirm no repeat overlap pattern

---

## Evidence
- Alarm: Unit picker pickup fail
- Alarm: Z1 spindle load upper limit
- Vision alarm during process
- CCTV shows panel overlap
- Physical NG panels: double cut + incomplete cut
