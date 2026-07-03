---
id: INC-2025-04-01-MOLDING-EAP-CANNOT-CONNECT-EQMLD00146
date: 2025-04-01
time: "05:30-07:53"
station: Molding
machine: EQMLD00146
model: C8.5 Small
issue_type:
  - IT
  - Software
  - Communication
  - Control
  - Human
status: Recovered / Preventive action defined
owner: EQ / SMD
tags:
  - molding
  - eap
  - secgems
  - communication
  - online-offline
  - model-server
  - machine-restart
---

# Molding C8.5 – EAP cannot connect

## Issue
- Issue description: EAP cannot connect with machine
- Model: C8.5 Small
- Impact quantity: 02 panels
- Machine: EQMLD00146
- Time: 05:30 – 07:53 (01/04/2025)

## Timeline
- Big cleaning process completed before startup
- FAI completed before issue
- 04:20 → PC / machine side issue observed:
  - PC screen had lag / control abnormality
  - after restart, communication state did not recover normally
- 05:45 AM → EQ manually re-connected EAP by clicking **Online** mode on MMI
- 07:54 AM → Machine auto compare OK after corrective setting / recovery
- Preventive setting simulation later confirmed machine can auto reconnect normally

## Symptom
- EAP could not connect with machine.
- Machine restart caused communication state between EAP and machine to auto change to **Offline**.
- MMI showed machine control state ON, but EAP still alarmed that equipment was not online.
- Manual online action was needed to recover temporarily.

## Root Cause
- Issue happened after machine restart.
- Communication state between EAP and machine automatically changed to Offline.
- EQ manually reconnected EAP through Online mode on MMI at 05:45 AM.
- SMD team check indicated that when manual reconnect occurred, there was a mismatch / misunderstanding between EAP and machine-state logic.
- Machine display control state was ON, but EAP still considered the equipment not online.
- Preventive-action slide shows the corrective direction was to change a **Secgems**-related setting in MMI so that:
  - Power up control state changes from **Offline** to **Online**
  - Machine can reconnect automatically with EAP after restart

## Failure Mechanism
- After restart, the communication / control state did not return to the expected online state automatically.
- MMI local display and EAP remote status were not synchronized.
- Because of this control-state mismatch, EAP still considered the equipment offline even though machine-side state appeared ON.
- Manual Online action could temporarily recover the link, but the underlying setting still allowed the mismatch to happen again until SMD adjusted the Secgems-related power-up control state.

## Corrective Action
1. EQ manually reconnected the machine to EAP through Online mode on MMI.
2. SMD team changed the Secgems-related setting in MMI.
3. Power-up control state was changed from **Offline** to **Online**.

## Preventive Action
1. Keep the updated Secgems / power-up communication setting so that machine reconnects to EAP automatically after restart.
2. No need to switch Online manually in the future if the corrected setting is maintained.
3. A simulation after setting change confirmed that machine can auto reconnect normally.

## Current Status
- Machine recovered.
- Auto reconnect behavior was confirmed by simulation after setting adjustment.
- Current status: recovered, preventive action defined.

## Impact
- Quality: 02 panels impacted
- Production: machine could not continue normally under EAP until reconnect was restored
- Safety: not stated in report
- Repeat risk: possible if communication / power-up setting is changed again or not standardized across restart conditions

## Open Risk / Follow-up
- Need to ensure the same setting is retained after future software / configuration changes
- Need to verify restart behavior again after future maintenance or reboot
- Need to standardize this setting across similar machines if they use the same communication architecture

## Evidence
- Attached slides show:
  - issue description and timeline
  - MMI communication / control-state screen
  - event / log snippets
  - before / after setting screenshots for power-up control states
