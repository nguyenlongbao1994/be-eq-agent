# BE EQ Troubleshooting Playbook

## Scope
This file is the **line-ready troubleshooting playbook** for BE EQ and Agents.

Use this file for:
- quick troubleshooting at line
- short engineering reporting
- failure-chain identification
- repeat issue comparison
- incident conversion guidance
- training support for EQ / PD / ME
- Watch / Hana support when troubleshooting touches readiness, automation, or shared-capacity risk

This file should focus on:
- how to troubleshoot
- what to check first
- how to classify issue
- how to write outputs consistently
- what recurring patterns matter most

Detailed case history should mainly stay in:
- `incidents/README.md`
- `incidents/YYYY/*.md`

---

# 1. Core Troubleshooting Principle

Most BE failures are **not** full machine breakdown.

Common failure sources:
- Process instability
- Sensor / detection gap
- Mechanical wear / misalignment
- Interface / communication failure
- Human operation error
- False alarm / false clear
- Capacity / readiness mismatch

---

# 2. First Rule: Physical Reality Before Signal

Before trusting alarm / PLC / software / system status, always check:

- Is the panel really out?
- Is the carrier really cleared?
- Is the conveyor / lift / ULD really moving?
- Is downstream really ready?
- Is the sensor detecting real position or only a partial-clear condition?
- Was alarm cleared on machine only, or also on system?

## Key principle
**Physical reality > system assumption**

---

# 3. Standard Troubleshooting Order

When issue happens, check in this order:

1. Physical blockage / mechanical / transfer
2. Sensor / detection / false clear
3. Control / actuator / interlock
4. Interface / handshake / communication
5. Process condition / margin / material
6. Human operation / reset / manual override / post-maintenance effect
7. Capacity / readiness / automation efficiency (if relevant)

---

# 4. Quick Classification Guide

| Symptom | First suspect |
|---|---|
| panel dropped / popped out / carrier collision | false clear / no feedback / manual override |
| machine OK but system shows error | sync gap / false alarm |
| FAI fail right after maintenance | release gap / alignment / optimize not finished |
| CT high but no quality NG | transfer path / sequence / automation efficiency |
| residue / peeling / edge defect while machine all OK | process interaction / material / upstream |
| intermittent 2D reader fault | focus / tuning / scanner stability |
| DC power alarm | DC module / clamp / cathode / contamination |
| transmission timeout in Sputter | belt / coupling / motor / driver / tray jam |
| corner crack / scratch / burr at cutting | blade gap / blade cycle / panel flatness |
| no obvious alarm but jam / impact occurs | unsafe manual handling / hidden transfer mismatch |

---

# 5. High-Risk Failure Chains

## 5.1 False Clear Chain
Panel or carrier is still physically inside, but system thinks it is already out.

### Result
- carrier drop
- panel pop-out
- collision
- panel stuck between stations

### Typical trigger
- out sensor positioned too early
- no second verification
- logic clears by signal only

---

## 5.2 Downstream Fail But Upstream Still Run
Downstream station is abnormal, but fault status is not returned to upstream.

### Result
- upstream continues transfer
- conveyor / lift not moving
- panel drops or jams between stations

### Typical example
- Lift fault but Laser keeps transferring
- ULD / conveyor stopped while table still moves

---

## 5.3 Manual Override During Auto Sequence
Operator / DL / PD resets alarm or changes Auto / Manual when product is not yet fully cleared.

### Result
- auto sequence breaks
- table continues movement with product still inside
- panel pop-out / carrier drop / collision

### Prevention
- block mode change during transfer
- confirm panel fully cleared before reset
- add double confirm or interlock

---

## 5.4 System False Alarm / Sync Mismatch
Machine is physically OK, but upper system / SMD / box still shows ERROR.

### Result
- false escalation
- noisy dashboard
- low trust in system state

### Typical causes
- transient fault recovers too quickly
- clear state not updated to upper layer
- no debounce / no clear logic

---

## 5.5 Post-Maintenance Release Gap
Maintenance was done, but:
- alignment not fully restored
- optimization not finished
- EQ / ME / QA not all confirmed
- PD still runs FAI

### Result
- FAI fail
- cut shift / cross deviation
- avoidable scrap

### Prevention
- machine release gate
- no action based on email / verbal only
- system status confirmation before FAI

---

## 5.6 Capacity / CT High
Machine quality result is OK, but automatic mode CT is much higher than target.

### Result
- capacity loss
- bottleneck
- UPD high
- wrong judgment if only output quality is checked

### Typical causes
- extra load / unload / transfer path
- too many intermediate motion steps
- poor motion sequence
- non-optimized automation logic

---

# 6. Station-Specific Quick Checklists

## 6.1 Water Clean
Check:
- loader / unloader status
- scanner robustness
- carrier code compatibility
- transfer stability

Do not over-assign downstream issue to Water Clean without:
- real surface evidence
- clear handshake / transfer relation

---

