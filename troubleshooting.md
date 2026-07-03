# BE EQ Troubleshooting Log

## Scope
This file consolidates troubleshooting knowledge, issue history, process learning, automation integration notes, and line-follow up items captured in the chat history.

## Data Integrity Rule
- Only information explicitly mentioned in the chat history is included.
- If a date was not clearly validated in the chat, the item is placed under **Undated / Training Knowledge** instead of forcing a date.
- This file is intended for:
  - BE EQ troubleshooting
  - daily / weekly reporting
  - training reference
  - Watch / Hana shared-line support
  - automation / SFIS line integration

---

# 1. BE SYSTEM FOUNDATION

## 1.1 BE Main Process Flow
Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

## 1.2 Core Troubleshooting Principle
Most failures are **not** machine breakdown.

Main failure drivers:
- Process instability
- Sensor / detection gap
- Mechanical wear
- System integration issue
- Human operation error
- Transfer / positioning issue
- Shared-line conflict or readiness gap

## 1.3 Failure Chain Logic
Small issue → misalignment → drop → stacking → collision → defect

## 1.4 Troubleshooting Priority Logic
1. Mold / mechanical side
2. Transfer / positioning
3. Sensor / detection
4. Control / actuator
5. Process condition / margin
6. Human operation
7. Automation / IT / routing / SFIS (if automation line)

---

# 2. STATION TRAINING KNOWLEDGE

## 2.1 Water Clean
### General understanding
- Core Water Clean process is relatively stable.
- Water Clean is not the main core-risk station by default.

### Main watch points
- Loader / unloader aging
- Transfer interface stability
- Scanner robustness
- Carrier code compatibility

### Rule
Do not over-assign downstream issues to Water Clean unless:
- there is real surface evidence, or
- handshake / transfer logic clearly points back to Water Clean

### Chemical / filter control
- N600: replace every 2 weeks
- Filter: replace/check every 1–2 weeks

---

## 2.2 CPF
### General understanding
CPF main failure mode is **glue-related instability**, not direct collision.

### Main watch points
- Glue overflow
- Dot weight instability
- Valve / chamber wear
- Process margin sensitivity
- Nozzle validation / trial status

### Rule
FAI pass does not guarantee stable process margin.

---

## 2.3 Molding
### General understanding
Molding is a multi-module system:
- handling
- transfer
- press
- vacuum
- pellet / compound supply

### Core troubleshooting logic
- If transfer pressure/time deviates:
  - suspect mold incomplete
  - suspect foreign material in mold
  - suspect abnormal force condition inside mold

- If vacuum is abnormal:
  - suspect mold side first
  - do not default to machine side first

- If machine runs but output is NG:
  - check mold surface first

### Restart / FAI rule
- If no input > 12 hours → redo FAI before restart

### Model change rule
Must verify:
- mold chase
- PR set
- recipe

### Maintenance / startup concern
Missing proper mold cleaning / smoothing / conditioning before FAI can create hidden mold surface risk.

---

## 2.4 Laser
### Machine platform understanding
There are 2 laser machine families:
- Hans
- E&R

These are different manufacturers, but they use the same type of laser source.

### Station architecture
Laser machine includes:
- load / unload
- dust extraction
- cooling
- laser head
- working table

### Key technical learning
Most critical areas:
1. Laser head
2. Working table

Hardest technical task:
- Adjusting the optical path of laser light

### Laser source / lifecycle
- Source power around 40 W
- Model Hades uses around 34 W
- Re-calibration every 6 months or when running a new model
- >35,000 hours: inspect / prepare replacement
- >40,000 hours: mandatory replacement

### Software / control
Laser uses 2 software groups:
- laser source control
- machine control

Known source control data:
- Spectra software
- current frequency setting learned: 102000 Hz

### Traceability
- Directly linked to SFIS
- No need to manually input code
- Uses DataMatrix code

