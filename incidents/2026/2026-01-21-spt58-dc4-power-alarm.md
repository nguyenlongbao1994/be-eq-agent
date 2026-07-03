---
id: INC-2026-01-21-SPT58-DC4-POWER-ALARM
date: 2026-01-21
time: "13:19-13:40"
station: Sputter
machine: Sputter#58
model: C10.5
issue_type:
  - Electrical
  - Power
  - Cathode
  - DC4
status: Recovered after DC4 replacement / Monitor & vendor repair follow-up
owner: EQ / PD
tags:
  - sputter
  - spt58
  - dc4-power
  - alarm
  - cathode4
  - c10.5
---

# SPT#58 – DC4 Power Alarm

## Issue
- Machine: Sputter#58
- Model: C10.5
- Problem: DC4 Power Alarm
- Time: 13:19 PM, 21th Jan, 2026
- NG Q’ty: 0 SIP / trays

## Timeline
- Before issue:
  - Machine run normally
- 21 Jan 13:19
  - Machine alarm:
    - "DC4 Power high than limit set"
- 21 Jan 13:23 ~ 13:38
  - EQ checked Cathode 4 → OK
  - EQ checked DC4 power detect output value → abnormal
  - Cause of alarm identified from DC4 power side
  - EQ replaced DC4 power
- 21 Jan 13:40
  - Machine run normal
  - PD did FAI OK

## Symptom
- While running normally, machine alarmed:
  - ALM2631: DC4 Power high than limit set
- No SIP / tray NG was recorded.
- Machine required stop and DC4 power troubleshooting.

## Root Cause
- EQ checked the machine and confirmed Cathode 4 condition was OK.
- DC4 power detection output value was abnormal.
- Normal value shown in the slide note:
  - approximately 245 kΩ
- Because DC4 output value was abnormal, DC4 power unit was identified as the cause of alarm.

## Failure Mechanism
- The machine alarm was triggered by DC4 power value exceeding the allowable condition.
- Cathode 4 itself was checked and found normal, so the issue was not traced to Cathode 4 body separation.
- The abnormal DC4 output value indicates the DC4 power source / module was not providing expected electrical condition.
- Once the DC4 power was replaced, machine operation returned to normal and remaining trays were processed without abnormality.
- This confirms the alarm source was DC4 power module abnormality rather than product-side issue.

## Actions
1. Check alarm on HMI:
   - ALM2631: DC4 Power high than limit set
2. Check Cathode 4
   - Result: OK (Separation normal)
3. Check DC4 power value
   - Result: abnormal
4. Turn off CB of DC4
5. Replace DC4 power
6. Run machine again
7. Continue process remaining 3 trays
   - Result: no abnormal
8. PD performed FAI OK

## Additional Follow-up / Preventive Direction
1. Keep monitoring machine after DC4 replacement
2. Bring out the DC power board / broker to vendor for repair

## Current Status
- DC4 power was replaced
- Machine recovered at 13:40
- Remaining 3 trays were processed normally
- PD completed FAI OK
- Current status: recovered, continue monitoring

## Impact
- Quality: 0 SIP / trays NG
- Production: short interruption during troubleshooting and replacement
- Safety: not stated in the slide
- Repeat risk: possible if repaired / replacement DC4 power quality is not verified

## Open Risk / Follow-up
- Need to keep monitoring DC4 power condition after replacement
- Need vendor to repair / analyze the removed DC power board
- Need to confirm no recurrence of ALM2631 after production restart

## Evidence
- Slide 1: issue summary and timeline for SPT#58 DC4 Power Alarm
- Slide 2: analysis showing Cathode 4 OK, DC4 power abnormal value, replacement action, and recovery with FAI OK
