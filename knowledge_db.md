# BE EQ Knowledge Database

## Purpose
This file stores reusable BE EQ knowledge for:
- troubleshooting
- training
- incident normalization
- pattern recognition
- Watch / Hana context review
- automation / dry-run / integration support

This file is **not** intended to store every incident in full detail.  
Detailed cases should stay in `incidents/YYYY/*.md`.

---

# 1. BE SYSTEM FOUNDATION

## 1.1 Main Process Flow
Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

## 1.2 Core Engineering Principle
Most failures are **not machine breakdown**.

Main failure sources:
- Process instability
- Sensor / detection gap
- Mechanical wear / misalignment
- Interface / communication failure
- Human operation error
- Transfer / positioning issue
- Shared-line conflict or readiness gap
- False alarm / false clear / state mismatch

## 1.3 Typical Failure Chain
Small issue → false clear / wrong timing / missing feedback → jam / collision / drop / defect

## 1.4 Troubleshooting Priority
When input is unclear, use this priority:
1. Physical reality first
2. Mold / mechanical / transfer
3. Sensor / detection / false clear
4. Control / actuator / interlock
5. Interface / handshake / communication
6. Process condition / margin
7. Human operation / manual override / reset / post-maintenance gap
8. Automation / IT / routing / SFIS
9. Capacity / readiness / share-line effect

---

# 2. STATION KNOWLEDGE

## 2.1 Water Clean

### Understanding
- Core Water Clean process is relatively stable
- Water Clean is not the default high-risk station

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
- Nozzle validation / trial

### Rule
FAI pass does not mean process margin is stable enough.

---

## 2.3 Molding

### Understanding
Molding là hệ thống đa module, failure thường đến từ tương tác giữa các module hơn là 1 machine breakdown đơn lẻ. Các khối chính gồm:
- handling
- transfer
- press
- vacuum
- pellet / compound supply
- vision / PR / recipe
- MMI / lot tracking / authorization / SECS-GEM

### Core engineering principle
- Physical reality before signal
- Vacuum abnormal: nghi mold side / sealing / contamination trước
- Transfer abnormal: nghi mold incomplete / foreign material / abnormal force in mold trước
- Machine chạy nhưng output NG: kiểm mold surface / cleaning / conditioning / recipe margin trước
- Most failures are not direct machine breakdown; cần tách process / sensor / mechanical / control / interface / human

### Main troubleshooting logic
- If transfer pressure / transfer time deviates:
  - suspect mold incomplete
  - suspect foreign material in mold
  - suspect abnormal force inside mold
- If vacuum is abnormal:
  - suspect mold side first
- If machine runs but output is NG:
  - check mold surface first
- If abnormality happens after conversion / cleaning / PM:
  - check release gap, conditioning, re-qualification, and taught position recovery first
- If downstream/upstream handoff is unstable:
  - suspect false clear / timing mismatch / readiness handshake before assuming hardware failure

### Machine architecture watch points
- Cassette Handler:
  - deck / lift / pusher / double leadframe detect / loader-offloader flow
- Leadframe Handler:
  - X-Z-rotation / pushers / anti-warpage / preheat / taught position drift
- Press / Mold:
  - clamp / plunger / transfer / UOD / mold contamination / mold seating
- Vacuum:
  - board vacuum / cavity vacuum / chamber vacuum / filter / leak / settle time
- Pellet / Compound:
  - pellet age / hopper feed / delay / preheat sequence / no-pellet false state
- Vision / Recipe:
  - PR set / light / orientation / mark detect / recipe-family mismatch

### MMI / operation knowledge
Main machine states:
- Not Ready
- Initializing
- Standby / Idle
- Ready
- Executing
- Pause / Pausing
- Alarm / Alarming

Main operational modes:
- Production
- Disabled
- Inactive
- Conditioning
- Conversion
- Short shots
- Transfer cleaning
- Compression cleaning
- Dry cycle

Practical use:
- Conversion: mold/tooling change
- Conditioning: mold wax / after cleaning stabilization
- Transfer cleaning / Compression cleaning: remove residue, verify mold-transfer condition
- Dry cycle: check mechanism / motion path without full material risk

### Restart / FAI rule
- If no input > 12 hours:
  - redo FAI before restart
- After re-init / long stop / post-maintenance:
  - verify remaining leadframe / pellet / mold condition before Start
  - confirm recipe, operation mode, and machine ready state before production

### Model change rule
Must verify:
- mold chase
- PR set
- recipe
- operation mode
- tool / family / carrier reference when applicable

### Process readiness concern
Missing proper mold cleaning / smoothing / conditioning / qualification before FAI can create hidden mold surface instability.

