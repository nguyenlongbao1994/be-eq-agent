---
id: INC-2022-07-29-MOLDING-C85-SMALL-BLEEDING
date: 2022-07-29
station: Molding
machine: EQMLD000154
model: C8.5 small
issue_type:
  - Process
  - Quality
  - Moldchase
  - Compound
status: Monitoring
owner: EQ
tags:
  - molding
  - bleeding
  - fiducial-mark
  - c8.5-small
  - moldchase
  - compound
  - vacuum
  - transfer-profile
---

# Molding C8.5 Small Bleeding

## Issue
- Compound bleeding was found at fiducial mark.
- Model: C8.5 small
- Machine: EQMLD000154

## Performance Report Period
- 08:00 AM 29/07 to 08:00 AM 30/07

## Production Data
- Total Prod: 678
- Panel OK: 671
- Panel NG: 7
- Time rework: 35 minute

## Initial Check Result
### 1. Machine Condition
- All machine parameter and condition were checked.
- No abnormal problem was found from machine condition.

### 1.1 Test Mold Balance
- Paper clamp is normal.
- Moldchase is balance.

### 1.2 Transfer Profile
- Clamp force actual is normal.
- Transfer pressure actual is normal.
- Result matched the parameter setup.

### 1.3 Cavity / Board Vacuum
- Cavity / Board vacuum actual = 5 hPa
- In-spec condition: < 30 hPa

## Root Cause Status
- No direct abnormal machine condition was found from parameter, mold balance, transfer profile, or vacuum check.
- Current evidence points more to process / condition-related bleeding behavior at fiducial mark rather than obvious machine breakdown.

## Failure Mechanism (Current Understanding)
- Compound bleeding appeared specifically at fiducial mark area.
- Since machine condition, mold balance, transfer profile, and cavity/board vacuum were all checked and were normal, the case was treated as a process-condition issue requiring stronger moldchase cleaning and maintenance control.
- Additional confirmation was requested for material-related and leadframe-related factors.

## Actions
### 2. Process Cleaning Moldchase
#### 2.1 PD transfer cleaning moldchase
- PD follows SOP of transfer cleaning moldchase after 140 shots, according to recipe setup by BE.

#### Cleaning / conditioning sequence recorded
- Transfer cleaning (9 times)
- Shots shot (1 time)
- Transfer cleaning (1 time)
- Transfer conditioning (2 times)
- Shots shot (1 time)
- Transfer conditioning (1 time)

### 2.2 EQ maintenance moldchase
- Plan: maintain moldchase weekly
- Actual: EQ maintained moldchase (BOT + TOP) with cycle 5 days/time
- EQ checks:
  - mold balance
  - vacuum
  - record in checksheet after maintenance

## Long-Term Plan
- EQ did not find abnormality from machine and will continue monitoring all machine conditions.
- Need BE support to check other possible factors such as:
  - compound
  - leadframe-specific condition
- Need BE to confirm whether all panel NG can pass or not, because this fiducial mark does not affect all stations.
- The report note states that the fiducial mark is not used by:
  - Laser
  - CP-filling
  - Jig Saw

## Current Status
- Machine condition check: normal
- Mold balance check: normal
- Transfer profile check: normal
- Cavity / board vacuum: normal (5 hPa)
- Current direction: process monitoring + moldchase cleaning control + weekly EQ maintenance

## Impact
- Quality: bleeding at fiducial mark, 7 panels NG during the recorded period
- Production: rework time recorded as 35 minutes
- Safety: not stated in the report
- Repeat risk: still present because the exact direct cause was not fully isolated to one single factor

## Open Risk / Follow-up
- Need continued monitoring of machine condition
- Need BE support on compound / leadframe factor review
- Need BE confirmation on pass / non-pass judgment for panel NG related to fiducial mark impact