### Utility
- Water cooling required to reduce laser head temperature

---

## 2.5 Dry Ice / Trench Dry Ice / Cutting DIC
### General understanding
Dry Ice system is not just the nozzle.
It is a full system including:
- gas / CDA / N2
- dry ice source
- nozzle / robot
- vacuum / pedestal
- magazine transfer
- scanner / software / SFIS / alarm pages

### Rule
Cold Jet pressure / output must not be adjusted freely outside spec.

### Alarm / troubleshooting thinking
Priority groups:
- Cold Jet / dry ice / output
- safety door / interlock
- magazine detect
- vacuum / pedestal condition
- SFIS / communication
- code reading / scanner

---

## 2.6 Jigsaw
### Vendor PM logic
Jigsaw follows vendor-defined lifetime-based PM logic.

### Confirmed control points
- Machine 58: blade change around 700 panels
- Other machines: blade change around 500 panels
- Blade thickness noted: 0.63 mm
- Table calibration: every 3 months
- Cleaning brush replacement: every 108000 runs
- Brush material: plastic
- Brush function: remove saw debris during cleaning

### Cleaning water
- RO water is 100% fresh
- No recycle
- Used water is discharged directly

### Risk logic
If blade / chuck / table condition is not controlled:
- crack risk
- burr risk
- hidden defect risk
- machine may still look normal while process quality is already out of control

---

## 2.7 Process Flow Rules Learned
- LTE must pass CDIC cleaning
- GPS does not need CDIC and can go directly to Sputter
- Any lot exceeding Q-time before Sputter must be cured again

---

# 3. TROUBLESHOOTING ISSUE HISTORY BY DATE

> Note:
> Only dates clearly stated or later explicitly confirmed in the chat are assigned here.

---

## 2026-06-01

### Issue: Panel dropped inside machine during LBO run
**Machine:** #232  
**Symptom:**
- One panel dropped inside machine during production

**Mechanism:**
- SMD lift malfunctioned
- Laser did not receive the corresponding error signal
- Transfer continued
- Panel fell to the machine bottom

**Issue type:**
- Sensor / Control / Transfer / Interlock

**Impact:**
- Panel drop
- Potential panel damage
- Missing machine stop condition
- Interlock / handshake gap

**Action / learning direction:**
- Need to verify lift-to-laser error signal communication
- Need to block downstream transfer if upstream lift is abnormal
- Treat as integration / control issue, not simple mechanical fault only

---

## 2026-06-11

### Issue: Laser232 / lift drop communication case
**Symptom:**
- Lift abnormality did not stop transfer logic
- Panel dropped between machine modules

**Mechanism:**
- Communication / interlock gap between lift abnormality and laser process continuation

**Issue type:**
- Control / Interface / Sensor / Transfer

**Impact:**
- Product drop
- Repeat risk if signal mapping not corrected

---

## 2026-06-13

### Follow-up / maintenance note
**Items captured:**
- Checked conveyor maintenance items
- Checked CPF glue replacement
- Machine 158 Press 2 force around 54 ton
- Laser PLC logic for loader / unloader signal was modified and re-tested

**Issue type examples present:**
- Control logic modification
- Process parameter observation
- Preventive maintenance follow-up

---

## 2026-06-15

### Laser Hans training note
**Main learning focus:**
- PLC logic for loader / unloader signal
- Retest after logic modification

**Broader technical capture added that day:**
- Hans + E&R machine family knowledge
- Laser optical path is hardest adjustment
- Calibration and source replacement rules
- Laser software structure
- SFIS direct link
- Water cooling requirement

---

## 2026-06-18

### Molding / mold change / FR4 readiness
**Symptom / note:**
- Mold chase / mold change before FR4 run still under follow-up

### Oven issue
**Symptom:**
- Over-temperature protection issue
- If setup too low, oven cannot reach required temperature

**Issue type:**
- Control / Utility / Process

