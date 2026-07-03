---
id: INC-2025-04-16-MOLDING-C85BIG-OVERFLOW-EQMLD00154-P2
date: 2025-04-16
station: Molding
machine: EQMLD00154
model: C8.5 Big
press: 2
issue_type:
  - Process
  - Mechanical
  - Moldchase
  - O-ring
  - Cavity balance
status: Recovered after O-ring replacement / Monitoring
owner: EQ
tags:
  - molding
  - c8.5-big
  - overflow
  - press2
  - top-cavity
  - shim
  - cylinder
  - o-ring
  - cavity-balance
---

# Molding 8.5 Big – Molding Overflow (Press 2)

## Issue
- Issue description: Molding Overflow
- Model: C8.5 Big
- Machine: EQMLD00154 – Press 2
- Slide issue time shown: 4/14/2025

## Timeline (Press 2)
- 4/15 08:50 → Stop Press 2, EQ action
  - Insert shim on top cavity balance
- 4/15 13:15 → FAI: issue still mold overflow
- 4/15 17:30 → Stop Press 2, EQ action
  - Replace cylinder
- 4/15 22:50 → FAI: issue still mold overflow

## Symptom
- Molding overflow happened repeatedly on Press 2.
- Overflow pattern remained even after initial balancing action and cylinder replacement.

## Root Cause Analysis
1. Check balance
   - Test paper clamping → Normal

2. Check transfer pressure profile
   - Transfer profile followed recipe → Normal

3. Check cavity
   - Mold cavity had no foreign object → Normal

## Root Cause
- Press #2 overflow was caused by poor quality O-ring on the top chase.
- O-ring height was lower than standard.
- Lower-than-standard O-ring height made the cavity unbalanced.

## Failure Mechanism
- Because paper-clamping balance, transfer profile, and cavity foreign-object checks were normal, the issue was not attributed to transfer-force abnormality or cavity contamination.
- Mechanical corrective actions such as shim insertion and cylinder replacement did not eliminate the overflow.
- This indicates the imbalance source remained at top-chase sealing / geometry condition.
- The top-chase O-ring height being lower than standard reduced sealing / support uniformity and created cavity imbalance.
- That cavity imbalance caused repeated molding overflow on Press 2.

## Actions
1. Remove top cavity and clean
2. Check and tighten bolt on top cavity
3. Insert shim on top cavity to rebalance mold chase
4. Replace cylinder
5. Disassemble top mold chase of Press #2 and replace new O-ring
6. Return mold chase to Press #2 of machine #154
7. Run 5 shots FR4
   - Result: normal

## Current Status
- After replacing the top-chase O-ring and returning mold chase to Press #2, FR4 5-shot verification result was normal.
- Current status: recovered after O-ring replacement, continue monitoring.

## Impact
- Quality: repeated mold overflow on Press 2
- Production: multiple stop / FAI loop required before stable recovery
- Safety: not stated in the report
- Repeat risk: possible if top-chase O-ring quality / height control is not maintained

## Open Risk / Follow-up
- Need to monitor recurrence of overflow on Press 2 after O-ring replacement
- Need to verify O-ring height / quality control for top chase
- Need to include top-chase O-ring condition in mold-chase verification when repeated overflow appears

## Evidence
- Attached slides showing:
  - issue timeline with repeated FAI overflow
  - normal paper-test balance result
  - normal transfer pressure profile result
  - cavity no foreign object result
  - action list ending with top-chase O-ring replacement and FR4 normal result
