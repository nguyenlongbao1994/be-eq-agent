---
id: INC-2026-01-06-MOLDING-ATTIS-HEATING-POWER-CORD-DAMAGED-EQMLD00157
date: 2026-01-06
time: "03:40-06:30"
station: Molding
machine: EQMLD00157
model: Attis
issue_type:
  - Electrical
  - Utility
  - Wiring
  - Heating
status: Recovered after reconnection / Replacement pending
owner: EQ
tags:
  - molding
  - attis
  - heating
  - power-cord
  - leadframe-handler
  - temperature-error
  - 220v
  - qtime
---

# Molding ATTIS – Power Cord of the Heating is Damaged

## Issue
- Issue description: Power cord of the heating plate is damaged
- Model: Attis
- Q’ty: 54 Panel Q-time
- Machine: EQMLD00157
- Time: 03:40 – 06:30 (06/01/2026)

## Timeline
- 01/05 20:10 → Big Clean
- 01/05 23:00 → FAI OK
- 01/06 03:40 → Machine alarm:
  - Temperature of leadframe handler error
- 01/06 06:30 → Machine run normal

## Symptom
- Machine alarmed: Temperature of leadframe handler error
- 54 panels became Q-time affected
- Leadframe-handler heating did not function normally

## Root Cause
- At 03:40 the machine had issue “temperature of leadframe handler error”
- EQ stopped the machine and checked the power voltage
- EQ found that the 220V power supply was lost
- Visual / physical check confirmed the power cord of the heating was damaged
- The broken power cord was later reconnected

## Failure Mechanism
- Leadframe-handler heating depends on stable 220V power supply
- When the heating power cord was damaged, electrical supply to the leadframe-handler heating was interrupted
- Because heating power was lost, the leadframe-handler temperature condition became abnormal and machine triggered temperature error
- Once the broken power cord was reconnected, heating function recovered and machine could run normally again

## Fishbone / Exclusion Summary
### Machine
- Visual check mold chase → OK
- Re-test transfer line by FR4 → Normal
- Expert onsite confirmed result → OK
- Machine-side main abnormal point identified: damaged power cord of the heating

### Man
- PD operating → Normal

### Environment
- Maintenance machine on time (8-Dec) → Normal

### Method
- PD cleaning mold chase process → Normal

### Material
- Normal

## Actions
### Short term
- The broken power cord was reconnected

### Long term
- Ordered a new power cord for replacement
- Added a monthly maintenance task to inspect the electrical condition of the leadframe handler

## Current Status
- Broken power cord was reconnected
- Machine recovered to normal at 06:30
- Long-term replacement power cord is required
- Monthly maintenance inspection item was added

## Impact
- Quality: 54 panels became Q-time affected
- Production: machine stopped until heating power was restored
- Safety: electrical damage at heating power cord is a safety-relevant maintenance concern
- Repeat risk: possible if cable condition is not inspected periodically

## Open Risk / Follow-up
- Need to replace the temporary reconnected power cord with a new one
- Need to sustain monthly inspection of leadframe-handler electrical condition
- Need to monitor if temperature error repeats before permanent replacement is completed

## Evidence
- Attached slides show:
  - issue summary and timeline
  - fishbone analysis highlighting damaged heating power cord
  - photo of damaged power cord
  - photo showing the broken power cord was reconnected
  - monthly maintenance addition reference
