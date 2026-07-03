---
id: INC-2024-04-10-MOLDING-C85SMALL-MOLD-INCOMPLETE-EQMLD00146-P1
date: 2024-04-10
time: "16:00"
station: Molding
machine: EQMLD00146
model: C8.5 Small
press: 1
issue_type:
  - Process
  - Moldchase
  - Human
  - Transfer Pressure
status: Corrective action defined / Monitoring
owner: EQ / PD
tags:
  - molding
  - c8.5-small
  - mold-incomplete
  - press1
  - top-mold-chase
  - cull-stuck
  - transfer-pressure
  - tpc-alarm
  - small-cleaning
---

# Molding C8.5 Small Mold Incomplete – EQMLD00146 Press 1

## Issue
- Issue description: Mold incomplete
- Model: C8.5 Small
- Machine: EQMLD00146 – Press 1
- Time: 16:00 PM (10/04/2024)

## Timeline
- 04/10 11:03 → No WIP => machine stop
- 04/10 14:31 → PD run machine
  - SFIS error
  - machine cannot input by EAP
- 04/10 15:45 → Input FAI panel (Shot 1)
  - Machine alarm: Selector move error
  - EQ removed panel manually
  - FAI finished, result OK
- 04/10 16:04 → Input second panel (Shot 2)
  - Machine alarm: TPC pressure sensors not within range
  - Mold incomplete found

## Symptom
- Mold incomplete happened at Press 1 on C8.5 Small.
- Shot 1 completed after manual handling.
- Shot 2 then triggered TPC pressure-sensor-out-of-range alarm and showed mold incomplete.

## Root Cause Analysis
### 1. Check cull remain of Shot 2 after mold incomplete
- Abnormal cull found at position 4 and 5
- Higher 5 mm than normal cull
- Mold delamination observed

### 2. Check profile transfer pressure at Shot 2
- Transfer pressure at position 20 mm = 16 MPa
- Transfer pressure was out of spec
- Machine alarm: TPC pressure sensors not within range

### 3. Simulation by FR4
- Simulation showed cull stuck in top mold chase

## Root Cause
- Root cause: cull of Shot 1 was stuck in the top mold chase when machine ran Shot 2, which caused mold incomplete.

### Reason chain from the slide
- Machine stopped from 11:03 to 15:45 (total stop time 4h40')
- PD input the first panel without doing small cleaning
- MOI requires small cleaning when machine stop exceeds 2 hours
- Cull of Shot 1 was stuck in top mold chase because mold condition was not good
- At Shot 1, the machine alarm required manual panel removal from chase
- EQ handled the alarm but did not check the top mold chase carefully
- Shot 2 was then input while cull of Shot 1 remained stuck in top mold chase at position 4 and 5
- Transfer pressure became out of spec during mold transfer
- Mold incomplete then happened

## Failure Mechanism
- Because machine stop duration exceeded the cleaning threshold, mold condition should have been restored by small cleaning before restart.
- Restart was performed without the required cleaning.
- After Shot 1 alarm, panel was manually removed, but the top mold chase was not fully verified.
- Residual cull remained stuck in top mold chase at positions 4 and 5.
- During Shot 2, the stuck cull interfered with transfer behavior.
- Transfer pressure at position 20 mm rose to 16 MPa and triggered TPC pressure-sensor out-of-range alarm.
- This abnormal transfer condition caused mold incomplete.

## Actions
1. Do big cleaning at three presses to recover machine.
2. PD must follow MOI and perform small cleaning if machine stop is over 2 hours.
3. EQ must check top mold chase carefully by mirror when machine has alarm related to this kind of issue.
4. Training is required for all molding engineers on this checking behavior.
5. The report also notes a management action:
   - minus performance bonus of EQ member who was handling for the next 3 months

## Current Status
- Corrective actions were defined in the report.
- Recovery direction was based on big cleaning and stricter restart/inspection control.
- Current status: monitoring after corrective action and training requirement.

## Impact
- Quality: mold incomplete on Shot 2
- Production: restart delay and interruption after machine stop / alarm sequence
- Safety: not stated in the report
- Repeat risk: high if stop >2h cleaning rule and top mold chase inspection are not followed strictly

## Open Risk / Follow-up
- Need to ensure PD always executes small cleaning after stop > 2 hours
- Need to ensure EQ verifies top mold chase carefully after any related alarm
- Need to monitor repeat TPC pressure-sensor-out-of-range pattern on restart after long stop
- Need to confirm training effectiveness for molding engineers

## Evidence
- Attached issue slides showing:
  - machine-stop timeline
  - shot sequence and alarm sequence
  - abnormal cull at positions 4 and 5
  - transfer-pressure comparison
  - FR4 simulation showing cull stuck in the top mold chase
``
