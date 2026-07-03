# BE EQ Knowledge Database

## Purpose
This file stores structured BE EQ knowledge, issue history, station logic, automation integration notes, and shared-line risk context for troubleshooting, training, reporting, and project readiness support.

## Data Rule
- Only confirmed information from the current chat history is included.
- Dates are assigned only when the date was explicitly stated or later explicitly corrected/confirmed.
- If the timing is not exact, information is stored under **Undated Training Knowledge** or **Cross-day Knowledge**.
- If no validated data exists for a topic, the correct answer is:
  **Data not available in current knowledge.**

---

# 1. BE SYSTEM FOUNDATION

## 1.1 Main Process Flow
Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

## 1.2 Core Engineering Principle
Most failures are **not machine breakdown**.

Main failure sources:
- Process instability
- Sensor / detection gap
- Mechanical wear
- System integration issue
- Human operation error
- Transfer / positioning issue
- Shared-line conflict or readiness gap

## 1.3 Failure Chain
Small issue → misalignment → drop → stacking → collision → defect

## 1.4 Troubleshooting Priority
1. Mold / mechanical side
2. Transfer / positioning
3. Sensor / detection
4. Control / actuator
5. Process condition / margin
6. Human operation
7. Automation / IT / routing / SFIS (if automation line)

---

# 2. STATION KNOWLEDGE

## 2.1 Water Clean
### Understanding
- Core Water Clean process is relatively stable.
- Water Clean is not the default high-risk station.

### Main watch points
- Loader / unloader aging
- Transfer interface stability
- Scanner robustness
- Carrier code compatibility

### Rule
Do not assign downstream issues to Water Clean unless:
- there is direct surface evidence, or
- transfer / handshake clearly points back to Water Clean

### Chemical / filter control
- N600: replace every 2 weeks
- Filter: replace/check every 1–2 weeks

---

## 2.2 CPF
### Understanding
Main CPF failure mode is **glue-related instability**, not direct collision.

### Main watch points
- Glue overflow
- Dot weight instability
- Valve / chamber wear
- Process margin sensitivity
- Nozzle trial / validation

### Rule
FAI pass does not mean process margin is stable enough.

---

## 2.3 Molding
### Understanding
Molding is a multi-module system:
- handling
- transfer
- press
- vacuum
- pellet / compound supply

### Main troubleshooting logic
- If transfer pressure / transfer time deviates:
  - suspect mold incomplete
  - suspect foreign material in mold
  - suspect abnormal force inside mold

- If vacuum is abnormal:
  - suspect mold side first

- If machine runs but output is NG:
  - check mold surface first

### Restart / FAI rule
- If no input > 12 hours:
  - redo FAI before restart

### Model change rule
Must verify:
- mold chase
- PR set
- recipe

### Process readiness concern
Missing proper mold cleaning / smoothing / conditioning before FAI can create hidden mold surface issues.

---

## 2.4 Laser
### Machine family
Two main machine types:
- Hans
- E&R

These use the same laser source type but are different machine families.

### Main machine structure
- load / unload
- dust extraction
- cooling
- laser head
- working table

### Critical technical focus
1. Laser head
2. Working table

### Hardest technical adjustment
- Optical path adjustment

### Source / lifecycle rule
- Recalibration every 6 months
- Recalibration required when running a new model
- >35,000 hours: inspect / prepare replacement
- >40,000 hours: mandatory replacement

### Laser software
- Laser source control software
- Machine control software
- Spectra source software frequency learned in training: 102000 Hz

### Traceability
- Direct link to SFIS
- DataMatrix used
- No manual code input required

### Utility
- Water cooling required for laser head

---

## 2.5 Dry Ice / Trench Dry Ice / Cutting DIC
### Understanding
Dry Ice is not only the nozzle.
It is a full system including:
- gas / CDA / N2
- dry ice source
- nozzle / robot
- vacuum / pedestal
- magazine transfer
- scanner / software / SFIS / alarm pages / running log

### Rule
Cold Jet output / pressure must not be adjusted freely outside spec.

### Main troubleshooting groups
- Cold Jet / output / dry ice feed
- vacuum / pedestal
- safety door / interlock
- magazine transfer
- scanner / code reading
- SFIS / software communication

---

## 2.6 Jigsaw
### PM / lifetime control
- Machine 58: blade change around 700 panels
- Other machines: blade change around 500 panels
- Blade thickness recorded in chat: 0.63 mm
- Table calibration: every 3 months
- Cleaning brush replacement: every 108000 runs

### Brush
- Material: plastic
- Function: remove saw debris

### Cleaning water
- 100% fresh RO water
- No recycle
- Direct discharge after use

