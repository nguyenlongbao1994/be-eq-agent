---
id: INC-2026-04-17-JIGSAW58-WATER-PRESSURE-TANK-LEAK-EQSAW00058
date: 2026-04-17
time: "21:50"
station: Jigsaw
machine: EQSAW00058
model: C10.5
issue_type:
  - Utility
  - Mechanical
  - Water system
  - Tank
status: Recovered after tank replacement / Leak monitoring required
owner: EQ / FA team
tags:
  - jigsaw
  - saw58
  - water-leak
  - di-water
  - pressure-tank
---

# Jig saw #58 – Water Pressure Tank Leak Issue

## Issue
- Machine: Jigsaw#58
- Model: C10.5
- Problem: Water pressure tank broken
- Time: 21:50 (17 Apr, 2026)

## Symptom
- Water leakage observed on floor near machine
- DI water leaking under high pressure
- Machine still running → no alarm triggered

## Root Cause
- DI water pressure tank was broken
- Equipment transferred from JQ (since 2021)
- Water still remained in system → pressure maintained
- No sensor / logic to detect tank failure → no alarm
- Leak only visible outside system

## Failure Mechanism
- Tank damage → high-pressure water escapes
- System still has internal pressure → continuous leakage
- Machine control does not monitor tank integrity
- Result:
  - No alarm
  - External leak only

## Actions
1. Leakage sensor alarm → EQ followed OCAP and closed main water valve
2. FA team installed new water pressure tank
3. Checked machine parameters
4. Performed FAI → OK
5. Resume production

## Current Status
- Tank replaced
- Leakage stopped
- Machine passed FAI
- Running normally

## Impact
- Quality: Not stated
- Production: short stop
- Safety: water leak → slip / electrical hazard risk
- Repeat risk: high if tank aging not controlled

## Preventive Action
1. Add periodic inspection for pressure tank condition
2. Define replacement lifetime (tank from 2021)
3. Strengthen leak detection system
4. Add DI water system checklist

## Open Risk / Follow-up
- Need monitor new tank performance
- Audit similar machines using same tank type
- Check corrosion / fatigue risk

## Evidence
- Photo shows water leakage on floor
- Tank damage visible
- Control panel shows no alarm
- New tank installed