### Water Clean issue
**Symptom:**
- Carrier QR codes not consistent
- Scanner new unit not yet available
- Current containment: carrier classification

**Issue type:**
- Scanner / Detection / Process control

### Laser 222
**Symptom:**
- Cold Jet out of spec
- Adjusted and FAI OK

**Issue type:**
- Process / Dry Ice / parameter recovery

### Jig Saw
**Symptom:**
- Product code cannot be read
- Note points toward DIC cleaning / surface cleanliness influence

**Issue type:**
- Detection / Surface / Process interaction

### Automation Hades update
- Inline Plasma machines have arrived at USI
- Installation / layout in progress
- One planned before Molding
- One planned before CPF

---

## 2026-06-22

### Training focus: Cutting / Trench Dry Ice / manual operation / parameter logic
**Main learning:**
- Startup flow
- Parameter pages
- Alarm detail
- Running log
- Maintenance page
- Scanner / InteChip / software interaction

### Plasma 3
- Setup completed

### Auto shuttle
- Fault recovered, status noted OK

### Laser cutting
**Symptom:**
- Dust collector hose was bent

**Issue type:**
- Utility / Exhaust / dust collection

### Sputter
**Symptom:**
- Reassembled part but screw was loose

**Issue type:**
- Mechanical fastening

### DL2
- FAI + check sheet mentioned for first shift

### Strong learning of the day
- Cold Jet pressure is not allowed to be modified freely
- Must troubleshoot based on spec, dust collector condition, vacuum / pedestal condition, and alarm logic

---

## 2026-06-23

### Plasma 2
- Setup completed

### WC79
**Symptom:**
- Scanner connection abnormality

**Issue type:**
- Scanner / Connection / Detection

### Laser 153
- 6-month PM completed
- No special issue found

### Dry Ice 22
- Mask replaced
- Check OK
- Check sheet completed

### Automation line
- Laser stress test was performed

### Saw 58
**Symptom:**
- Handling / output-side issue was noted
- Exact mechanism not finalized in note

### SOP / DCN
**Learning confirmed:**
- Any new check sheet / verification item / form revision must be updated through DCN-controlled document release
- Each controlled form must have:
  - document number
  - revision version
  - controlled release
- During FAI / checklist execution, each item must be checked only after actual verification is completed

### Sputter
- Full set of internal screws replaced

---

## 2026-06-24

### Mold 146
**Symptom:**
- Pin dropped from mold
- Risk of falling onto mold chase surface and causing damage

**Containment / action:**
- Glue was applied to re-fix the pin
- Daily monitoring in place

**Issue type:**
- Mechanical / mold protection / hidden damage risk

### CPF
**Symptom:**
- Z-axis abnormality

**Issue type:**
- Axis / mechanical / control

### Laser 230
- Quarterly PM performed
- Actual CT around 11–15 seconds

### Hades auto line / Laser CB
**Symptom:**
- Cannot detect PCB mark

**Issue type:**
- Vision / detection / alignment / control

### TDIC #43
**Symptom:**
- Vacuum / dust filter issue

**Issue type:**
- Utility / vacuum / cleaning

### Plasma 3
- QR scanner optimization ongoing

---

## 2026-06-25

### Plasma 2 – automation line
**Symptom:**
- Base orientation reversed
- Requires modification

**Commitment / target:**
- Must complete modification and run by 2026-07-01

**Issue type:**
- Mechanical integration / installation

### WC37
**Symptom:**
- Pressure drop observed
- Nozzle confirmed not clogged

**Issue type:**
- Utility / pressure / flow

### Laser
**Symptom:**
- PD broke cooling water connector
- Connector replaced and machine recovered OK

**Issue type:**
- Human / mechanical / utility

### Cold Jet tuning
- FAI = 167 kg
- Actual peak = 172

### SFIS / Baymax / TCP-IP
**Function under integration:**
- Plasma automation line to send product data string to system through Baymax via TCP/IP

