---
id: INC-2022-09-06-MOLDING-EQMLD00147-C85BIG-P2-CAVITYVACUUM
date: 2022-09-06
time: "16h00-19h30"
station: Molding
machine: EQMLD00147
model: C8.5 BIG
press: 2
issue_type:
  - Utility
  - Process
  - Vacuum
  - Material
status: Monitoring
owner: EQ
tags:
  - molding
  - cavity-vacuum
  - press2
  - c8.5-big
  - vacuum-tube
  - heater-block
  - leakage
  - maintenance
---

# Molding: Cavity Vacuum Too High > 30 hPa

## Background
- Time: 16h00 – 19h30 (09/06)
- Station: Molding EQMLD00147 – C8.5 BIG – Press 2
- Issue: Press 2 – Cavity vacuum too high
- Description: Cavity vacuum when checking before mold was too high > 30 hPa

## Symptom
- During pre-mold checking, cavity vacuum at Press 2 was higher than the control limit (>30 hPa).

## Root Cause
- The vacuum tube was connected directly to the heater block (175°C).
- Because of long-term exposure to high temperature, the vacuum tube was damaged over time.
- Tube degradation caused vacuum leakage, resulting in cavity vacuum >30 hPa.
- Tube material noted in the report: heat-resistant plastic.
- The report notes that USI already used tube suitable for vacuum according to vendor guidance.

## Failure Mechanism
- Long-term thermal exposure from the heater block degraded the vacuum tube material.
- Once tube integrity was reduced, leakage occurred in the vacuum path.
- Because the vacuum path leaked, cavity vacuum during checking increased above the normal control target.

## Actions
### Short Term
- Changed new vacuum tube of heater block at Press 2.

### Long Term
- Check the status of vacuum tube during weekly moldchase maintenance.
- Replace new tube during monthly maintenance.

## Current Status
- Immediate containment was completed by replacing the vacuum tube at Press 2.
- Long-term control is based on periodic inspection and scheduled tube replacement.
- Current status: monitoring after replacement.

## Impact
- Quality: cavity vacuum out of spec before molding can affect molding stability
- Production: pre-mold check abnormality may delay machine release
- Safety: not stated in the report
- Repeat risk: possible if tube aging is not controlled by periodic replacement

## Open Risk / Follow-up
- Need to verify cavity vacuum remains within control limit after tube replacement
- Need to confirm weekly and monthly maintenance execution is sustained

## Evidence
- Attached analysis report image
- Photos show the vacuum tube area connected to heater block and the replaced tube area
