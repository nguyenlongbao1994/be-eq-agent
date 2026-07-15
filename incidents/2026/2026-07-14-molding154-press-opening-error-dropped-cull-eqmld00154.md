---
id: INC-2026-07-14-MOLDING154-PRESS-OPENING-ERROR-DROPPED-CULL-EQMLD00154
date: 2026-07-14
station: Molding
machine: EQMLD00154
model: C10.5 N244B
area: Press 2 / Press 3 / Compound Handler
issue_type:
  - Mechanical
  - Process
  - Mold chase
  - Cull
  - Motor overload
status: Recovered after damaged panel removal, nozzle cleaning and mold chase transfer to #158 / Press 2 verification pending
owner: EQ / PD / Molding
tags:
  - molding154
  - press-opening-error
  - dropped-cull
  - mold-chase-jam
  - motor-overload
  - compound-handler
  - eqmld00154
---

# Molding 154 – Error occurred while opening the press

## Issue Description
- Model: C10.5 N244B
- Station: Molding
- Machine: EQMLD00154
- Issue: Error occurred while opening the press
- Impact: 7 SIPs scrap

## Customer Impact
- 7 SIPs scrap

## Containment Actions
- Moved mold chase to #158 machine to run and cover output.

## Timeline
- 08:15 14/07/2026
  - PD big clear
- 11:00 14/07/2026
  - Machine FAI → OK
- 16:14 14/07/2026
  - Previous alarm occurred:
    - "Error while pushing lead frames to the lead frame handler"
  - Issue was recovered at 16:21
- 16:30 14/07/2026
  - Press 2 alarm:
    - "Error occurred while opening the press"
- 19:30 15/07/2026
  - Move mold chase to #158 to run
- 22:30 15/07/2026
  - Machine recovered / machine can run normal

## Symptom
- Press 2 could not open the press.
- Mold chase was jammed.
- Motor overload occurred.
- 7 SIPs were scrapped.
- Issue happened after a previous Press 3 / leadframe-handler related alarm and recovery.

## FA & RC

### Previous alarm
- At 16:14, Press 3 had alarm:
  - "Error while pushing lead frames to the lead frame handler"
- Issue was recovered at 16:21.
- Previous version of report also mentioned:
  - leadframe handler pusher panel-to-mold-chase error
  - pusher cylinder stuck
  - cleaning inside / piston of cylinder was required

### Main root cause chain
- During the 7 minutes downtime, cull stuck on the nozzle.
- When the Compound Handler released the cull, the cull was not completely detached from the nozzle.
- The Compound Handler then moved to Press 2.
- The cull dropped onto Press 2.
- The dropped cull damaged the panel and caused the mold chase to jam.
- Mold chase jam caused motor overload.
- Motor overload prevented mold opening.

## Confirmed Root Cause
- The cull was not fully detached from the nozzle after Compound Handler cull release.
- The cull dropped onto Press 2 and jammed the mold chase.
- This caused panel damage, motor overload, and press-opening failure.

## Contributing Cause
- Previous Press 3 leadframe-handler alarm created troubleshooting downtime.
- During this downtime, the cull remained stuck on the nozzle.
- No effective confirmation existed to ensure the nozzle was clear after cull release before the Compound Handler moved to the next press.

## Failure Mechanism
- Compound Handler picked up / handled cull during troubleshooting.
- Cull was released but not completely detached from the nozzle.
- Because nozzle-clear status was not confirmed, the handler moved to Press 2.
- The remaining cull dropped into Press 2.
- The dropped cull damaged the panel and jammed the mold chase.
- The jam created abnormal load / motor overload.
- Because of motor overload and mold chase jam, the press could not open normally.

```text
Previous leadframe-handler alarm
→ troubleshooting downtime
→ cull stuck on nozzle
→ cull release incomplete
→ compound handler moved to Press 2
→ cull dropped onto Press 2
→ panel damaged
→ mold chase jam
→ motor overload
→ press opening failed
