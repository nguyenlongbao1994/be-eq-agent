---
id: INC-2026-01-27-SAW73-SCRATCHES-ON-PCB-SURFACE-JIGSAW73
date: 2026-01-27
station: Jigsaw
machine: Jigsaw#73
model: C10.5S
issue_type:
  - Mechanical
  - Process
  - Gap
  - Blade nozzle
status: Recovered after gap adjustment / Preventive check required
owner: EQ / ME / PD
tags:
  - jigsaw
  - saw73
  - scratches
  - pcb-surface
  - c10.5s
  - blade-nozzle
  - gap
---

# SAW#73 – Scratches on the PCB surface

## Issue
- Machine: Jigsaw#73
- Model: C10.5S
- Problem: Scratches on the PCB surface
- Time: 19:30 PM, 27th Jan 2026
- Fail Q’ty: 137 SIPs

## Timeline
- 27 Jan 19:30
  - PD visual SIP after Jigsaw process
  - Detected scratches on the PCB surface
- 27 Jan 19:35 ~ 21:00
  - EQ checked parameters of machine
  - No abnormal found
  - EQ checked gap between blade nozzle #1 and panel
  - Result: NG → identified as the cause of error
- 28 Jan
  - EQ combined with ME to check machine again
  - Adjusted GAP between nozzle #1 and panel to 4.3 mm
  - Ran 4 bare panels → OK
- 28 Jan 15:00
  - PD performed FAI OK
  - Visual check on 10 panels found no abnormal
  - Machine returned to normal run

## Symptom
- Scratches were found on the PCB surface after Jigsaw process.
- Mapping NG SIPs showed concentration on blade #1 side.

## Root Cause
- Machine recipe, blade setting, vacuum, chuck table position, and spindle were checked and found normal.
- The gap between blade nozzle #1 and panel was NG.
- This NG gap caused scratching on the PCB surface.

## Failure Mechanism
- If the gap between blade nozzle #1 and panel is too small or out of target, nozzle / blade-side structure can interfere with PCB surface during processing.
- Although machine parameters and spindle/vacuum conditions were normal, the mechanical clearance at blade nozzle #1 was not acceptable.
- This insufficient or abnormal gap created physical contact or friction effect on the PCB surface, producing scratches.

## Checks Performed
1. Check machine parameters → No abnormal
2. Check recipe → No abnormal
3. Check blade setting → No abnormal
4. Check vacuum → No abnormal
5. Check chuck table position → No abnormal
6. Check spindle → No abnormal
7. Check gap between blade nozzle #1 and panel → NG

## Corrective Action
1. EQ and ME adjusted the gap between blade nozzle #1 and panel to 4.3 mm
2. Ran test with 4 bare panels → OK
3. PD performed FAI → OK
4. Ran 10 panels and visual result was OK
5. Machine resumed normal production

## Preventive Action
1. Check other Jigsaw machines to ensure no similar abnormality exists
2. Must check the gap between blade nozzle and panel every time blade nozzle is adjusted

## Current Status
- Gap between blade nozzle #1 and panel was corrected to 4.3 mm
- 4 bare-panel test result was OK
- FAI was OK
- 10-panel visual verification was OK
- Machine returned to normal run

## Impact
- Quality: 137 SIPs failed due to scratches on PCB surface
- Production: machine required stop / investigation / re-adjustment
- Safety: not stated in the slide
- Repeat risk: possible if nozzle-to-panel gap is not checked after every blade-nozzle adjustment

## Open Risk / Follow-up
- Need to check all other Jigsaw machines for the same gap issue
- Need to enforce gap verification every time blade nozzle is adjusted
- Need to monitor recurrence specifically on blade #1 side

## Evidence
