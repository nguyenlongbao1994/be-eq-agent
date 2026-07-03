---
id: INC-2025-07-03-ATTIS-LASER155-EXTERNAL-GATE-DISABLE-EQLAS00155
date: 2025-07-03
time: "21:15-21:25"
station: Laser
machine: EQLAS00155
model: Attis
issue_type:
  - Control
  - Software
  - Laser head
  - Interlock
status: Vendor check pending / Software preventive action required
owner: EQ / Vendor / JQ expert
tags:
  - attis
  - laser155
  - external-gate-disable
  - spectra-physics
  - interlock
  - laser-head
  - software
---

# Attis Laser #155 – External Gate Disable

## Issue
- Issue: External gate disable
- Q’ty NG: 5 SIPs under ME checking
- Model: Attis
- Machine: EQLAS00155
- Time: 21:23, 03 July 2025

## Timeline
- 21:15 03/07 → Power check is normal
- 21:23 03/07 → Run FAI, machine alarm:
  - "External gate disable"
  - detected 5 SIPs NG
- 21:25 03/07 → Stop machine #155 to check and find root cause

## Symptom
- During FAI, machine #155 triggered alarm "External gate disable".
- 5 SIP NG were detected.

## Root Cause
1. Check logfile:
   - Log recorded: "Laser Status Error => External Gate Disable"
2. Check "spectra-physics" program controlling the laser head:
   - External gate status: disable
   - QSW (Hz) value: 100000 Hz
   - Power check value: 12.03 W

### Root cause conclusion
- External gate in disabled status caused the laser computer to lose automatic control of laser beam close/open.
- Laser power stayed ON.

## Failure Mechanism
- The external gate function is part of the laser-head control / interlock logic.
- When external gate status became disabled in the spectra-physics control program, the laser computer could not automatically command the beam to close/open as required by machine sequence.
- Because of this control-state abnormality, laser power remained ON and the FAI run produced the same defect symptom that was later confirmed again by simulation.

## Actions
1. Simulation:
   - When external gate was disabled, test with bare panel showed the same symptom as the real issue.
2. CCTV review:
   - Checked CCTV at issue time 21:23 while machine was in automatic mode.
   - At 21:15 EQ checked laser power, but the slide notes that clear action could not be seen at that time.
3. Vendor / JQ expert support:
   - Check with vendor and JQ expert to find the real reason why external gate became disabled in spectra-physics program.
   - Need to determine whether disable happened by manual action or automatically.
   - Checkpoint: 7/4
4. Software preventive action:
   - Check with vendor to update software to prevent the issue.
   - Requirement: all functions need to be enabled before machine start.
   - Checkpoint: 7/4

## Current Status
- Physical issue was reproduced in simulation when external gate was disabled.
- Root-cause direction points to software / control-state problem in spectra-physics / external gate status.
- Vendor and JQ expert follow-up is still required.

## Impact
- Quality: 5 SIP NG detected
- Production: FAI interrupted by external gate disable alarm
- Safety: laser power always ON is a control / interlock risk
- Repeat risk: high until root cause of external-gate disable and preventive software action are confirmed

## Open Risk / Follow-up
- Need vendor confirmation whether external gate disable was manual or auto-triggered
- Need software update / preventive setting if vendor confirms fix path
- Need startup checklist to confirm all control functions enabled before machine start
- Need continued monitoring of external gate state during FAI / startup

## Evidence
- Attached slides show:
  - issue summary and timeline
  - logfile line “Laser Status Error => External Gate Disable”
  - spectra-physics screen with external gate status = disable
  - QSW value 100000 Hz
  - power check value 12.03 W
  - action plan for vendor / software review
