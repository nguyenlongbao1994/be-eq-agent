---
id: INC-2024-11-22-MOLDING-MODEL-SERVER-CANNOT-READ-DATABASE-EQMLD00146
date: 2024-11-22
time: "04:15 AM"
station: Molding
machine: EQMLD00146
model: C8.5 Small
issue_type:
  - IT
  - Software
  - Database
  - PC
status: Recovered / Preventive action defined
owner: EQ / BESI
tags:
  - molding
  - c8.5-small
  - model-server
  - database
  - blue-screen
  - software-conflict
  - backup-restore
  - pc
---

# Model server can't be reading the model out of database – EQMLD00146

## Issue
- Issue description: Model server can't be reading the model out of database
- Model: C8.5 Small
- Impact quantity: 02 panels
- Machine: EQMLD00146
- Time: 04:15 AM (22/11/2024)

## Timeline
- 21/11 20:10 → Big cleaning process
- 21/11 22:45 → FAI
- 22/11 04:20 → PC screen had lag and could not be controlled
- After PC restart, the software could not be turned on

## Symptom
- Model server could not read model data out of database.
- PC screen lagged and could not be controlled.
- After restart, machine software could not be turned on.

## Root Cause Analysis (initial EQ check)
1. Checked and cleaned inside the PC  
   - No abnormality detected

2. Checked the fuse area  
   - Used electricity meter to measure continuity
   - All fuses were normal

### Initial conclusion
- The root cause of the problem had not yet been found during the initial EQ check.

## Temporary Action
1. Run Molding machine (EQMLD000147) for day shift
2. Contact BESI vendor to come and check the machine

## Vendor Analysis
1. Cloned new hard disk from original hard disk and installed it to the molding PC  
   - Still could not open machine application

2. Used empty recipe database to test  
   - Still failed
   - This issue was not related to recipe database

3. Restored machine software by latest backup file  
   - Machine application could be opened normally

## Vendor / IT conclusion
- BESI IT confirmed there was a software conflict leading to blue screen
- One database file became error / corrupted
- Because of this condition, machine application could not be opened

## Failure Mechanism
- A software conflict caused the molding PC to enter unstable / blue-screen condition.
- During this fault, one database file became abnormal.
- Because machine application depends on valid software/database environment, the application could not be launched after restart.
- Testing with a cloned disk and empty recipe database showed the problem was not caused by recipe database content itself.
- Recovery was only achieved after restoring machine software from the latest backup.

## Corrective / Preventive Actions
1. Restore machine by latest backup file  
   - Machine recovered

2. Perform dry-run testing to ensure machine runs normally after restore

3. Back up machine software every 3 months

## Current Status
- Machine recovered after software restore from latest backup
- Preventive action defined: periodic software backup every 3 months

## Impact
- Quality: 02 panels impacted
- Production: machine could not run until software recovery was completed
- Safety: not stated in the report
- Repeat risk: possible if backup control and software integrity management are not maintained

## Open Risk / Follow-up
- Need to confirm stable operation after dry-run and production restart
- Need to maintain software backup discipline every 3 months
- Need to watch for recurrence of blue-screen / application start failure

## Evidence
- Attached slides showed:
  - issue timeline
  - blue-screen display
  - PC / fuse checking photos
  - restored machine application screen after recovery
