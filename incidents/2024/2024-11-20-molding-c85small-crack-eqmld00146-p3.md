---
id: INC-2024-11-20-MOLDING-C85SMALL-CRACK-EQMLD00146-P3
date: 2024-11-20
time: "02:26-06:45"
station: Molding
machine: EQMLD00146
model: C8.5 Small
press: 3
issue_type:
  - Process
  - Human
  - Moldchase
  - Transfer Time
status: Corrective action defined / Monitoring
owner: EQ / PD
tags:
  - molding
  - c8.5-small
  - crack
  - press3
  - moldchase
  - conditioning
  - top-cavity
  - transfer-time
  - max-transfer-time
---

# Molding C8.5 Small – Molding Crack (Press 3)

## Issue
- Issue description: Molding Crack
- Model: C8.5 Small
- Machine: EQMLD00146 – Press 3
- Time range: 02:26 – 06:45 (11/20/2024)

## Timeline
- 11/19 20:15–22:40 → Big Cleaning
- 11/19 22:45 → FAI, no abnormal
- 11/20 02:26 → Issue happened
  - Shot: 65
  - Press #3: Right
  - NG: 1 pcs
  - PD cannot detect by visual inspection
- 11/20 06:46 → Machine standby at shot 107
- Total NG in slide: 123 pcs NG

## Symptom
- Molding crack occurred on C8.5 Small at Press 3.
- Initial NG was very small and could not be detected by visual inspection.
- Issue accumulated until total NG shown in report reached 123 pcs.

## Root Cause
- OP forgot to supply conditioning compound into mold chase at the last conditioning step.
- Because the last conditioning step was missed, the conditioning layer of the mold chase was not good.
- After molding, the top of the panel stuck on the top cavity.
- When the mold opened, a release force acted on the panel surface.
- This release force caused molding crack.
- The crack was very small and could not be inspected visually at the beginning.

## Failure Mechanism
- Mold chase requires correct conditioning-compound supply at the final conditioning step to form a stable release layer.
- Because the final conditioning step was missed, the release condition of the top cavity became poor.
- After molding completion, the panel surface adhered / stuck to the top cavity.
- When the mold opened, separating force was applied on the stuck panel surface.
- This force created very small molding crack that escaped early visual detection.

## Supporting Process Observation from EQ Action Slide
- Actual transfer time depends on actual pellet length or pellet missing.
- Machine compares actual transfer time against maximum transfer time in recipe.
- If actual time exceeds maximum transfer-time setting, the machine alarms.

## EQ Actions
1. Adjust parameter in recipe: **Maximum transfer time**
   - Previous value shown in slide: 16 s
   - Changed value shown in slide: >= 18.5 s

2. Training for PD when the machine reports:
   - "Max transfer time exceeded"

3. EQ must check transfer profile for all steps of Big Cleaning before doing FAI panel and sign on checksheet.
   - ME / IPQC double confirm and sign on checksheet.

## Current Status
- Corrective actions were defined in the report:
  - increase maximum transfer time
  - add PD training for max-transfer-time alarm
  - require EQ/ME/IPQC check-sheet confirmation before FAI after Big Cleaning
- Current status: monitoring after corrective action.

## Impact
- Quality: molding crack issue, total 123 pcs NG shown in slide
- Production: issue continued from shot 65 until machine standby at shot 107
- Safety: not stated in the report
- Repeat risk: high if conditioning step is missed again or if transfer-time abnormality is not controlled

## Open Risk / Follow-up
- Need to ensure OP executes final conditioning-compound supply step every time
- Need EQ to verify transfer profile after Big Cleaning before FAI
- Need PD training effectiveness on "Max transfer time exceeded" alarm
- Need to monitor whether small crack can still escape visual inspection and require stronger detection method

## Evidence
- Attached slides showing:
  - issue timeline
  - recipe maximum transfer time change
  - alarm examples for max transfer time exceeded
  - training/checksheet action evidence
