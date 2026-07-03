---
id: INC-2026-04-20-MOLDING154-P2-RIGHT-MOLD-SHIFT-EQMLD00154
date: 2026-04-20
station: Molding
machine: EQMLD00154
model: C10.5 N243S
press: 2 Right
issue_type:
  - Mechanical
  - Human
  - Moldchase
  - Center pin
status: Corrective action completed / Long-term control ongoing
owner: EQ / ME
tags:
  - molding
  - n243s
  - mold-shift
  - press2
  - right-side
  - center-pin
  - moldchase
  - eqmld00154
---

# N243S – Molding 154# P2 Right Mold Shift

## Issue Description
- Model: C10.5 N243S
- Station: Molding
- Machine: EQMLD00154
- Problem: 3 panel mold shift out of spec
- Spec: 0.10 mm
- Actual: 0.15 mm
- Additional impact: PCB hole damage
- Detection point / impact noted in slide: after sputter check

## Customer Impact
- No impacts

## Containment Actions
- Hold in sputter VI
- Check the result and judgement by ME

## Timeline
- 04/18/2026 → EQ assembled and installed mold chase P85025351
- 04/20/2026 13:00 → Machine FAI found mold shift
  - Right side = 0.15 mm
- 04/20/2026 16:00 → Disassembled mold chase
  - Found NG centre pin = 1.45 mm
  - Correct pin = 1.50 mm
- 04/20/2026 20:00 → Production normal at night shift after corrective action

## Checking Result
- After removing cavity and measuring the centre pin, EQ found 1F/6 pin Ø1.45 mm at the RIGHT side.
- Normal pin size should be Ø1.50 mm.

## Root Cause
1. The Ø1.45 mm pin belonged to Audio mold chase.
2. The Ø1.45 mm pin size is different from C10.5 / Attis mold chase pins.
3. The wrong pin remained in the PIN BOX and was mixed together with other pins.
4. EQ did not detect the small dimensional gap between Ø1.45 mm and Ø1.50 mm by visual inspection when assembling mold chase P85025351.
5. The Ø1.45 mm pin at the right side could not align correctly with the PCB hole.
6. When the mold chase closed, the poor alignment caused panel shift.
7. Final result: mold shift happened, overspec 0.15 mm.

## Failure Mechanism
- Right-side center pin controls / supports PCB alignment during mold-chase closing.
- A smaller Ø1.45 mm pin was installed instead of the correct Ø1.50 mm pin.
- Because the pin diameter was smaller, the right-side PCB-hole alignment became inaccurate.
- When mold chase closed, the panel position shifted due to this misalignment.
- This produced mold shift measured at 0.15 mm, exceeding the 0.10 mm spec.

## Short-Term Corrective Action
1. Withdraw new pin Ø1.50 mm from warehouse and change the correct center pin at right venting — Done
2. Different sizes of pins are placed separately and the pin of size Ø1.46 mm was moved out from workshop area — Done
3. Install mold chase P85025351 and verify
   - Production normal in night shift 04/23
   - Result in spec = 0.04 mm — Done

## Long-Term Corrective Action
1. Sort all pins of total 14 mold chase C10.5 / Attis — Done
2. In maintenance area, separate different pins in different boxes and add clear marking to avoid mixing — Done
3. Update mold-chase maintenance checklist by adding item:
   - "measure the pin dimensions and record the data" — Done
4. Attach pin-size diagrams for different mold-chase types as warning in molding maintenance area — Ongoing

## Current Status
- Correct pin was replaced.
- Production recovered and normal result was confirmed in night shift.
- Verified in-spec result after correction: 0.04 mm.
- Long-term control for pin segregation and pin-dimension verification is already implemented or in progress.

## Impact
- Quality: 3 panels mold shift out of spec, actual 0.15 mm
- Production: temporary abnormality until correct pin was installed
- Safety: not stated in the slide
- Repeat risk: reduced after pin segregation and pin-dimension checklist update, but still depends on maintenance discipline

## Open Risk / Follow-up
- Need to finish the ongoing pin-size warning display in maintenance area
- Need to sustain pin sorting and clear marking discipline
- Need to maintain dimensional measurement record in mold-chase maintenance checklist

## Evidence
- Issue summary slide showing spec 0.1 mm / actual 0.15 mm and PCB-hole damage note
- Measurement image showing centre pin = 1.45 mm
- Comparison image between Audio pin and C10.5 pin
- Maintenance / storage-box improvement photos and checklist update references
