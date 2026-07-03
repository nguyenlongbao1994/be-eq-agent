# BE EQ Knowledge Database

## Purpose
This file stores structured BE EQ knowledge for troubleshooting, reporting, training, automation integration, and shared-line risk analysis.

---

# 1. BE SYSTEM FOUNDATION

## 1.1 Main Process Flow
Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

## 1.2 Core Engineering Principle
Most failures are **not** machine breakdown.

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
7. Automation / IT / routing / SFIS (if auto line)

---

# 2. STATION KNOWLEDGE

## 2.1 Water Clean
### Understanding
- Core Water Clean process is relatively stable.
- Water Clean is not the default high-risk process station.

### Main watch points
- Loader / unloader aging
- Transfer interface
- Scanner robustness
- Carrier code compatibility

### Rule
Do not assign downstream issues to Water Clean without:
- clear surface evidence, or
- handshake / transfer evidence

### Control
- N600: replace every 2 weeks
- Filter: replace / check every 1–2 weeks

---

## 2.2 CPF
### Understanding
Main CPF risk is glue instability, not direct collision.

### Main watch points
- Glue overflow
- Dot weight instability
- Valve / chamber wear
- Process margin sensitivity
- Nozzle validation / trial

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
- If transfer pressure / time deviates:
  - suspect mold incomplete
  - suspect foreign material in mold
  - suspect abnormal force inside mold

- If vacuum is abnormal:
  - suspect mold side first

- If machine runs but output is NG:
  - check mold surface first

### Restart rule
- If no input > 12 hours:
  - redo FAI before restart

### Model change rule
Must verify:
- mold chase
- PR set
- recipe

### Process readiness
Missing proper cleaning / smoothing / conditioning before FAI may create hidden mold surface issues.

---

## 2.4 Laser
### Machine family
Two main machine types:
- Hans
- E&R

They are different manufacturers but use the same laser source type.

### Main machine sections
- load / unload
- dust extraction
- cooling
- laser head
- working table

### Critical technical focus
1. Laser head
2. Working table

### Hardest technical adjustment
- Optical path alignment

### Calibration / lifecycle
- Recalibration every 6 months
- Recalibration also required when running a new model
- >35,000 hours: inspect / prepare source replacement
- >40,000 hours: mandatory source replacement

### Laser software
- One software for laser source control
- One software for machine control
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
- scanner / software / SFIS / logs / alarms

### Rule
Cold Jet output / pressure must not be adjusted freely outside defined spec.

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
- Blade thickness noted in line learning: 0.63 mm
- Table calibration every 3 months
- Cleaning brush replacement every 108000 runs

### Brush
- Material: plastic
- Function: remove saw debris during cleaning

### Cleaning water
- 100% fresh RO water
- No recycle
- Direct discharge after use

### Risk
If blade / chuck / table condition is not controlled:
- crack risk
- burr risk
- hidden defect risk
- machine may appear normal while process quality is already unstable

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
- Speed: 35800 cph
- Accuracy: ±40 µm

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

# 4. ISSUE DATABASE

## 4.1 Cold Jet #22 Output Instability
### Symptom
- Dry ice output / weight drops below spec
- Intermittent behavior
- No hardware or software change noted

### Failure mechanism
- Flow instability due to pressure / temperature / feed dynamics
- Partial freezing may restrict actual flow without full clogging

### Top suspects
1. Dry ice quality variation
2. Partial nozzle freezing
3. CDA fluctuation

### Quick checks
- Change dry ice block
- Purge system before run
- Check real-time air pressure, not setpoint only
- Run ≥3 repeat cycles

### Impact
- Cleaning instability
- Hidden contamination risk
- Yield impact
- Hard-to-catch intermittent pattern

### Action
- Purge before run
- Clean nozzle / pipe
- Log weight trend per shift

---

## 4.2 Mold 147 Press 2 Abnormal During Cleaning
### Symptom
- Press 2 abnormal during cleaning while preparing for Automation Hades FRB

### Condition
- Isolated and stopped from use
- Root cause still under investigation

### Main risk
- Mold-side abnormality
- Potential hidden mechanical issue

---

## 4.3 Mold 146 Pin Drop
### Symptom
- Pin dropped from mold
- Risk of falling onto mold chase surface

### Impact
- Mold chase surface damage risk

### Action
- Pin was re-fixed using glue
- Daily monitoring in place

---

## 4.4 Laser CB Cannot Detect PCB Mark
### Symptom
- Hades auto line Laser CB cannot detect PCB mark

### Possible impact
- CT increase
- Detection instability
- Automation readiness risk

---

## 4.5 Laser CT Instability
### Symptom
- One laser unit causes higher CT
- Vision NG / cannot detect was associated in note

### Impact
- Throughput loss
- Automation unbalance
- Possible repeat issue if mark / optics / alignment not controlled

---

