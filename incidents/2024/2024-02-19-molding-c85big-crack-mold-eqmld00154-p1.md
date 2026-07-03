---
id: INC-2024-02-19-MOLDING-C85BIG-CRACK-MOLD-EQMLD00154-P1
date: 2024-02-19
time: "22:54"
station: Molding
machine: EQMLD00154
model: C8.5 Big
press: 1
issue_type:
  - Process
  - Moldchase
  - Vacuum
  - Quality
status: Monitoring after verification
owner: EQ / ME
tags:
  - molding
  - c8.5-big
  - crack-mold
  - press1
  - moldchase
  - clamp-block
  - vacuum-hole
  - o-ring
  - maintenance
---

# Molding C8.5 Big Crack Mold – EQMLD00154 Press 1

## Issue
- Issue: Crack mold
- Model: C8.5 Big
- Quantity: 5 SIP
- Machine: EQMLD00154 – Press #1
- Time: 22:54 – 2/19/2024

## Timeline (Press 1)
- 2/1 → Weekly maintain mold chase
- Note on plan line: stop input model C8.5 Big, only input C8.5 Small
- 2/19 20:05 → Big cleaning process
- 2/19 22:23 → Run FAI OK
- 2/19 22:54 → Molding corner crack issue (01 pcs) happened at shot 4/97 of Press 1
- 4:24 → Machine stop due to production / no OT
  - Note: this time appears in the slide without a clearly printed date next to it

## Symptom
- Crack-mold / molding corner crack issue appeared on Press 1.
- One visible event in the timeline happened at shot 4/97.
- Total quantity reported for the case: 5 SIP.

## Root Cause Status
- The slides do not show one final explicit root-cause sentence.
- Available checks in the report indicate:
  - mold-chase maintenance history was reviewed
  - mold-chase balance after install was normal
  - machine logfile alarms were reviewed and considered common alarms, not directly related to molding corner crack
  - transfer pressure and clamp force at shot 4 were within spec
- Therefore, the case was not directly concluded as transfer-force or press-balance abnormality.

## Failure Mechanism (current understanding from report)
- Since mold-chase balance, transfer pressure, transfer clamp force, and machine-log common alarms did not show direct abnormal evidence, the investigation direction focused on mold-chase condition and vacuum-related local condition.
- The report specifically required:
  - mold-chase maintenance review
  - clamp-block vacuum-hole inspection
  - ME double-check of mold compound and PCB input
- This indicates the issue was treated as a local mold-side / vacuum-side / material-interaction condition rather than an obvious machine-force abnormality.

## Verification / Analysis Performed

### 1. Verify history maintain mold chase (Press #1)
- Mold chase weekly maintained on 2/1
- DRI noted in the slide: DL-Tony Le
- Maintenance followed SOP maintain mold chase from JQ site guide

#### Weekly mold-chase maintenance items shown in slide
**Top mold**
- Clean back side by copper plate and dust-free cloth
- O-ring on back side: replace if damaged
- Cavity: clean surface by high-temperature eraser
- Rubber seal on front of top mold: replace O-ring if damaged

**Bottom mold**
- Clamp block:
  - clean remaining compound and foreign material on surface
  - check O-ring
  - replace if damaged
  - replace new one in monthly maintain
- Seal window:
  - clean and replace new O-ring seal
- Plunger:
  - clean plunger hold and replace new O-ring
- Top edge strip:
  - clean remaining compound by copper plate

### 2. Check balance result after install to machine at 03:07 (2/1)
- Mold-chase balance result: normal

### 3. Check log file machine
- Report states machine logfile was checked for the relevant period
- Slide note:
  - There are 6 types of machine alarm
  - All are common alarms
  - They are considered not related to molding corner crack issue

### 4. Check process data at shot 4
- Transfer pressure spec: 6.5–11 MPa
- Actual transfer pressure: 7 MPa → OK
- Transfer clamp force spec: 45–60 Ton
- Actual transfer clamp force: 50 Ton → OK
- Trend of pressure and clamp force: no abnormality

## Actions / Corrective Direction
### Moldchase maintenance direction
- Replace O-ring where needed
- Clean bottom chase
- Clean top / cavity areas according to mold-chase maintenance SOP
- Perform detailed clamp-block vacuum-hole checks
- Use microscope / visual check for vacuum-hole condition

### Additional action direction
- ME needs to double-check material input:
  - mold compound
  - PCB

## Current Status
- Mold-chase maintenance history was verified
- Mold-chase balance after install was normal
- Process data at shot 4 was within transfer and clamp-force spec
- Machine-log alarms were judged common alarms and not directly linked to corner crack
- Current direction: continue monitoring after maintenance / vacuum-hole verification / material double check

## Impact
- Quality: 5 SIP crack-mold issue reported
- Production: machine later stopped according to timeline
- Safety: not stated in the report
- Repeat risk: still present because no single final direct root cause was closed in the slide

## Open Risk / Follow-up
- Need to confirm clamp-block vacuum holes are not partially clogged
- Need to confirm mold-chase maintenance execution quality and O-ring condition
- Need ME confirmation on mold compound and PCB input condition
- Need continued monitoring on Press 1 for repeat corner crack pattern

## Evidence
- Attached slides showing:
  - issue timeline
  - mold-chase maintenance checklist / SOP references
  - clamp-block and vacuum-hole inspection direction
  - transfer pressure / clamp-force shot-4 checking result
