---
id: INC-2023-12-11-MOLDING-C85BIG-SHIFT-EQMLD000147
date: 2023-12-11
station: Molding
machine: EQMLD000147
model: C8.5 Big
issue_type:
  - Mechanical
  - Process
  - Clamp
  - Cylinder
  - Positioning
status: Monitoring after action
owner: EQ
tags:
  - molding
  - c8.5-big
  - shift
  - clamp-force
  - cylinder
  - logfile
  - reposition
  - press1
  - press2
---

# Molding C8.5 Big Shift – EQMLD000147

## Issue Summary
- Title on report: Molding C8.5 Big Shift
- File reference shown in slide: Molding logfile
- Main concern: repeated molding shift events appeared together with clamp-force-related abnormal events in the machine timeline.

## Timeline Alarm / Logfile Summary
### 2023-12-11
- 22:00 → Press #2 alarm: cavity vacuum error
- 22:15 → Swap mold chase between Press #2 and Press #1 to solve cavity-vacuum alarm
- 22:36 → 1st error: clamp-force-related error
- 23:05 → No.1 SIP: molding shift

### 2023-12-12
- 22:15 → Maintenance performed at Press #1 and #2

### 2023-12-13
- 04:38 → No.201 SIP: molding shift

### 2023-12-14
- 02:34 → Last time error: clamp-force-related error
- 03:30 → Changed cylinder clamp force
- After this point, the slide states: no further clamp-force and molding-shift issue happened

## Symptom
- Molding shift happened repeatedly on C8.5 Big.
- Machine logfile showed repeated clamp-force-related abnormal signals before / around the molding-shift events.

## Root Cause Status
- The slides do not provide one explicit root-cause sentence in the same way as other reports.
- However, the timeline and action set indicate that the issue was associated with clamp-force / cylinder condition and panel positioning in mold chase.

## Failure Mechanism (based on timeline + action logic in report)
- Clamp-force-related abnormality was repeatedly recorded in the machine timeline.
- Molding shift events occurred after these clamp-force abnormalities.
- The later corrective action focused on:
  - changing the right cylinder of Press #1
  - adding leadframe reposition function after pellet drop
  - training EQ to double-check cylinder condition when “Right Clamp force release” alarm appears
  - adding cylinder maintenance and clamp-force alarm control into standard control system
- This indicates the issue was treated as a combination of:
  - clamp / cylinder condition abnormality
  - leadframe / PCB positioning instability before mold chase close

## Actions
### 1. Immediate production control
- 12/14 20:00: stop input at machine EQMLD000147
- Production was changed to machine EQMLD000154
- Changed right cylinder of Press #1

### 2. Add function: "reposition lead frames after pellet drop"
- Pusher will move into the mold chase
- Purpose: check and push PCB into correct position again before mold chase closes

### 3. Training action
- Train EQ engineer that when machine alarm "Right Clamp force release" appears,
  cylinder condition must be double-checked

### 4. Maintenance action
- Add cylinder maintenance item into 6-month maintenance checksheet
- Note in slide: before this, cylinder lifetime was not defined

### 5. Alarm-list improvement
- Add more "clamp force alarm" entries into molding alarm list

## Working Principle Added in Report
The slide shows the intended sequence:
1. Panel pushed into mold chase
2. Compound handle moves into mold chase to supply compound
3. Compound handle moves out of mold chase
4. Pusher moves into the mold to align PCB again
5. Mold chase closes

The added function specifically reinforces step 4.

## Current Status
- Right cylinder of Press #1 was changed
- Reposition function was added
- EQ training action was defined
- Cylinder maintenance control and alarm-list improvement were added
- Report note states that after clamp-force change, no further clamp-force or molding-shift issue happened in the shown timeline

## Impact
- Quality: molding shift issue affected product stability
- Production: machine input was stopped and production moved to another machine during containment
- Safety: not stated in the report
- Repeat risk: reduced after action, but still requires monitoring because the control strategy was expanded beyond one single replacement action

## Open Risk / Follow-up
- Need to continue monitoring whether clamp-force-related alarms recur
- Need to verify reposition function remains effective in preventing incorrect PCB / leadframe position before mold chase close
- Need to ensure cylinder lifetime control is sustained in periodic maintenance
- Need to ensure clamp-force alarm list is updated and used correctly by EQ / PD

## Evidence
- Attached slides show:
  - molding logfile timeline
  - action slide with cylinder change and reposition function
  - maintenance / SOP / alarm-list update evidence
``