High-risk release gap after:
- mold conversion
- cleaning
- recipe change
- PM / taught-position adjustment
- sensor or vacuum-related repair

### Maintenance / PM focus
Per shift / day main focus:
- mold cleaning
- vision backlight cleaning
- leadframe guides cleaning
- empty cull / dust / pellet dump / reject bins

Weekly / monthly focus:
- vacuum filter drain / check
- clamp unit check
- mold temperature verification
- belt tension / motion path condition
- plunger / center pin / UOD / transfer mechanism condition

### Recipe / process control focus
Critical recipe domains:
- handling settings
- press settings
- transfer settings / transfer profile
- temperature settings
- cleaning settings
- vacuum settings
- vision settings
- carrier / PR set / qualification status

Rule:
- Recipe must be qualified before production
- Parameter change after conversion / debugging should require re-check / re-qualification according to local release rule

### Quick checks for Molding
When issue is unclear, prioritize:
1. Physical blockage / mold contamination / loose hardware / jam
2. Vacuum reach / leakage / false feedback / settle time
3. Transfer path / clamp / push force / taught position
4. Sensor / detection / false clear / vision / orientation
5. Recipe / mode / family / PR mismatch
6. Human reset / manual override / post-maintenance effect
7. Interface / communication / upstream-downstream readiness


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
- laser head
- working table
- optical path

### Lifecycle / calibration rule
- Recalibration every 6 months
- Recalibration required when running a new model
- >35,000 hours: inspect / prepare replacement
- >40,000 hours: mandatory replacement

### Software / traceability
- Laser source control software
- Machine control software
- Spectra frequency learned in training: 102000 Hz
- Direct link to SFIS
- DataMatrix used
- No manual code input required

### Utility
- Water cooling required for laser head

### High-risk failure families in Laser
- post-maintenance alignment release gap
- false-clear transfer issue
- ULD / lift / conveyor communication gap
- manual override during transfer
- CT / vision instability

---

## 2.5 Dry Ice / Trench Dry Ice / Cutting DIC

### Understanding
Dry Ice is not only the nozzle.
It is a full system including:
- gas / CDA / N2
- dry ice source
- nozzle / robot
- vacuum / pedestal
- magazine / carrier / conveyor
- scanner / software / SFIS / logs / alarms

### Rule
Cold Jet output / pressure must not be adjusted freely outside spec.

### Main troubleshooting groups
- Cold Jet / output / dry ice feed
- vacuum / pedestal
- safety door / interlock
- magazine / carrier transfer
- scanner / 2D code reading
- SFIS / SMD / software communication
- false alarm vs actual status mismatch

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
If blade / chuck / table / nozzle gap condition is not controlled:
- crack risk
- burr risk
- scratch risk
- hidden defect risk
- machine may appear normal while quality is already unstable

---

## 2.7 Sputter

### High-risk subsystems
- DC power modules
- cathode / clamp
- chamber contamination
- transmission / belt / coupling / motor

### Typical repeat patterns
- DCx power alarms
- cathode short
- clamp degradation / peeling
- transmission timeout
- motor coupling loose
- chamber contamination after poor surface roughness / cleaning quality

---

## 2.8 Process Flow Rules
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

# 4. HIGH-VALUE FAILURE PATTERN LIBRARY

## 4.1 False-clear transfer pattern
### Symptom
- carrier / panel looks “cleared” by signal
- but product is still physically in transfer zone

### Typical result
- panel pop-out
- carrier drop
- collision
- product stuck between modules

### Main causes
- out sensor positioned too early
- no second confirmation
- system clears by signal only

### Stations often affected
- Laser
- ULD / Lift interface
- Dry Ice carrier transfer

---

## 4.2 Downstream fail but upstream still run
### Mechanism
Downstream module fault exists, but fault status is not returned to upstream.

### Result
- upstream keeps moving
- downstream not ready
- drop / jam / collision occurs

### Examples
- Lift fault but Laser still transfers
- ULD / conveyor stop while table still moves

---

## 4.3 Manual override during auto sequence
### Mechanism
Operator / DL / PD changes mode or resets alarm while sequence is not physically complete.

### Result
- table moves unexpectedly
- carrier / panel collision
- false restart state
- panel ejection / carrier drop

### Prevention
- block mode switch during transfer
- require physical-clear confirmation
- add popup / double confirm

---

## 4.4 System false alarm / sync mismatch
### Symptom
Machine is physically OK, but upper system / SMD / box still shows error.

### Main causes
- transient fault recovered too quickly
- state not cleared to upper system
- debounce / clear logic not sufficient