**Issue type:**
- IT / integration / traceability

---

## 2026-06-26

### WC
- Checked 1M / 3M / 6M PM items

### TDIC
- Cold Jet changed from #22 to #26
- Checked dry ice pipe
- Cleaned nozzle

### Key symptom learned for #22
**Symptom:**
- #22 often drops dry ice output / weight below spec
- No hardware or software change was made

**Issue type:**
- Process / Utility / Intermittent

**Mechanism learned:**
- likely flow instability instead of fixed hardware failure
- strong suspects:
  - dry ice quality variation
  - partial freezing
  - air fluctuation

### Jig Saw
- PM with belt check

### CDIC
- Checked tool / part / mask / pedestal

### Dry run
- 10:00 started Molding 157 + robot dry run
- Initially only 10% because Plasma 2 setup not complete
- 10:30 marked done

### Laser CB
**Symptom:**
- One machine still contributes to higher CT

### Plasma 3
**Symptom:**
- SFIS software still not fully fixed

### 14:34
- Shifted work focus to CPF auto line

---

## 2026-06-29

### Mold 147 / Press 2
**Symptom:**
- Abnormal during cleaning while preparing for Automation Hades FRB
- Press isolated and stopped from use
- Root cause investigation ongoing

**Issue type:**
- Mechanical / mold / cleaning abnormality

### Jig Saw line stability
- FAI at 10:30 showed no issue
- Machine 58 and 72 were running small model
- 4 sets available, currently 3 sets for C10
- Blade management confirmed:
  - machine 58 ~700 panel per blade change
  - others ~500 panel per blade change
- Blade thickness: 0.63 mm
- Table calibration: every 3 months
- Brush replacement: every 108000 runs
- RO fresh cleaning water, no recycle

### Process flow confirmation
- LTE must go CDIC
- GPS can go direct to sputter
- Over Q-time before sputter → curing required

### Line status
- By 14:00 all WIP below saw had been cleared
- Automation line bypass run showed no issue
- At that time plasma and sputter load/unload were not running

---

# 4. AUTOMATION / SFIS / SHARED-LINE INTEGRATION

## 4.1 Plasma 3 SFIS
### Confirmed status
- Plasma 3 can send data to SFIS
- Machine-side software behavior became normal
- IT still has not completed route / routing on system side
- Therefore, station still cannot be fully online

### Interface path learned
- Baymax ↔ machine
- TCP/IP
- product string / data sending to system

### Main issue type
- IT / routing / integration / readiness

### Impact
- Traceability incomplete
- Online station cannot be fully released
- Shared automation ramp risk remains

---

## 4.2 Dry run plan logic learned
### Time slots learned
- 09:00–11:00 → Molding to trench / AVI side
- 13:00–14:00 → Plasma to CPF unload
- 15:00–16:30 → Carrier / laser flow
- Additional flow includes sputter side depending on line slot

### Control method
For each run, need to record:
- actual start time
- actual end time
- normal running time
- issue time
- total input quantity

### Support logic
- PD collects PCB and records time / issues
- EQ / Automation / SMD guide operation, issue handling, manual fallback

---

# 5. WATCH / HANA CONTEXT LEARNED IN CHAT

## 5.1 Watch context
Main watch items repeatedly appearing in chat:
- Cold Jet #22 output instability
- Laser CT instability due to vision NG
- Plasma 3 SFIS not online because IT routing not finished
- Jigsaw blade / brush lifetime control
- Mold 147 Press 2 abnormality under monitoring
- Dry run control and manual fallback readiness

## 5.2 Hana context
Hana shares line / resource context with Watch.

### Known readiness principles captured
- Majority of machine capability is already available
- Vacuum baking is an exception requiring transfer
- Some EE lab tools are missing / long lead time (~8 weeks), such as:
  - J-Link Pro
  - I2C/SPI shifter board
  - Battery simulator
  - Chamber

