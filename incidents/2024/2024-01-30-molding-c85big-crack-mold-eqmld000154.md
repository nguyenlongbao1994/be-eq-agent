---
id: INC-2024-01-30-MOLDING-C85BIG-CRACK-MOLD-EQMLD000154
date: 2024-01-30
time: "22:55"
station: Molding
machine: EQMLD000154
model: C8.5 Big
press: 1
issue_type:
  - Process
  - Moldchase
  - Vacuum
  - Quality
status: Monitoring after maintenance
owner: EQ / ME
tags:
  - molding
  - c8.5-big
  - crack-mold
  - press1
  - sip1
  - moldchase
  - vacuum-hole
  - o-ring
  - clamp-block
---

# Molding C8.5 Big Crack Mold – EQMLD000154

## Issue
- Issue: Crack mold
- Model: C8.5 Big
- Quantity: 5 SIP
- Machine: EQMLD000154
- Time: 22:55 – 30/01/2024

## Timeline
- 30/01 20:10 → Big cleaning process at Press #1 and Press #3
- 30/01 22:41 → Run FAI OK
- 30/01 22:55 → Press 1, Shot 4/85: Mold crack
- 30/01 22:59 → Press 1, Shot 5/85: Mold crack
- 30/01 23:46 → Press 1, Shot 14/85: Mold crack
- 30/01 23:56 → Press 1, Shot 17/85: Mold crack
- 31/01 00:49 → Press 1, Shot 33/85: Mold crack
- 31/01 03:40 → Machine stop after running 85 shots

## Commonality Check
- All 5 NG SIPs happened at SIP No.1 on Press 1
- Distribution noted in slide: 1 right side, 4 left side
- Time range of occurrence: from 22:55 (30/01/2024) to 00:49 (31/01/2024)

## Symptom
- Repeated crack-mold issue occurred on C8.5 Big.
- Total affected quantity reported in the slide: 5 SIP.
- All NG SIPs were concentrated at SIP No.1 on Press 1.

## Root Cause Status
- The slides do not state one single final root-cause sentence.
- Machine checking results shown in the report indicate:
  - transfer profile was normal
  - transfer pressure was within spec
  - transfer clamp force was within spec
  - pressure and clamp-force trend showed no abnormality
  - press balance test result was normal
- Corrective direction therefore focused on:
  - mold chase maintenance
  - clamp-block vacuum-hole inspection
  - material input double check

## Failure Mechanism (current understanding from report)
- Because transfer profile, clamp force, and press-balance checks were normal, the issue was not directly attributed to obvious transfer-force abnormality.
- The repeated concentration on SIP No.1 at Press 1 suggests a local mold-side / moldchase-side condition.
- The report therefore treated mold chase condition, O-ring / bottom chase cleanliness, top cavity cleanliness, and clamp-block vacuum-hole condition as the main physical areas requiring correction.
- The report also requested ME to double-check mold compound and PCB input, indicating that process/material interaction was still a possible contributing factor.

## Machine Checking
### 1. Check transfer profile data for shots 4, 5, 14, 17, 33
- Transfer pressure spec: 6.5–11 MPa
- Actual transfer pressure shown: 7 MPa → OK
- Transfer clamp-force spec: 45–60 Ton
- Actual transfer clamp-force shown: 50 Ton → OK
- Pressure trend and clamp-force trend: no abnormality found

### 2. Test balance at Press 1
- Test balance at 10 Ton, 20 Ton, 30 Ton → result normal
- Carbon-paper print check:
  - vent line 10 Ton = not dark
  - vent line 20 Ton = darker than 10 Ton
  - vent line 30 Ton = dark
- Conclusion in slide: OK

## Actions
### 1. Maintenance mold chase
- Replace O-ring
- Clean bottom chase
- Ultrasonic clean top cavity by RBS 35 for 8 hours

### 2. Check hole vacuum of clamp block
- Check all vacuum holes of clamp block to see whether any hole is clogged
- Check visual condition of all hole vacuum by Keyence microscope

### 3. Material double check
- Need ME to double check material input:
  - mold compound
  - PCB

## Current Status
- Transfer profile check: normal
- Clamp-force and pressure trend: normal
- Press balance test: normal
- Corrective focus shifted to moldchase maintenance, vacuum-hole inspection, and material input review
- Current status: monitoring after maintenance action

## Impact
