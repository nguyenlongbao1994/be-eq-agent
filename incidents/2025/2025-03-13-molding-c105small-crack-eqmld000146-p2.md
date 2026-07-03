---
id: INC-2025-03-13-MOLDING-C105SMALL-CRACK-EQMLD000146-P2
date: 2025-03-13
time: "06:55-12:40"
station: Molding
machine: EQMLD000146
model: C10.5 Small
press: 2
issue_type:
  - Process
  - Mechanical
  - Cull
  - Anti-warpage
status: DOE planned / Modification pending
owner: EQ / PT Lab
tags:
  - molding
  - c10.5-small
  - crack
  - press2
  - cull
  - knife
  - anti-warpage
  - gate-row
  - hollow-out
---

# Molding C10.5 Small – Molding Crack (Press 2)

## Issue
- Issue description: Molding Crack
- Model: C10.5 Small
- Machine: EQMLD000146 – Press 2
- Date: 3/13/2025
- Quantity NG: 5 pcs

## Timeline
- 3/13 06:55–09:30 → Big Cleaning
- 3/13 09:45 → FAI normal
- 3/13 12:15 → Issue happened
  - Shot: 16
  - Press #2: Left
  - NG: 5 pcs at the same location
  - PD could not detect by visual inspection
- 3/13 12:40 → Small clean
- Slide note shows total 5 SIP NG during the issue window

## Symptom
- Molding crack occurred on C10.5 Small at Press 2.
- 5 pcs / 5 SIP NG were found at the same location.
- PD could not detect the crack clearly by visual inspection at the beginning.

## Root Cause
- When the knife cut the cull together with the panel, a small remaining cull was left.
- The small remaining cull dropped onto the panel.
- Then the compound handler pushed the panel from mold chase to leadframe handler.
- During this transfer, the small remaining cull dropped onto the top surface of the panel.
- This interaction caused molding crack.

## Failure Mechanism
- A knife-cut event left a small residual cull.
- The residual cull dropped and landed on panel surface.
- During panel transfer from mold chase to leadframe handler, the remaining cull interfered with the panel.
- Local mechanical contact / pressure from the dropped small cull created repeated crack at the same position.
- Because the crack was very small, initial visual detection by PD was difficult.

## Action
### Modify anti-warpage surface
1. Small cull almost only falls in the Gate row.
2. Modify anti-warpage surface with hollow out at Gate-side position.
3. Anti-warpage must not touch PCB surface at Gate side, but still must be sufficient to prevent PCB warpage.
4. Bring to PT Lab to modify.
   - Checkpoint: 14/March
5. DOE with Small model first, then apply to Big model.

## Proposed Modification Dimensions
- Hollow out for big model:
  - X = 23.5 mm
  - Z = 0.8 mm
- Hollow out for small model:
  - X = 25.3 mm
  - Z = 0.8 mm

## Current Status
- Root cause direction identified as residual small cull dropping onto panel.
- Corrective direction is anti-warpage modification with hollow-out at Gate side.
- PT Lab modification and DOE were planned.
- Current status: modification pending / DOE planned.

## Impact
- Quality: 5 pcs / 5 SIP NG shown in the slide
- Production: issue occurred after FAI normal and required small-clean action
- Safety: not stated in the report
- Repeat risk: high until anti-warpage modification is completed and DOE confirms effectiveness

## Open Risk / Follow-up
- Need PT Lab to complete anti-warpage modification
- Need DOE verification on Small model first
- Need confirmation before applying same concept to Big model
- Need monitoring of repeat crack at same location after modification

## Evidence
- Attached slides show:
  - issue summary and timeline
  - root-cause mechanism diagram with knife / cull / panel / small cull
  - before/after anti-warpage modification concept with hollow-out dimensions
