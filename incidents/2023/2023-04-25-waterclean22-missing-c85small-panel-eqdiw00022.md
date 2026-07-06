---
id: INC-2023-04-25-WATERCLEAN22-MISSING-C85SMALL-PANEL-EQDIW00022
date: 2023-04-25
time: "19:17-19:37"
station: Water Clean
machine: EQDIW00022
model: C8.5 Small
issue_type:
  - Process
  - Carrier
  - Handling
  - Water Clean
status: Production stopped to find dropped panel / Monitoring
owner: EQ / PD
tags:
  - water-clean
  - waterclean22
  - missing-panel
  - carrier
  - top-cover
  - c8.5-small
  - eqdiw00022
---

# Water clean #22 – Missing C8.5 Small panel issue

## Issue
- Issue: Missing C8.5 Small panel issue
- Model: C8.5 Small
- NG Q’ty: 01 panel
- Machine: Water clean #22
- Reference machine code used in this incident file: EQDIW00022
- Time: 19:37 PM, 25th April 2023

## Symptom
- PD team found that the C8.5 Small carrier came out of the Water clean machine without PCB panel at 19:37 PM.
- 01 panel was missing.

## Root Cause Analysis
- EQ and PD checked CCTV and found:
  - there was a carrier with panel input into the Water clean machine without top cover at 19:17 PM
- When the carrier with panel was cleaned by water and air in the Water clean machine:
  - panel was dropped out of the carrier

## Root Cause
- A carrier entered the Water clean machine without top cover.
- Without the top cover, the panel was not held securely inside the carrier.
- During water and air cleaning, the panel dropped out of the carrier.

## Failure Mechanism
- The carrier top cover is required to hold the panel securely during Water Clean process.
- When the carrier entered the machine without top cover, the panel retention condition became abnormal.
- Under water and air cleaning force, the unsecured panel dropped out of the carrier.
- This caused the missing panel issue at machine output.

## Checks Performed
1. Check loader, conveyor, and Water clean machine during the issue time
   - No abnormal
2. Check pusher position when pushing carrier out of magazine
   - The pusher contacted the center of carrier
   - The pusher did not impact the top cover of carrier

## Actions
1. Check loader, conveyor, and water clean machine during the issue time
   - no abnormal
2. Check pusher position when pushing carrier out of magazine
   - pusher contacted the center of carrier
   - no impact to top cover of carrier
3. Stop water clean #22 to find the dropped panel

## Current Status
- Machine was stopped for panel tracing and checking.
- No machine-side abnormal was found in loader / conveyor / pusher position during the issue window.
- Current status: under monitoring after issue investigation.

## Impact
- Quality: 01 panel missing
- Production: machine stopped to find the dropped panel
- Safety: not stated in the slide
- Repeat risk: possible if carrier condition / top-cover control is not checked before input

## Open Risk / Follow-up
- Need to control carrier input condition, especially top cover completeness
- Need to verify no carrier enters Water clean machine without top cover
- Need to continue monitoring for repeated missing-panel issue

## Evidence
- Slide title: Water clean #22_ Missing C8.5 Small panel issue
- Issue section states:
  - Model: C8.5 Small
  - NG Q’ty: 01 panel
  - Machine: Water clean #22
  - Time: 19:37 PM, 25th April 2023
- Root cause analysis states:
  - carrier input into Water clean machine without top cover at 19:17 PM
  - during water and air cleaning, panel dropped out of carrier
- Action section states:
  - loader / conveyor / water clean machine had no abnormal
  - pusher contacted the center of carrier and did not impact top cover
  - stop water clean #22 to find the dropped panel