## 6.2 CPF
Check:
- glue overflow
- dot weight
- valve / chamber wear
- nozzle validation
- process margin

Remember:
- FAI pass does not guarantee stable process margin

---

## 6.3 Molding
Check:
- transfer pressure / transfer time
- vacuum
- mold surface
- contamination / foreign material
- pellet / compound condition
- mold-side abnormality before assuming machine-side issue

Rules:
- vacuum abnormal → check mold side first
- if no input > 12 hours → redo FAI before restart
- if machine runs but output NG → check mold surface first

---

## 6.4 Laser / ULD / Lift / Conveyor
Check:
- panel fully out or not?
- out sensor positioned too early?
- ULD / lift / conveyor really running?
- downstream fault fed back to laser or not?
- any manual mode switch during transfer?
- any reset without physical verification?
- any post-maintenance alignment or release issue?
- vision mark detection / CT / lens / Z-focus / power stability

Typical recurring chains:
- panel not fully out + table still move
- lift NG + no feedback to laser
- ULD jam recovery without physical-clear confirmation
- FAI run before machine release after maintenance

---

## 6.5 LT Dry Ice / Cutting Dry Ice / Dry Ice
Check:
- scanner / reader focus
- lane A vs lane B difference
- carrier / conveyor actual position
- SMD / machine state mismatch
- blade / nozzle / weight / output consistency
- intermittent issue or full fail?
- Cold Jet / blade / nozzle / vacuum / pedestal

Remember:
- Dry Ice is a full system, not nozzle only

---

## 6.6 Jigsaw / Saw
Check:
- blade cycle count
- nozzle-to-panel gap
- panel flatness / curvature
- blade-side error mapping
- test by bare panel
- scratches / dimension / vision stop relation
- blade / brush / table condition

If symptom is:
- scratches on PCB surface
- dimension fail
- edge burr
- corner crack
Then always compare:
- blade life
- nozzle gap
- panel curvature
- chuck / spindle / table condition

---

## 6.7 Sputter (MUST HAVE)

### 6.7.1 DC Power Alarm
Check:
- which DC channel alarmed (DC1 / DC4 / DC5 / DC7 …)
- measured DC output value vs normal reference
- cathode separation condition
- clamp condition
- whether product / tray NG exists or not

Typical pattern:
- cathode OK
- DC output abnormal
- replace DC module → recover

### 6.7.2 Cathode / Clamp / Peeling
Check:
- cathode short or not
- clamp surface roughness / peeling
- contamination / conductive debris
- chamber contamination
- DC power relation

Typical pattern:
- clamp degradation / peeling
→ cathode short
→ DC power alarm

### 6.7.3 Transmission Timeout / CHx Path
Check:
- tray physically stuck or not
- belt / coupling / motor / driver
- fixing screw integrity
- transmission guide wear
- driver communication error

Typical pattern:
- coupling loose because fixing screw damaged
- rubbing over time
- disengagement
- timeout + communication alarm

### 6.7.4 Emergency Stop / EMO
Check:
- electrical power distribution
- front / rear cabinet power state
- EMO button position
- whether shutdown is safety-triggered or equipment-triggered

Typical pattern:
- machine shutdown
- no equipment fault
- EMO pressed by human operation

### 6.7.5 Chamber / Surface / Cleaning Vendor
If chamber-related or peeling-related issue repeats:
- review cleaning vendor quality
- review roughness spec
- check shield / clamp / cathode contamination
- verify updated part source

---

## 6.8 Automation / Capacity
Check:
- process time vs transfer time
- auto path vs manual path
- extra buffer / mechanism steps
- load/unload bottleneck
- vendor motion optimization need
- manual fallback path

---

# 7. Quick Checks by Failure Type

## Mechanical / Transfer
- remove jam and inspect physically
- verify all moving parts free
- check product / carrier still inside zone or not
- confirm real position, not system position only

## Sensor / Detection
- confirm detect point
- check if signal turns ON too early
- check focus / vision / image quality
- compare lane A vs lane B if applicable

## Control / Interface
- verify handshake between modules
- confirm downstream ready signal exists
- check if upstream is blocked when downstream NG
- validate reset / clear logic

## Process / Material
- compare lot / upstream state
- check edge-only / corner-only pattern
- verify cosmetic / adhesion / residue / contamination
- confirm if all machine condition is in spec

## Human / Operation
- any manual reset?
- any auto / manual switch?
- any action during transfer?
- any missed PM / release / confirmation step?
- any EMO / safety trigger by operator?

---

# 8. Validated Training / Knowledge Snapshot

## 8.1 Water Clean
- Core Water Clean process is relatively stable
- Main concerns:
  - loader / unloader aging
  - transfer interface
  - scanner robustness
  - carrier compatibility
- N600: replace every 2 weeks
- Filter: replace / check every 1–2 weeks

## 8.2 CPF
- Main CPF risk is glue-related instability
- FAI pass does not mean process margin is stable

