---
id: INC-2022-01-11-UNDERFILL-SPILL-GLUE-ISSUE-DISPENSE135
date: 2022-01-11
time: "12h30-15h00"
station: Underfill
machine: 135# Dispense machine
issue_type:
  - Process
  - Dispense
  - Needle wear
  - Underfill
status: Recovered after needle replacement / Pre-setup needle check required
owner: EQ / Leo
tags:
  - underfill
  - glue-spill
  - valve1
  - dispense
  - needle-wear
  - machine135
---

# Underfill spill glue issue report

## Issue
- Station: Underfill – 135# Dispense machine
- Time: 12h30–15h00
- Error description: Glue is spill in PCB location of valve 1
- Change valve last time: 8:20 AM
- Fail SIP: 0

## Symptom
- Glue spill was observed at PCB location of valve 1.
- Issue happened at Underfill station on 135# Dispense machine.

## Root Cause
- Glue weight in valve 1 was bigger than valve 2 by 0.08 mg/dot.
- This difference was out of spec:
  - Spec limit: < 0.05 mg/dot difference
- The needle of valve 1 was much more worn out than valve 2.

## Failure Mechanism
- Needle wear at valve 1 changed the dispense condition.
- Because valve 1 needle was significantly more worn than valve 2, glue output from valve 1 increased abnormally.
- The glue weight difference between valve 1 and valve 2 became 0.08 mg/dot, exceeding the allowable difference limit.
- This abnormal dispense imbalance caused glue spill at the PCB location of valve 1.

## Actions
### Short term
- Change the new needle to valve 1
- Machine ran normal from 15:00 PM to now

### Long term
- Check worn-out condition of needles between 2 valves before setting up the machine

## Current Status
- Valve 1 needle was replaced.
- Machine recovered and ran normally from 15:00 PM.
- Current status: recovered, continue checking needle wear before setup.

## Impact
- Quality: glue spill issue observed
- Production: temporary issue during 12h30–15h00
- Safety: not stated in the report
- Fail SIP: 0

## Open Risk / Follow-up
- Need to compare wear condition between valve 1 and valve 2 before machine setup
- Need to monitor glue weight difference between both valves
- Need to prevent repeat needle wear imbalance from causing out-of-spec glue output

## Evidence
- Report title: Underfill spill glue issue report
- Root cause note states:
  - valve 1 glue weight was 0.08 mg/dot higher than valve 2
  - spec limit is < 0.05 mg/dot difference
  - valve 1 needle was much more worn out than valve 2
- Action note states:
  - changed new needle to valve 1
  - machine ran normal from 15:00 PM
