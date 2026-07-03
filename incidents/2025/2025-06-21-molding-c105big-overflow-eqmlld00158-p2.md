---
id: INC-2025-06-21-MOLDING-C105BIG-OVERFLOW-EQMLLD00158-P2
date: 2025-06-21
station: Molding
machine: EQMLLD00158
model: C10.5 Big
press: 2
issue_type:
  - Process
  - Mechanical
  - Clamp force
  - Cylinder
status: Recovered after temporary mold-chase move / cylinder replacement
owner: EQ
tags:
  - molding
  - c10.5-big
  - overflow
  - press2
  - left-side
  - clamp-force
  - cylinder
  - fai
---

# Molding C10.5 Big – Molding Overflow (Press 2)

## Issue
- Issue description: Molding Overflow
- Model: C10.5 Big
- Machine: EQMLLD00158 – Press 2
- Time: 6/21/2025

## Timeline (Press 2)
- 6/20 20:30 → Big clean
- 6/20 22:55 → FAI: OK
- 6/21 01:20 → Shot 20: Left side mold overflow
- 6/21 01:50 → Stop Press 2, EQ action:
  - check machine condition
- 6/21 02:50 → Move mold chase to Press 1
  - FAI OK
  - machine run normal

## Symptom
- Molding overflow happened on the left side at Press 2.
- Overflow appeared after FAI had already passed OK.
- The visible abnormal area was located at the left-side edge / gate side.

## Root Cause Analysis
1. Check balance
   - Test paper clamping → Normal

2. Check transfer pressure profile
   - Transfer profile followed recipe → Normal

3. Check clamp force
   - Left & Right different: 254 / 272 kN → Abnormal

## Root Cause
- Manual apply-high-clamp-force checking found that the left cylinder had a problem.
- Left-side clamp force was lower than right side.
- Difference between left and right clamp force was 254 / 272 kN.
- This difference was out of spec because it exceeded >10 kN.

## Failure Mechanism
- Overflow did not come from paper-clamping imbalance or transfer-profile abnormality, because both checks were normal.
- The abnormality was found in clamp-force imbalance.
- Since the left cylinder generated lower force than the right side, the mold-closing force distribution became uneven.
- This uneven clamping condition led to overflow at the left side during molding.

## Actions
1. Temporary move mold chase to Press 1
   - Run FAI OK
   - Recover production
2. Replace cylinder clamp force at Press 2

## Current Status
- Production was recovered by moving mold chase to Press 1 temporarily.
- Press 2 corrective action was defined as cylinder replacement.
- Current status: recovered under temporary action, with hardware corrective action required / executed for Press 2.

## Impact
- Quality: molding overflow at left side
- Production: Press 2 had to stop; production recovered through temporary move to Press 1
- Safety: not stated in the report
- Repeat risk: high if left/right clamp-force difference is not corrected

## Open Risk / Follow-up
- Need to verify left/right clamp-force balance after cylinder replacement
- Need to rerun FAI on Press 2 after replacement
- Need to monitor whether overflow reappears on left side after recovery

## Evidence
- Attached slides show:
  - timeline of overflow event
  - comparison photo of overflow vs normal panel
  - normal paper-test balance
  - normal transfer-pressure profile
  - clamp-force values 254 / 272 kN
  - action to move mold chase and replace cylinder
``
