---
id: INC-2026-04-22-CPF92-VALVE-CANNOT-PRODUCTION-EQCPF00092
date: 2026-04-22
station: CPF
machine: EQCPF00092
model: Attis
issue_type:
  - Process
  - Valve
  - Nozzle
  - Solenoid
  - CPF
status: Production restored / Long-term valve check updated
owner: EQ / ME
tags:
  - cpf92
  - valve-cannot-production
  - nozzle-dirty
  - solenoid-wire-broken
  - attis
  - eqcpf00092
---

# N240 | CPF92 Issue Valve cannot production

## Issue Description
- Model: Attis
- Station: Cpfilling
- Machine: EQCPF00092
- Impact: Out put production
- Customer Impact: N/A

## Containment Actions
- Stop machine

## Timeline
> Note: timeline in the slide shows time only.  
> Register date key used for this incident: 2026/04/22

- 09:25
  - Machine running normal
  - CPF92
- 09:30
  - Replace valve #18
  - Dot weight out spec
  - Can’t production
  - CPF92
- 10:30
  - Replace valve #09
  - Can’t production
  - CPF92
- 11:30
  - Replace valve #05
  - Can’t production
  - CPF92
- 12:00
  - Remove valve #05 to CPF94
  - Can’t production
  - CPF94
- 12:30
  - EQ install valve 02 for CPF94
  - CPF94
- 13:00
  - Production has been restored
  - CPF94

## Symptom
- Valve could not support normal production output.
- Multiple valve positions were checked / replaced during troubleshooting.
- Production was restored after temporary replacement and repair actions.

## FA & RC
1. Check nozzle, needle, o ring, seal replacement and machine maintenance history
   - On time
   - No abnormal

2. Check the nozzle by microscope 30x
   - All valve OK

3. Check the nozzle by microscope 160x
   - Valve #09, #05 OK
   - Valve #18 has dirty → abnormal

4. Check solenoid valve connect wire
   - Valve #09, #18 OK
   - Valve #05 has broken → abnormal

## Root Cause
- Valve #18 had dirty / contamination at nozzle level detectable under microscope 160x.
- Valve #05 had broken solenoid-valve connection wire.
- These two abnormal conditions caused valve instability and “cannot production” behavior.
- General maintenance history itself was normal, so the problem was not caused by missed valve / seal replacement schedule.

## Failure Mechanism
- CPF dispensing depends on:
  - clean nozzle condition
  - stable solenoid actuation
  - correct stocker adjustment
- When valve #18 nozzle became dirty, glue flow / dispense condition was abnormal.
- When valve #05 solenoid wire was broken, valve actuation became abnormal.
- These valve-side abnormalities prevented stable production output.
- Production was restored only after:
  - replacing / swapping valve for temporary recovery
  - reconnecting solenoid wire
  - adjusting stocker
  - cleaning nozzle by microscope 160x verification

## Corrective Actions

### Short-term corrective action
1. Install valve #02 at CPF94 → OK, run production normal
2. Valve #05 reconnect wire of solenoid → OK, run normal
3. Valve #09 after maintain again adjust stocker = 4.5 line → OK, run normal
4. Valve #18 after maintain check nozzle by microscope 160x and clear → OK, run normal

### Long-term corrective action
1. Need adjust stocker when adjust glue weight
2. After valve maintenance will check by microscope 160x

## Current Status
- Production has been restored.
- Valve #02 was installed for CPF94 and run production normal.
- Valve #05 wire issue was corrected.
- Valve #09 stocker was adjusted to 4.5 line.
- Valve #18 nozzle contamination was checked again by microscope 160x and cleaned.
- Long-term control was added for stocker adjustment and microscope 160x verification after maintenance.

## Impact
- Quality: not explicitly stated in the slide
- Production: output production impacted before restoration
- Customer impact: N/A
- Safety: not stated in the slide
- Repeat risk: possible if valve nozzle cleanliness and solenoid wire condition are not checked deeply enough after maintenance

## Open Risk / Follow-up
- Need to maintain microscope 160x nozzle check after valve maintenance
- Need to adjust stocker whenever glue weight is adjusted
- Need to monitor repeat issue on valve positions #18, #05, and #09
- Need to verify valve wire / holder condition during preventive maintenance

## Evidence
- Slide title: N240 | CPF92 Issue Valve cannot production
- Description confirms:
  - Model: Attis
  - Station: Cpfilling
  - Machine: EQCPF00092
  - Impact: Out put production
- FA&RC confirms:
  - maintenance history normal
  - 30x microscope all valve OK
  - 160x microscope: valve #18 dirty
  - solenoid connect wire: valve #05 broken
- Corrective action confirms:
  - install valve #02 for CPF94
  - reconnect wire valve #05
  - adjust stocker valve #09 = 4.5 line
  - check and clear valve #18 by microscope 160x