### Risk
If blade / chuck / table condition is not controlled:
- crack risk
- burr risk
- hidden defect risk
- machine may appear normal while quality is already unstable

---

## 2.7 Process Flow Rules
- LTE must pass CDIC cleaning
- GPS can go directly to Sputter
- Any lot exceeding Q-time before Sputter must be cured again

---

# 3. EQUIPMENT DATA

## 3.1 Panasonic AM100
- Model: NM-EJM4D
- Dimension: 1970 × 2105 × 1500 mm
- Weight: 2780 kg
- Power:
  - 3-phase AC 200 / 220V ±10V
  - or AC 380 / 400 / 420 / 480V ±20V
  - 2.0 kVA
- Air:
  - 0.5–0.8 MPa
  - 200 L/min
- Placement speed: 35800 cph
- Placement accuracy: ±40 µm

## 3.2 Intelume CCM-A201
- Fully automatic dry ice cleaning system
- Cleans residue after laser processing
- Dual nozzle design
- Integrated:
  - dust collection
  - electric heating
  - hot air circulation
  - product adsorption / clamping
- Intended to reduce frost / condensation / secondary contamination
- Detailed facility data not validated in current knowledge

## 3.3 Han’s Laser HDZ-GL4030
- No validated detailed specification in current knowledge
- Installation manual / utility drawing still required

---

# 4. ISSUE HISTORY BY DATE

> Only dates that were explicitly given or later clearly confirmed are assigned here.

---

## 2026-06-01

### Issue: Panel dropped inside machine during LBO run
**Machine:** #232

#### Symptom
- One panel dropped inside machine during production

#### Mechanism
- SMD lift malfunctioned
- Laser did not receive corresponding error signal
- Transfer continued
- Panel fell to machine bottom

#### Issue type
- Sensor / Control / Transfer / Interlock

#### Impact
- Panel drop
- Product damage risk
- Missing stop / handshake logic
- Repeat risk if interface not corrected

#### Action / learning direction
- Need lift-to-laser error signal verification
- Need transfer block if upstream lift is abnormal
- Treat as communication / interlock gap, not simple mechanical failure only

---

## 2026-06-11

### Issue: Laser / lift communication drop case
#### Symptom
- Lift abnormality did not stop downstream action
- Panel dropped between machine modules

#### Issue type
- Control / Interface / Sensor / Transfer

#### Main logic
- Communication / handshake gap exists between lift abnormality and laser process continuation

---

## 2026-06-13

### General line notes
- Checked conveyor maintenance items
- Checked CPF glue replacement
- Machine 158 Press 2 force around 54 ton
- Laser PLC logic for loader / unloader signal was modified and re-tested

### Issue type examples that day
- Preventive maintenance
- Control logic modification
- Parameter observation

---

## 2026-06-15

### Laser Hans training note
#### Main learning
- Loader / unloader PLC logic
- Retest after modification

#### Technical knowledge captured that day
- Hans + E&R machine families
- Optical path is hardest adjustment
- Calibration and source replacement logic
- Software structure and SFIS traceability
- Water cooling requirement

---

## 2026-06-18

### Molding / mold chase / FR4 readiness
#### Note
- Mold chase / mold change before FR4 run was still under checking / follow-up

### Oven issue
#### Symptom
- Over-temperature protection issue
- If setup too low, oven cannot reach required temperature

#### Issue type
- Control / Utility / Process

### Water Clean issue
#### Symptom
- Carrier QR codes not consistent
- Scanner replacement not yet available
- Temporary handling by carrier classification

#### Issue type
- Detection / Scanner / Process control

### Laser 222
#### Symptom
- Cold Jet out of spec
- Adjusted and FAI OK

#### Issue type
- Process / Dry Ice / parameter recovery

### Jigsaw
#### Symptom
- Product code cannot be read
- Surface / DIC cleanliness suspected from note

#### Issue type
- Detection / Surface / Process interaction

### Automation Hades update
- Inline Plasma machines arrived at USI
- Installation / layout in progress
- One before Molding
- One before CPF

---

## 2026-06-22

### Training focus
- Cutting / Trench Dry Ice startup flow
- Parameter pages
- Alarm detail
- Running log
- Manual maintenance pages
- Scanner / software / InteChip usage logic

### Plasma 3
- Setup completed

### Auto shuttle
- Fault recovered, note indicates OK

### Laser cutting
#### Symptom
- Dust collector hose was bent

#### Issue type
- Utility / Exhaust / dust collection

### Sputter
#### Symptom
- Reassembled part but screw was loose

#### Issue type
- Mechanical fastening

### DL2
- FAI + first-shift check sheet mentioned