## 4.6 Plasma 3 SFIS Not Fully Online
### Status
- Machine side can send data to SFIS
- Software behavior normal
- IT routing not completed
- Station cannot be fully online

### Interface path
- Machine ↔ Baymax via TCP/IP
- Product data string sent to system

### Impact
- Traceability incomplete
- Automation line integration incomplete

---

## 4.7 WC Scanner / Carrier Code Compatibility
### Symptom
- Carrier QR code not consistent
- Scanner replacement not yet available
- Temporary containment done by carrier classification

### Impact
- Scanner detect instability
- Loading / identification variability

---

## 4.8 CPF Z-axis Abnormality
### Symptom
- Z-axis issue noted in CPF

### Status
- Requires follow-up / root cause narrowing

---

## 4.9 TDIC #43 Vacuum / Dust Filter Issue
### Symptom
- Vacuum / dust filter abnormality at TDIC #43

### Issue type
- Utility / cleaning / airflow / vacuum

---

## 4.10 Laser Cooling Water Connector Broken by PD
### Symptom
- Cooling water connector broken during operation / handling

### Action
- Replaced with new connector
- Machine recovered OK

### Issue type
- Human / mechanical / utility

---

## 4.11 WC37 Pressure Drop
### Symptom
- Pressure drop observed
- Nozzle confirmed not clogged

### Issue type
- Utility / flow / pressure

### Status
- Root cause needs further isolation

---

## 4.12 Laser Cutting Dust Collector Hose Bent
### Symptom
- Dust collector hose bent in laser cutting area

### Impact
- Dust extraction efficiency risk
- Cleaning / contamination / fume removal concern

---

## 4.13 Sputter Screw Loose After Reassembly
### Symptom
- Part reassembled but screw loose

### Action
- Later internal screws were fully replaced

---

## 4.14 Product Code Read NG at Jigsaw
### Symptom
- Product code read failed

### Suspected connection in note
- Related to surface cleanliness / DIC cleaning condition

---

# 5. AUTOMATION / DRY RUN KNOWLEDGE

## 5.1 Dry run slots learned
- 09:00–11:00 → Molding to AVI / trench side
- 13:00–14:00 → Plasma to CPF unload
- 15:00–16:30 → Carrier / laser flow
- Additional line slots may cover sputter side depending on run plan

## 5.2 Dry run record rule
For each run:
- actual start time
- actual end time
- normal running time
- issue time
- total input quantity

## 5.3 Support role logic
- PD collects PCB and records time / issue
- EQ / Automation / SMD guide operation, manual fallback, troubleshooting

---

# 6. WATCH CONTEXT

## 6.1 Main Watch Points
- Cold Jet #22 instability
- Laser CT instability due to vision NG
- Plasma 3 SFIS not fully online
- Jigsaw blade / brush lifetime control
- Mold 147 Press 2 cleaning abnormality under monitoring
- Dry run control and manual fallback readiness

## 6.2 Watch Interpretation Rule
Most issues should first be interpreted as:
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

## 7.2 Readiness principle
Classify readiness into:
1. Machine available
2. Need transfer
3. Need new buy
4. Can share with Watch but capacity must be controlled

## 7.3 Known example from chat
- Vacuum Baking requires transfer
- Several lab tools have ~8 weeks lead time:
  - J-Link Pro
  - I2C/SPI shifter board
  - Battery simulator
  - Chamber

## 7.4 Main risk
- Shared-capacity conflict
- Readiness gap
- Ramp delay

---

# 8. DOCUMENT CONTROL / DCN

## Rule learned
When any checklist / verification item / form changes:
- update through DCN-controlled document system
- must have:
  - document number
  - revision version
  - controlled release
- operator / engineer should print from system
- each FAI / checklist item should only be checked after actual completion / verification

---

# 9. RECOMMENDED TROUBLESHOOTING OUTPUT FORMAT

## Standard troubleshooting output
- Symptom
- Failure mechanism
- Top suspected causes
- Quick checks
- Impact
- Containment
- Corrective action
- Preventive action

## Report format
- Issue
- Impact
- Root Cause
- Action
- Risk
- Owner / next step (if available)

---

# 10. OPEN ITEMS STILL NOT CLOSED

- Mold 147 Press 2 root cause
- Plasma 3 IT routing completion
- Laser CB CT root cause per machine
- WC37 pressure drop root cause
- CPF Z-axis abnormality
- TDIC #43 vacuum / dust filter abnormality
- Hades auto line PCB-mark detection issue

---

# 11. ANCHOR USAGE NOTE

Suggested section anchors after upload:
- `#41-cold-jet-22-output-instability`
- `#42-mold-147-press-2-abnormal-during-cleaning`
- `#46-plasma-3-sfis-not-fully-online`
- `#6-watch-context`
- `#7-hana-project-context`

Use these for:
- direct report links
- troubleshooting reference
- Agent grounding
``
