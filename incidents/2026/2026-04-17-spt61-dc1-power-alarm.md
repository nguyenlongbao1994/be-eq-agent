---
id: INC-2026-04-17-SPT61-DC1-POWER-ALARM
date: 2026-04-17
time: "02:15-04:00"
station: Sputter
machine: Sputter#61
model: Attis
issue_type:
  - Electrical
  - Power
  - Cathode
  - Clamp
status: Recovered after clamp replacement / Vendor surface control required
owner: EQ / PD
tags:
  - sputter
  - spt61
  - dc1
  - power-alarm
  - cathode1
  - clamp
---

# SPT#61 – DC1 Power Alarm

## Issue
- Machine: Sputter#61
- Model: Attis
- Problem: DC1 Power Alarm
- Time: 02:15 PM, 17 Apr, 2026
- NG Qty: rework 1 tray → OK

---

## Timeline
- Before issue:
  - Machine run normally
- 17 Apr 02:15
  - Machine alarm:
    - "DC1 Power alarm"
- 02:15 ~ 04:00
  - EQ manual check DC1 → NG
  - EQ check Cathode 1 → Short cathode
  - Stop machine
  - Clean and replace clamp of cathode 1
- 17 Apr 04:00
  - Machine run normal
  - PD perform FAI OK

---

## Symptom
- Machine alarmed DC1 Power.
- Production stopped for inspection.
- 1 tray required rework.

---

## Root Cause
- DC1 abnormal detected.
- Cathode 1 condition:
  - Short cathode identified
- Main root cause:
  - Surface degradation of clamp → electrical short

---

## Failure Mechanism
- Cathode clamp surface roughness degraded over time.
- Surface peeling created conductive path.
- Result:
  - Electrical short at cathode
  - DC1 power abnormal → alarm triggered
- Because DC circuit unstable → machine stopped for protection.

---

## Actions
1. Detect DC1 alarm
2. Manual check DC1 → NG
3. Check Cathode 1 → short cathode
4. Stop machine
5. Clean chamber area
6. Replace clamp of cathode 1
7. Run machine again
8. PD perform FAI → OK
9. Rework 1 tray → OK

---

## Preventive Action
- Replace all shields / clamps from old vendor (Guangzhong)
- Move to new vendor (Hantong) with surface roughness control
- Define roughness spec: 20–30 micron
- Monitor clamp condition in PM

---

## Current Status
- Clamp replaced
- Machine recovered
- FAI OK
- Rework completed
- Production resumed

---

## Impact
- Quality: 1 tray rework
- Production: temporary stop (≈2 hours)
- Safety: medium (electrical short risk)
- Repeat risk: high if clamp surface not controlled

---

## Open Risk / Follow-up
- Need confirm new vendor surface roughness stability
- Need audit all cathode clamps on similar machines
- Need schedule PM for clamp inspection
- Monitor repeat DC1 alarm

---

## Evidence
- Alarm: DC1 Power Alarm
- Check result: Cathode 1 short
- Physical inspection: clamp degradation / peeling
- Action: replace clamp → machine recovered
