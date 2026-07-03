---
id: INC-2026-01-22-SAW73-BALL-VISION-ERROR-JIGSAW73
date: 2026-01-22
time: "08:50-11:10"
station: Jigsaw
machine: Jigsaw#73
model: C10.5S
issue_type:
  - Process
  - Mechanical
  - Vision
  - Blade
  - Panel condition
status: Recovered after blade replacement / Monitoring required
owner: EQ / ME / PD
tags:
  - jigsaw
  - saw73
  - ball-vision
  - 2nd-vision-stop
  - blade-cycle
  - panel-curvature
---

# SAW#73 – Ball Vision Error

## Issue
- Machine: Jigsaw#73
- Model: C10.5S
- Problem: Ball vision error
- Alarm: “2nd Vision Result Stop”
- Time: 08:50 AM, 22 Jan, 2026
- Fail Qty: 1 SIP

## Timeline
- Before issue:
  - Machine ran normally
- 22 Jan 08:50
  - Machine alarm:
    - “2nd Vision Result Stop”
- 08:55 → 10:50
  - EQ + ME checked machine parameters → No abnormal
  - Checked blade cycle time → abnormal (824 / 1100)
  - Checked SIP error position → located at panel corner
- 22 Jan 11:10
  - Replace blade
  - PD performed FAI OK
  - Machine returned to normal run

## Symptom
- Vision system stopped at second result verification.
- Error concentrated at corner of panel.
- 1 SIP failed.

## Root Cause
- Machine parameter:
  - Blade setting → OK
  - Vacuum → OK
  - Chuck table → OK
  - Nozzle → OK
- Abnormal findings:
  - Blade cycle time: 824 / 1100 → abnormal
  - SIP error at panel corner
- Conclusion (from slide):
  - End-of-cycle blade condition degraded
  - Panel curvature suspected → affecting cutting result

## Failure Mechanism
- Blade wear at end-of-cycle reduces cutting stability.
- Panel curvature introduces uneven contact during cutting.
- Combined effect leads to:
  - unstable cut edge
  - vision mismatch at 2nd inspection
- Result → “2nd Vision Result Stop” alarm triggered.

## Checks Performed
1. Check machine parameter → OK
2. Check blade setting → OK
3. Check vacuum → OK
4. Check chuck table → OK
5. Check nozzle → OK
6. Check blade cycle time → NG (824/1100)
7. Check SIP error position → panel corner

## Corrective Action
1. Replace blade
2. Run machine test
3. PD performed FAI → OK
4. Resume normal production

## Preventive Action
1. Control blade life by cycle count
2. Monitor end-of-cycle blade condition
3. Check panel flatness before cutting
4. Track vision NG at panel corner

## Current Status
- Blade replaced successfully
- FAI result: OK
- Machine running normally
- Monitoring ongoing

## Impact
- Quality: 1 SIP NG
- Production: short stop for troubleshooting and blade replacement
- Safety: not stated
- Repeat risk: medium if blade lifecycle and panel flatness not controlled

## Open Risk / Follow-up
- Need to define blade replacement threshold
- Need to monitor panel curvature from upstream
- Need to track recurrence of “2nd Vision Result Stop”

## Evidence
- Alarm: “2nd Vision Result Stop”
- Cycle time abnormal: 824 / 1100
- SIP error position at panel corner
- Replace blade → FAI OK → machine normal