### Strong learning of the day
- Cold Jet pressure must not be adjusted freely
- Troubleshooting must follow spec, vacuum, pedestal, dust collector and alarm logic

---

## 2026-06-23

### Plasma 2
- Setup completed

### WC79
#### Symptom
- Scanner connection abnormality

#### Issue type
- Scanner / Connection / Detection

### Laser 153
- 6-month PM completed
- No special issue found

### Dry Ice 22
- Mask replaced
- Check OK
- Check sheet completed

### Automation line
- Laser stress test performed

### Saw 58
#### Symptom
- Handling / output-side issue noted
- Exact mechanism not finalized in chat

### DCN / controlled document learning
- Any new checklist / form / verification item must be updated through controlled DCN release
- Must have:
  - document number
  - revision version
  - controlled release
- FAI / checklist items must only be checked after actual verification is completed

### Sputter
- Full set of internal screws replaced

---

## 2026-06-24

### Mold 146
#### Symptom
- Pin dropped from mold
- Risk of falling onto mold chase surface

#### Impact
- Mold chase damage risk

#### Action
- Re-fixed using glue
- Daily monitoring in place

### CPF
#### Symptom
- Z-axis abnormality

#### Issue type
- Axis / mechanical / control

### Laser 230
- Quarterly PM performed
- Actual CT around 11–15 seconds

### Hades auto line / Laser CB
#### Symptom
- Cannot detect PCB mark

#### Issue type
- Vision / mark detection / automation control

### TDIC #43
#### Symptom
- Vacuum / dust filter issue

#### Issue type
- Utility / cleaning / airflow

### Plasma 3
- QR scanner optimization ongoing

---

## 2026-06-25

### Plasma 2 – automation line
#### Symptom
- Base orientation reversed
- Requires modification

#### Target
- Must finish modification and run by 2026-07-01

#### Issue type
- Mechanical integration / installation

### WC37
#### Symptom
- Pressure drop observed
- Nozzle confirmed not clogged

#### Issue type
- Utility / flow / pressure

### Laser
#### Symptom
- PD broke cooling water connector
- Connector replaced and machine recovered OK

#### Issue type
- Human / mechanical / utility

### Cold Jet tuning
- FAI = 167 kg
- Actual peak = 172

### SFIS / Baymax / TCP-IP
#### Function under integration
- Plasma automation line must send product data string through Baymax via TCP/IP to system

#### Issue type
- IT / integration / traceability

---

## 2026-06-26

### WC
- Checked 1M / 3M / 6M PM items

### TDIC
- Cold Jet changed from #22 to #26
- Checked dry ice pipe
- Cleaned nozzle

### Key symptom for #22
#### Symptom
- #22 often drops dry ice output / weight below spec
- No hardware or software change was made

#### Issue type
- Process / Utility / Intermittent

#### Main suspect logic captured in chat
- likely flow instability, not fixed hardware breakdown
- main suspects:
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
#### Symptom
- One machine still contributes to higher CT

### Plasma 3
#### Symptom
- SFIS software still not fully fixed

### 14:34
- Shifted work focus to CPF auto line

---

## 2026-06-29

### Mold 147 / Press 2
#### Symptom
- Abnormal during cleaning while preparing for Automation Hades FRB
- Press isolated and stopped from use
- Root cause investigation ongoing

#### Issue type
- Mold / cleaning abnormality / mechanical

### Jigsaw line stability
- FAI at 10:30 showed no issue
- Machine 58 and 72 running small model
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
- GPS can go direct to Sputter
- Over Q-time before Sputter → curing required

### Line status
- By 14:00 all WIP below Saw had been cleared
- Automation line bypass run showed no issue
- At that time Plasma and Sputter load/unload were not running

---

# 5. UNDATED TRAINING KNOWLEDGE (EARLY JUNE TO LATE JUNE)

## 5.1 Molding training target bundle
### Topics learned
- Alarm troubleshooting
- Advanced troubleshooting
- Model change
- Production monitoring + practice

### Core molding learning
- Transfer pressure/time abnormal → mold incomplete / foreign material / abnormal pressing force
- Vacuum abnormal → mold side first
- Model change → verify mold chase / PR set / recipe
- No input >12h → redo FAI

---

## 5.2 Laser buyoff / FAI training
### Key buyoff logic learned
Laser release is not only recipe check.
Must consider:
- X-Y table precision
- Scanner precision
- Scanner + CCD positioning accuracy
- Repeatability
- Spot circularity / beam profile
- Z parameter window
- Laser power decay

### Laser release checks repeatedly used
- recipe
- parameter
- FAI dimension
- trench shift
- trench inspection

---

