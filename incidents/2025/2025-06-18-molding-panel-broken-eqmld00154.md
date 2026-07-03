---
id: INC-2025-06-18-MOLDING-PANEL-BROKEN-EQMLD00154
date: 2025-06-18
station: Molding
machine: EQMLD00154
model: C8.5 Small
issue_type:
  - Mechanical
  - Human
  - Handling
  - Brake shaft
status: Recovered / Training corrective defined
owner: EQ / ME / PD
tags:
  - molding
  - panel-broken
  - brake-shaft
  - anti-warpage
  - leadframe-handler
  - cassette
  - big-cleaning
  - air-gun
---

# Molding machine #154 – Issue Panel broken

## Issue
- Issue: Panel broken
- Abnormal Qty: 3 pcs scrap
- Model: C8.5 Small
- Machine: EQMLD00154
- Time: 18th Jun 2025

## Timeline
- 22:53 → Start FAI machine #154
- 23:03:22 → Machine alarm:
  - "Error while pushing leadframe into the cassette"
- 1 PCB broken at leadframe handle
- PD called EQ and ME to handle the problem

## Symptom
- Panel broken happened during movement from leadframe handler to cassette.
- Machine alarm appeared while pushing leadframe into the cassette.
- Scrap quantity recorded in the slide: 3 pcs.

## Root Cause
- Brake shaft position inside anti-warpage showed abnormal difference between left side and right side.
- Panel broken happened at right side.
- During movement from leadframe handler to cassette, the brake shaft did not clamp the PCB in a fixed position.
- In Big Cleaning before production, OP cleaned anti-warpage of leadframe handle and used air gun to blow directly at the brake shaft.
- The direct air-gun action caused brake shaft position to become offset from normal.
- Because brake shaft position became offset, the brake shaft could not clamp the panel PCB correctly.

## Failure Mechanism
- Brake shaft inside anti-warpage is used to clamp and stabilize the panel during the transfer path from leadframe handler to cassette.
- After OP used air gun directly during Big Cleaning, the brake shaft shifted from its correct position.
- Because the brake shaft was offset, PCB was not clamped firmly during transfer.
- While moving toward cassette, the unstable panel position led to panel broken at the right side.

## Actions
1. Re-fix brake shaft position to recover proper clamping.
2. Test by dummy bare PCB.
3. Result after re-fix: machine can run normally.
4. Train OP on molding work instruction for correct anti-warpage cleaning method.
5. Corrective emphasis: avoid direct air-gun blow that can shift brake shaft position.

## Current Status
- Brake shaft position was re-fixed.
- Dummy bare PCB test confirmed normal machine running.
- Corrective training for OP was required / initiated.

## Impact
- Quality: 3 pcs scrap
- Production: FAI / machine run interrupted by panel-broken issue
- Safety: not stated in the slide
- Repeat risk: possible if anti-warpage cleaning method is not controlled

## Open Risk / Follow-up
- Need to ensure OP follows corrected anti-warpage cleaning method
- Need to monitor brake shaft position stability after cleaning
- Need to verify no recurrence of right-side panel broken during cassette transfer

## Evidence
- Attached slides showing:
  - issue summary and alarm timing
  - left side OK vs right side NG brake shaft position
  - actual image when PD used air gun to clean anti-warpage
  - before / after brake shaft position recovery
  - action note for OP training
