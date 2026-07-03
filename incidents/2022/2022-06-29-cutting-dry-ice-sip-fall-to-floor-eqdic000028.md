---
id: INC-2022-06-29-CUTTING-DRY-ICE-SIP-FALL-TO-FLOOR-EQDIC000028
date: 2022-06-29
time: "03:30 AM"
station: Cutting Dry Ice
machine: EQDIC000028
model: C8.5 Small
issue_type:
  - Human
  - Handling
  - Magazine
  - Process
status: Corrective action defined / Training required
owner: EQ / PD
tags:
  - cutting-dry-ice
  - sip-fall
  - magazine-change
  - carrier-fall
  - eqdic000028
  - c8.5-small
---

# Cutting Dry Ice – SIP Fall to Floor

## Issue
- Issue description: SIP fall to floor
- Model: C8.5 Small
- Machine: EQDIC000028
- NG SIP: 22 pcs
- Time: 3:30 AM, 29th Jun 2022

## Symptom
- During Cutting Dry Ice machine running, EQ supported PD to change magazine.
- SIP fell to the floor during magazine handling.
- 22 pcs became NG.

## Root Cause
- EQ took the empty magazine to change magazine for unloader.
- EQ did not check magazine status carefully.
- EQ did not know that one carrier still remained at the top side of the magazine.
- Because the remaining carrier was still inside the top side of magazine, the carrier fell down when EQ lifted the magazine.
- The carrier falling caused SIP to fall to the floor and created 22 pcs NG.

## Failure Mechanism
- Magazine handling was performed without confirming whether the magazine was completely empty.
- One carrier remained in the magazine.
- When EQ lifted the magazine during unloader magazine change, the retained carrier was no longer supported.
- The carrier dropped out and SIP fell to the floor.
- This is a handling / verification failure during magazine-change process.

## Actions
1. PD to make layout separating 3 types of magazine:
   - Empty magazine
   - Loading magazine
   - Unloading magazine
2. Define / make process for Change Magazine for Unloader.
3. Train EQ and PD members:
   - When working with magazine, EQ must check magazine status carefully
   - Assembly cover correctly to avoid carrier falling out

## Current Status
- Corrective action direction was defined in the report.
- Main focus is process standardization and training to prevent repeat handling error.

## Impact
- Quality: 22 pcs NG SIP
- Production: interruption / loss caused by carrier fall
- Safety: falling carrier / magazine handling presents physical handling risk
- Repeat risk: high if magazine status checking and visual separation are not standardized

## Open Risk / Follow-up
- Need PD to complete physical layout separation for the 3 magazine types
- Need formal magazine-change process for unloader
- Need EQ / PD training completion and verification
- Need to confirm assembly cover is always used correctly to prevent carrier falling out

## Evidence
- Report slide titled "Cutting Dry Ice_ SIP fall to floor"
- Issue section showing NG SIP = 22 pcs, model C8.5 Small, machine EQDIC000028, time 3:30 AM 29th Jun
- Cause section explaining one carrier remained on the top side of the magazine
- Action section requiring layout separation and process/training update