### Result
- dashboard noise
- low trust in system
- wrong escalation

---

## 4.5 Post-maintenance release gap
### Symptom
Machine just maintained; FAI or MP run fails immediately after maintain.

### Main causes
- alignment not fully restored
- optimize recipe not finished
- no release gate across EQ / ME / QA / PD
- communication by email / verbal only

### Result
- shift / cross deviation
- scrap at FAI
- avoidable downtime

---

## 4.6 Intermittent scanner / vision issue
### Symptom
Reader works sometimes, fails sometimes.

### Main causes
- focus not fine-tuned
- scanner position unstable
- barcode image blurred
- bracket loosen / vibration

### Result
- intermittent “2D reader fault”
- lane-specific unstable read
- no full machine fail, only random detection fail

---

## 4.7 Capacity / CT high
### Symptom
Machine runs without NG, but CT is above target.

### Main causes
- extra loading / unloading / transfer path
- too many intermediate motion steps
- buffer / mechanism overhead in automation mode

### Result
- capacity loss
- target not met
- UPD high

### Typical action
- compare manual vs auto path
- cut idle movement
- optimize sequence with vendor / IE

---

## 4.8 Cold Jet output instability
### Symptom
- kg or effective output below spec
- intermittent
- no obvious HW/SW change

### Main suspects
- dry ice quality variation
- partial freezing in pipe/nozzle
- real-time air fluctuation

### Quick checks
- change dry ice block
- purge before run
- compare real-time pressure, not setup only
- run repeated cycles

---

## 4.9 Mold abnormal during cleaning
### Symptom
- abnormality happens during cleaning / preparation
- not necessarily during MP run

### Main suspects
- contamination / residue
- loose element / pin problem
- mold-side mechanical interaction

### Action
- isolate first
- inspect mold-side surface / loose hardware
- monitor after temporary fix

---

## 4.10 Vision-driven CT increase
### Symptom
- one unit causes higher CT
- vision NG / cannot-detect associated

### Main suspects
- mark detect instability
- camera / alignment / optics issue
- product cleanliness / contrast issue

### Action
- compare CT by machine
- correlate with vision NG log
- verify mark condition / camera condition

---

# 5. VALIDATED JUNE SNAPSHOT (FROM CURRENT CHAT HISTORY)

> This section keeps only high-value validated June points used frequently by Agents.  
> Full case details should be stored in incidents.

## 2026-06-01
- Laser / Lift / transfer panel drop pattern captured:
  - lift fault
  - no error signal returned to laser
  - transfer continued
  - panel dropped inside machine

## 2026-06-18 to 2026-06-29
Validated June notes include:
- Laser 222 Cold Jet out of spec → adjusted, FAI OK
- WC scanner / carrier QR mismatch handling
- TDIC / Dry Ice / nozzle / pipe checks
- Mold 146 pin drop
- CPF Z-axis abnormality
- Laser CB cannot detect PCB mark
- Plasma 2 base reversed on automation line
- WC37 pressure drop
- Laser cooling connector broken by PD then replaced
- Plasma 3 SFIS not fully fixed / IT routing not complete
- Mold 147 Press 2 abnormal during cleaning
- Jigsaw blade life / brush / table calibration / fresh RO water
- LTE / GPS / curing flow rule confirmation

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
Most Watch issues should first be interpreted as:
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

## 7.3 Known readiness items from current chat
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
- Additional slots may include sputter side depending on plan

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

# 9. DOCUMENT CONTROL / REPORTING RULE

## 9.1 Document control
Any added checklist / form / verification item should be:
- updated in DCN-managed system
- version-controlled
- document-number controlled
- printed from system for use

## 9.2 Execution rule
During FAI / checksheet:
- verify first
- only then check / tick the item

## 9.3 Standard troubleshooting output
- Symptom
- Failure mechanism
- Top suspected causes
- Quick checks
- Impact
- Containment
- Corrective action
- Preventive action

## 9.4 Reporting output
- Issue
- Impact
- Root Cause
- Action
- Risk
- Next step / owner (if available)

---

# 10. OPEN ITEMS STILL NOT CLOSED
- Mold 147 Press 2 root cause
- Plasma 3 IT routing completion
- Laser CB CT root cause per machine
- WC37 pressure drop root cause
- CPF Z-axis abnormality
- TDIC #43 vacuum / dust filter abnormality
- Hades auto-line PCB mark detect issue

---

# 11. Final reminder for Agents
This file stores reusable knowledge and patterns.

Do not store every new incident here in full detail.  
New incidents should go to:
- `incidents/README.md`
- `incidents/YYYY/*.md`
``