### Risk themes
- shared-capacity conflict
- equipment readiness gap
- transfer dependency
- ramp delay risk

---

# 6. ISSUE-TYPE LIBRARY DERIVED FROM CHAT

## 6.1 Mechanical
- Mold pin drop
- Loose screw after reassembly
- Cooling water connector break
- Dust hose bent
- Base installed in reverse direction
- Jigsaw wear / brush / blade / table condition

## 6.2 Electrical / Control
- Loader / unloader PLC logic modification
- Signal handshake gap between lift and laser
- Z-axis abnormality
- software not fully sending / routing data

## 6.3 Sensor / Detection
- PCB mark cannot be detected
- Vision NG drives CT increase
- Scanner connector abnormality
- Product code cannot be read
- QR code inconsistency

## 6.4 Process
- Cold Jet unstable output
- Kgs / output drift below spec
- vacuum / dust filter issue
- molding transfer / vacuum / mold-side logic
- glue instability in CPF
- Water Clean surface / scanner compatibility

## 6.5 IT / Integration
- SFIS routing not done
- Baymax TCP-IP string send path
- online station not completed
- Agent knowledge retrieval limitation

## 6.6 Utility
- pressure drop
- CDA fluctuation
- dust collection weakness
- RO water standard
- oven setup / over-temp logic

## 6.7 Planning / Capacity / Readiness
- Hana shares resources with Watch
- transfer lead item exists
- some lab / validation items have long lead time
- dry run readiness and manual fallback planning required

---

# 7. TROUBLESHOOTING PATTERNS CAPTURED FOR AGENT USE

## 7.1 Cold Jet / dry ice output drop pattern
### Symptom
- kg or effective output below spec
- no obvious HW/SW change
- intermittent

### Top suspect
1. dry ice quality variation
2. partial freezing in pipe/nozzle
3. real-time air fluctuation

### Quick check
- change dry ice block
- purge before run
- compare real-time pressure, not setup only
- run repeated cycles

### Prevention
- add repeatability check before release
- log kg trend by shift / machine

---

## 7.2 Mold abnormal during cleaning
### Symptom
- abnormality happens during cleaning / prep, not necessarily during MP run

### Top suspect
1. contamination / residue
2. loose element / pin problem
3. mold-side mechanical interaction

### Action
- isolate first
- do not continue running blindly
- inspect mold-side surface / loose hardware
- monitor after temporary fix

---

## 7.3 Vision-driven CT increase
### Symptom
- one unit in laser line causes higher CT
- linked with cannot-detect / vision NG

### Top suspect
1. mark detect instability
2. camera / alignment / optics issue
3. product cleanliness / contrast issue

### Action
- separate CT by machine
- correlate with vision NG log
- verify mark condition / camera condition

---

# 8. OPEN ITEMS STILL NOT CLOSED IN CHAT

## Open / under follow-up
- Mold 147 Press 2 root cause
- Plasma 3 IT routing to complete online release
- Laser CB CT root cause per machine
- WC37 pressure drop real root cause
- CPF Z-axis abnormality
- TDIC #43 vacuum / dust filter issue
- Hades auto line PCB mark detect issue

---

# 9. REPORTING TEMPLATE DERIVED FROM CHAT

## Short reporting format
- Issue
- Impact
- Root Cause
- Action
- Risk

## Troubleshooting format
- Symptom
- Failure mechanism
- Top suspected causes
- Quick checks
- Containment
- Prevention

---

# 10. NOTES FOR REPO USE

## Recommended section anchors
Example GitHub links after upload:
- `#cold-jet-22`
- `#mold-147--press-2`
- `#plasma-3-sfis`
- `#2026-06-25`
- `#issue-type-library-derived-from-chat`

These anchors can be used for:
- precise linking in reports
- agent grounding
- line-by-line knowledge navigation

---
# END OF FILE