## 8.3 Molding
- Multi-module system:
  - handling
  - transfer
  - press
  - vacuum
  - pellet / compound
- Transfer abnormal → suspect mold-side incomplete / contamination / force abnormality
- Vacuum abnormal → mold side first
- Model change → verify mold chase / PR set / recipe

## 8.4 Laser
- Main technical focus:
  - laser head
  - working table
  - optical path
- Laser source:
  - recalibration every 6 months
  - inspect / prepare replacement after ~35,000 hours
  - mandatory replacement after ~40,000 hours
- Direct link to SFIS
- DataMatrix used
- Water cooling required

## 8.5 Dry Ice / LT Dry Ice / Cutting Dry Ice
- Not only nozzle:
  - CDA / N2
  - dry ice source
  - nozzle / robot
  - vacuum / pedestal
  - magazine / carrier / conveyor
  - scanner / SMD / SFIS
- Cold Jet pressure must not be adjusted freely outside spec

## 8.6 Jigsaw
- Machine 58: blade ~700 panels
- Other machines: blade ~500 panels
- Blade thickness: 0.63 mm
- Table calibration: every 3 months
- Brush replacement: every 108000 runs
- RO water is 100% fresh

## 8.7 Sputter
Validated recurring lessons:
- DC module failure can cause alarm even when cathode itself is OK
- Clamp / cathode peeling can trigger short + DC power alarm
- Transmission timeout can be linkage between:
  - mechanical jam
  - coupling loose
  - motor / driver issue
- EMO cases must be separated from equipment fault cases

---

# 9. Validated June-to-Now Snapshot (Frequently Reused)

These lessons were repeatedly reused in chat and should remain easy to find:

## Laser / Transfer / Automation
- Lift / ULD communication gap can cause panel drop if downstream fault is not returned upstream
- Laser transfer / ULD / conveyor issues often fail by:
  - false clear
  - manual override
  - no panel-clear double check
  - no feedback signal
- Post-maintenance release gap can create FAI fail / cut shift even when machine “looks maintained”
- Machine can be physically OK while system / sequence is still unsafe

## Dry Ice / LT Dry Ice / Cutting Dry Ice
- WC / scanner / carrier QR mismatch was a real process-control issue
- Lane reader unstable is often a tuning / focus / blur issue rather than full scanner breakdown
- SMD false alarm can occur while machine is physically normal

## Jigsaw / Saw
- Blade-nozzle gap + blade cycle + panel curvature are recurring root chains for:
  - scratches
  - dimension fail
  - vision stop
  - corner crack

## Sputter
- DC1 / DC4 / DC5 / DC7 alarms are recurring power-side patterns
- CHB / transmission timeouts can be mechanical linkage issues, not only sensor errors
- Clamp surface quality and peeling are critical repeat causes
- Emergency stop (EMO) must be treated as human safety operation unless evidence says equipment fault

## June line-specific notes often referenced
- Cold Jet #22 intermittent output drop likely tied to dry ice quality / freezing / air fluctuation
- Plasma 3 SFIS send OK but routing not complete = not fully online
- Mold 147 Press 2 abnormal during cleaning remained open
- Laser CB CT increase linked to machine-specific cannot-detect / vision behavior
- Jigsaw blade / brush / table control directly affects stable quality

---

# 10. Watch / Hana Quick Context

## Watch
When issue relates to Watch, emphasize:
- repeat issue risk
- CT / bottleneck effect
- machine stability trend
- dry-run / manual fallback
- integration / online readiness

## Hana
When issue relates to Hana, also check:
- share line with Watch
- share machine / capacity conflict
- readiness
- transfer / new buy / long lead item risk

---

# 11. Standard Short Output Format

## Troubleshooting format
- Symptom
- Failure mechanism
- Related history
- Top suspected causes
- Quick checks
- Containment
- Prevention

## Report format
- Issue
- Impact
- Root Cause
- Action
- Risk
- Next step / owner

---

# 12. Incident Conversion Guidance

When user asks to “send code” or “convert issue”:
## Code 1
Row for-incidents/README.md
## Code 2
Path:
```text-incidents/YYYY/file-name.md
## Code 3
Detail markdown file with:

Issue
Timeline
Symptom
Root Cause
Failure Mechanism
Actions
Preventive
Current Status
Impact
Open Risk
Evidence

Mandatory rule for Code 1
The last column must always be:./2026/file-name.md And Code 1 / Code 2 must match 100% slug.
# 13. Open Items Still Not Closed

Mold 147 Press 2 root cause
Plasma 3 IT routing completion
Laser CB CT root cause per machine
WC37 pressure drop root cause
CPF Z-axis abnormality
TDIC #43 vacuum / dust filter abnormality
Hades auto-line PCB mark detect issue


# 14. Final Reminder
At BE line:

do not trust signal before physical confirmation
do not conclude machine broken before checking process / sensor / interface / human cause
always compare with related history before concluding or creating a new incident
