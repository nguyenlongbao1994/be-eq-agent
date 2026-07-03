---
id: INC-2025-04-17-MOLDING-INCOMPLETE-MOLDING-WW16-SYS851380-P3
date: 2025-04-17
station: Molding
machine: system#851380
press: 3
area: WW16
issue_type:
  - Control
  - Software
  - Transfer
  - Process
status: Helpdesk / service analysis pending
owner: EQ / Helpdesk / Service team
tags:
  - molding
  - incomplete-molding
  - unexpected-transfer-error
  - pellet-transfer
  - press3
  - ww16
  - software-stop
  - tsgsd-8977
---

# Incomplete Molding – WW16 system#851380 Press 3

## Problem Statement
- On WW16 during running production, system#851380 Press 3 suddenly triggered error:
  - "Unexpected transfer error"
- The error happened during transferring pellet.
- Result:
  - incomplete fill
  - 2 strips were rejected

## What We Know
- There was no machine error before the issue happened.
- There was a signal showing unstable pressure on the affected shot, but the signal did not exceed the limit.
- There was no sign of dropping clamp force.
- There was no abnormal movement in transfer.
- After the issue happened, the machine could still run a few more dummy shots without repeating the transfer error.
- Current evidence indicates this was a one-time event.

## What We Don't Know
- Why the machine stopped the transfer at that moment.

## Root Cause Status
- No confirmed mechanical root cause was found in the available analysis.
- No direct abnormality was found in clamp force, friction, or transfer physical behavior.
- Current technical hypothesis points to a forced stop condition from software / control logic.

## Failure Mechanism
- During pellet transfer, the system triggered "Unexpected transfer error" and stopped transfer.
- The resulting transfer interruption caused incomplete fill and rejected strips.
- Mechanical checks did not show clear abnormal clamp-force condition or abnormal friction condition.
- Repeated dummy-shot validation also did not reproduce the issue.
- Based on the available evidence, the current hypothesis is that machine software / control logic may have violated some internal forcing-stop condition and stopped transfer as a safety action.

## Action Taken
1. Clamp-force checking:
   - result: balance and stable
   - even without clamp-force compensate
2. Friction checking:
   - result: smooth and low friction
   - no abnormal found on transfer movement
3. Run dummy shots for validation:
   - issue did not repeat
   - no abnormal found in transfer graph
4. Overall conclusion from physical checking:
   - no abnormal found in mechanical and physical condition

## Hypothesis
- Machine could have violated some kind of forcing-stop condition from software design
- Therefore software may have forced the transfer to stop for safety purpose

## Next Plan
- Seek more input from helpdesk and service team
- Ticket created:
  - TSGSD-8977

## Current Status
- Mechanical and physical checks did not find abnormality
- Issue could not be repeated in dummy-shot validation
- Current status remains open under helpdesk / service-team analysis

## Impact
- Quality: incomplete fill, 2 strips rejected
- Production: transfer was interrupted by unexpected transfer error
- Safety: not stated in the slide
- Repeat risk: currently unclear because it appears to be a one-time event, but software-side risk remains open until root cause is validated

## Open Risk / Follow-up
- Need helpdesk / service team feedback on possible software-forced stop logic
- Need to monitor whether the same "Unexpected transfer error" repeats under production conditions
- Need to correlate future events with transfer graph and pressure signal behavior if recurrence happens

## Evidence
- Attached slide showing:
  - transfer graph while issue happened
  - machine error screenshot
  - incomplete molding strips due to transfer stopped
  - action taken, hypothesis, and next-plan section
