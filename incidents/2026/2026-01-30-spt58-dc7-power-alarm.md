---
id: INC-2026-01-30-SPT58-DC7-POWER-ALARM
date: 2026-01-30
time: "11:45 PM-12:30"
station: Sputter
machine: Sputter#58
model: C10.5
issue_type:
  - Electrical
  - Power
  - Cathode
  - DC7
status: Recovered after DC7 replacement / Monitor & vendor repair follow-up
owner: EQ / PD
tags:
  - sputter
  - spt58
  - dc7-power
  - alarm
  - cathode7
  - c10.5
---

# SPT#58 – DC7 Power Alarm

## Issue
- Machine: Sputter#58
- Model: C10.5
- Problem: DC7 Power Alarm
- Time: 11:45 PM, 30th Jan, 2026
- NG Qty: 0 SIP / tray

## Timeline
- Before issue:
  - Machine run normally
- 30 Jan 11:45
  - Machine alarm:
    - "DC7 Power Overload"
- 11:50 ~ 12:16
  - EQ checked Cathode 7 → OK
  - EQ checked DC7 power
  - Detect output value was NG
  - Cause of alarm identified from DC7 power side
  - Replace DC7 power
- 30 Jan 12:30
  - Machine run normal
  - PD do FAI OK

## Symptom
- While running normally, the machine alarmed:
  - ALM2856: DC7 Power Overload
- No SIP / tray NG was recorded.
- Machine required stop and DC7 power troubleshooting.

## Root Cause
- EQ checked Cathode#7 and found no abnormality.
- EQ checked DC7 power value and found abnormal output.
- The slide shows:
  - DC power value = 9.55 kΩ
  - Normal reference = ~245 kΩ
- Therefore, DC7 power was identified as the cause of alarm.

## Failure Mechanism
- The machine alarm was triggered because the DC7 power condition exceeded the allowable range.
- Cathode#7 separation was checked and found normal, so the issue was not traced to Cathode#7 body abnormality.
- The DC7 power output value was far from the normal reference.
- This abnormal electrical output caused the DC7 Power Overload alarm.
- After replacing the DC7 power unit, the machine resumed normal operation and completed the remaining 1 tray without abnormality.
- This confirms the alarm source was the DC7 power unit rather than the cathode itself.

## Actions
1. Check alarm on HMI:
   - ALM2856: DC7 Power Overload
2. Check Cathode#7
   - Result: OK (Separation)
3. Check DC power value
   - Result: abnormal
   - Measured value: 9.55 kΩ
   - Normal reference: ~245 kΩ
4. Replace DC7 power
5. Run machine again
6. Continue processing the remaining 1 tray
   - Result: no abnormal
7. PD do FAI OK

## Preventive / Follow-up Action
1. Keep monitoring machine after DC7 replacement
2. Bring out DC power broker / board to vendor for repair

## Current Status
- DC7 power was replaced
- Machine recovered at 12:30
- Remaining 1 tray was processed normally
- PD completed FAI OK
- Current status: recovered, continue monitoring

## Impact
- Quality: 0 SIP / tray NG
- Production: short interruption during troubleshooting and replacement
- Safety: not stated in the slide
- Repeat risk: possible if repaired / replacement DC7 power quality is not verified

## Open Risk / Follow-up
- Need to keep monitoring DC7 power condition after replacement
- Need vendor to repair / analyze the removed DC power unit
- Need to confirm no recurrence of ALM2856 after production restart

## Evidence
- Slide 1: issue summary and timeline for SPT#58 DC7 Power Alarm
- Slide 2: analysis showing Cathode#7 OK, DC7 power abnormal value 9.55 kΩ, replacement action, and recovery with FAI OK
