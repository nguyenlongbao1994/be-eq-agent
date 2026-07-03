---
id: INC-2021-07-10-MOLDING-FQMLD00143-PRESS3-VOID
date: 2021-07-10
time: "00h24"
station: Molding
machine: FQMLD00143
press: 3
issue_type:
  - Mechanical
  - Process
  - Vacuum
  - Mold balance
status: Monitoring
owner: Loki Gener
tags:
  - molding
  - void
  - press3
  - mold-balance
  - vacuum
  - moldchase
  - shim
  - fr4
  - fai
---

# Molding Incomplete Analysis Report – FQMLD00143 Press 3

## Background
- Time: 00h24 (07/10)
- Station: Molding FQMLD00143 – Press 3
- Error code: Molding Void
- Error description: Press 3 was not able to produce because of void issue at position SIP (1-4-19)
- Failure quantity: N/A

## Symptom
- Press 3 could not continue production due to molding void issue.
- Void was reported at SIP position (1-4-19).

## Root Cause
- Press 3 of machine #147 was not balanced.
- When clamp force was applied, pressure was too high at the four corners.
- Vacuum air could not escape from the mold chase correctly.
- Mold compound flow in the top cavity resulted in mold overflow.

## Failure Mechanism
- Press imbalance caused uneven clamp-force distribution.
- Excessive local pressure at the four corners restricted normal vacuum air release.
- Trapped air and unstable compound flow inside the cavity contributed to void / overflow-related molding abnormality.

## Actions
- Checked cylinder, mold chase, and heater block: no abnormality found.
- EQ added shim at the top of Press 3 to balance the press again.
- Total shim thickness added: 0.09 mm.
- Checked mold balance again.
- FR4 result after balancing: OK.
- FAI panel run planned for verification and continued monitoring.

## Current Status
- Initial mechanical / mold-side checks showed no abnormality on cylinder, mold chase, and heater block.
- Press balancing adjustment was completed with 0.09 mm shim.
- FR4 result after balancing was OK.
- Current direction: wait for FAI panel confirmation and continue monitoring.

## Impact
- Quality: void risk on molded product
- Production: Press 3 could not continue normal output until rebalancing action
- Safety: not stated in the report
- Repeat risk: present until FAI panel confirms stable balance and vacuum release behavior

## Open Risk / Follow-up
- Need to confirm stability during FAI panel run
- Need to continue monitoring repeat risk of press imbalance and molding void recurrence

## Evidence
- Attached analysis report image
- Included cavity / mold-side photos and balancing verification photos
``