## 5.3 LT Dry Ice / DIC startup knowledge
### Startup conditions learned from manual reading / training
Before running:
- compressed air main pressure around 0.6 MPa
- N2 around 0.4 MPa
- correct recipe / program
- initialize
- start
- first article / first piece before auto run

### Parameter logic learned
- hot air set temperature
- drying time
- dry ice threshold
- vacuum / negative pressure threshold
- CDA flow limit
- idle-time anti-freezing logic
- chamber temperature / humidity
- robot speed

### Important mechanism
- Delay logic and anti-freezing settings are important to prevent dry ice line freezing / clogging

---

## 5.4 Document control / DCN knowledge
### Meaning
Any added checksheet, form change, or verification item should be:
- updated in DCN-managed system
- version-controlled
- document-number controlled
- printed from system for use

### Execution rule
During FAI / checksheet:
- verify first
- only then check / tick the item

---

# 6. WATCH CONTEXT

## 6.1 Main Watch Points
- Cold Jet #22 instability
- Laser CT instability due to vision NG
- Plasma 3 SFIS not fully online
- Jigsaw blade / brush lifecycle control
- Mold 147 / Press 2 abnormality under monitoring
- Dry run control and manual fallback readiness

## 6.2 Interpretation Rule
Most Watch issues must first be interpreted as:
- process instability
- detection gap
- mechanical wear
- system integration issue
- human operation issue

Do not default to machine breakdown.

---

# 7. HANA PROJECT CONTEXT

## 7.1 Shared-line condition
- Hana shares resources / line context with Watch

## 7.2 Readiness classification
1. Machine available
2. Need transfer
3. Need new buy / long lead time
4. Can share with Watch but capacity must be controlled

## 7.3 Known readiness items from chat
- Vacuum Baking requires transfer
- Some EE lab tools have ~8 weeks lead time:
  - J-Link Pro
  - I2C/SPI shifter board
  - Battery simulator
  - Chamber

## 7.4 Main risk
- Shared-capacity conflict
- Readiness gap
- Ramp delay

---

# 8. AUTOMATION / DRY RUN KNOWLEDGE

## 8.1 Dry run slots learned
- 09:00–11:00 → Molding to trench / AVI side
- 13:00–14:00 → Plasma to CPF unload
- 15:00–16:30 → Carrier / laser flow
- Additional slots may later include sputter side depending on plan

## 8.2 Dry run record rule
For each run:
- actual start time
- actual end time
- normal running time
- issue time
- total input quantity

## 8.3 Support logic
- PD collects PCB and records time / issues
- EQ / Automation / SMD guide operation, issue handling and manual fallback

---

# 9. ISSUE PATTERN LIBRARY

## 9.1 Cold Jet / dry ice output drop pattern
### Symptom
- kg or effective output below spec
- no obvious HW/SW change
- intermittent

### Main suspects
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

## 9.2 Mold abnormal during cleaning
### Symptom
- abnormality happens during cleaning / preparation
- not necessarily during MP run itself

### Main suspects
1. contamination / residue
2. loose element / pin problem
3. mold-side mechanical interaction

### Action
- isolate first
- inspect mold-side surface / loose hardware
- monitor after temporary fix

---

## 9.3 Vision-driven CT increase
### Symptom
- one unit causes higher CT
- linked with vision NG / cannot-detect

### Main suspects
1. mark detect instability
2. camera / alignment / optics issue
3. product cleanliness / contrast issue

### Action
- compare CT by machine
- correlate with vision NG log
- verify mark condition / camera condition

---

# 10. DOCUMENT CONTROL / REPORTING FORMAT

## 10.1 Standard troubleshooting output
- Symptom
- Failure mechanism
- Top suspected causes
- Quick checks
- Impact
- Containment
- Corrective action
- Preventive action

## 10.2 Reporting output
- Issue
- Impact
- Root Cause
- Action
- Risk
- Next step / owner (if available)

---

# 11. OPEN ITEMS STILL NOT CLOSED

- Mold 147 Press 2 root cause
- Plasma 3 IT routing completion
- Laser CB CT root cause per machine
- WC37 pressure drop root cause
- CPF Z-axis abnormality
- TDIC #43 vacuum / dust filter abnormality
- Hades auto-line PCB mark detect issue

---

# 12. ANCHOR USAGE NOTE

Suggested useful anchors after upload:
- `#41-cold-jet-22-output-instability`
- `#42-mold-147-press-2-abnormal-during-cleaning`
- `#43-mold-146-pin-drop`
- `#46-plasma-3-sfis-not-fully-online`
- `#6-watch-context`
- `#7-hana-project-context`

These can be used for:
- direct section links in reports
- issue traceability
- agent grounding
