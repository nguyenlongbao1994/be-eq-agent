---
id: INC-2026-06-05-MOLDING-CAVITY-VACUUM-BEFORE-TRANSFER-ERROR-EQMLD000146
date: 2026-06-05
station: Molding
machine: EQMLD000146
model: C10.5 N244S
press: 3
issue_type:
  - Process
  - Vacuum
  - Moldchase
  - Maintenance
status: Corrective action completed / Verification in day shift
owner: EQ
tags:
  - molding
  - c10.5-n244s
  - cavity-vacuum
  - before-transfer-error
  - moldchase
  - press3
  - o-ring
  - eqmld000146
---

# Molding 146 – Cavity vacuum before transfer error

## Issue Description
- Model: C10.5 N244S
- Station: Molding
- Machine: EQMLD000146
- Customer impact: No impacts
- Containment action: Stop Press 3 temporarily and keep running Press 1 and Press 2

## Timeline
- 04/06/2026 20:15 → PD big clear
- 05/06/2026 00:00 → Machine FAI => OK
- 05/06/2026 02:00 → Press 3 alarm:
  - "Cavity vacuum before transfer error"
- 05/06/2026 02:20 → Continue production with Press 1 & Press 2
- 05/06/2026 04:00 → Swapped mold chase from Press 2 to Press 3 and continued production

## Symptom
- Press 3 triggered alarm: cavity vacuum before transfer error.
- Alarm still occurred after basic cleaning inside mold chase.
- Production had to continue using only 2 presses temporarily.

## Root Cause Analysis
### 1. Check machine error log
- Log line shown on slide:
  - 06/05/2026 01:59:24
  - PR33
  - Cavity vacuum error before transfer
  - CV error before transfer (5203)

### 2. Checking mold chase area
- EQ checked and cleaned the inside of mold chase using a brush
- Then tried production one more time
- Result:
  - alarm still occurred

### 3. Checking vacuum manually
- Manual vacuum check performed using FR4
- Vacuum value was normal:
  - < 30 hPa

### 4. Check Press #3 by mold-chase swap
- Swapped the mold chase from Press 2 to Press 3 for checking
- Result:
  - product ran normally

## Root Cause
- Mold chase was identified as the issue source.
- Mold chase required maintenance and replacement of all O-rings.

## Failure Mechanism
- The alarm was not caused by general vacuum-system loss because manual vacuum value checked by FR4 was normal (<30 hPa).
- Cleaning the mold-chase area also did not eliminate the alarm.
- When the mold chase from Press 2 was swapped into Press 3, the product ran normally.
- This indicates the specific mold chase originally used at Press 3 had an internal sealing / maintenance issue.
- The most likely physical cause in the slide conclusion is mold-chase sealing degradation requiring O-ring replacement.

## Corrective Actions
### Short term corrective action
1. Temporarily continue production with 2 presses — Done
2. Re-perform maintenance on mold chase of Press 3 and replace all O-rings — Done

### Long term corrective action
1. Re-input mold chase in day shift to verify result after maintenance — Jun/05

## Current Status
- Production was maintained temporarily with Press 1 and Press 2.
- Mold chase of Press 3 was maintained and all O-rings were replaced.
- Follow-up verification in day shift was planned / required after maintenance.

## Impact
- Quality: no direct customer impact stated
- Production: Press 3 had to be stopped temporarily
- Safety: not stated on the slide
- Repeat risk: possible if mold-chase seals / O-rings degrade again and are not renewed during maintenance

## Open Risk / Follow-up
- Need to verify Press 3 mold chase result in day shift after re-input
- Need to monitor recurrence of cavity vacuum before transfer error on the same mold chase
- Need to maintain O-ring replacement discipline during mold-chase maintenance

## Evidence
- Attached slide showing issue description, timeline, machine log snippet, mold-chase area photo, and manual cavity vacuum check screen
