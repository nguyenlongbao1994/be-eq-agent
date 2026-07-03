---
id: INC-2022-10-11-MOLDING-C85BIG-CRACK-6PCS-EQMLD00147
date: 2022-10-11
time: "01:05 PM"
station: Molding
machine: EQMLD00147
model: C8.5 Big
issue_type:
  - Mechanical
  - Transfer
  - Handling
  - Process
status: Recovered / Monitoring
owner: EQ
tags:
  - molding
  - c8.5-big
  - crack
  - 6pcs
  - brake-shaft
  - leadframe-handler
  - transfer
  - pcb-crack
---

# Molding C8.5 Big Crack 6 Pcs – EQMLD00147

## Issue
- Machine: Molding EQMLD00147
- Model: C8.5 Big
- Quantity NG: 6 PCS
- Time: 01:05 PM (11/10/2022)

## Symptom
- 6 pcs were cracked during molding process.
- The defect was associated with leadframe handler movement / transfer.

## Root Cause
- Brake shaft was broken.
- Because the brake shaft was broken, it could not hold the PCB when the leadframe handle was moving.
- When the leadframe handle turned at high speed to transfer PCB, the panel moved out of the leadframe handle before the leadframe handle moved up.
- The panel movement then resulted in PCB crack.

## Failure Mechanism
- The brake shaft is intended to hold / stabilize the PCB during leadframe-handle movement.
- Once the brake shaft was broken, PCB holding function was lost.
- During high-speed turning / transfer, the panel shifted or moved out of the leadframe handle too early.
- Because the panel was no longer properly held during the transfer sequence, PCB crack occurred.

## Actions
- Replaced the brake shaft of the leadframe handler with a new part so that the PCB can be held correctly during leadframe-handle movement.
- The report states: machine recover normal form 01:45 AM.
  - Note: the time is transcribed exactly from the slide and may require original source confirmation if AM/PM timing needs strict validation.

## Current Status
- Brake shaft was replaced.
- Machine recovered to normal condition after replacement.
- Current status: recovered, continue monitoring for repeat risk.

## Impact
- Quality: 6 pcs cracked
- Production: machine interrupted until brake shaft replacement
- Safety: not stated in the report
- Repeat risk: present if brake-shaft wear / breakage is not monitored

## Open Risk / Follow-up
- Need to monitor brake shaft condition / holding function during transfer
- Need to ensure leadframe handler can hold PCB stably during high-speed turning movement

## Evidence
- Attached issue-analysis slides showing:
  - brake shaft broken
  - cracked panel strip
  - panel movement out of leadframe handler
  - leadframe handle movement path
