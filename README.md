# BE EQ Knowledge Base

## Cold Jet #22
- Output drop issue
- Root cause:
  - dry ice quality
  - nozzle freezing
  - CDA fluctuation

## Plasma 3 SFIS
- Data send: OK
- Routing: NOT DONE
- Not online

## Jigsaw
- Blade:
  - Machine 58: 700 panels
  - Others: 500 panels
- Brush: 108000 cycles

## Mold 147
- Press 2 abnormal
- Under monitoring
==================================================
[BE SYSTEM TRAINING – FOUNDATION]
==================================================

Flow chuẩn BE:
Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

Core rule:
- Không chẩn đoán cục bộ
- Luôn kiểm upstream + downstream
- Không default machine breakdown nếu chưa loại trừ process / interface

Failure nature:
- Phần lớn lỗi là:
  - process instability
  - detection gap
  - mechanical wear
  - system interaction
  - human operation

Failure chain:
Small issue → misalignment → drop → stacking → collision → defect

==================================================
[STATION KNOWLEDGE]
==================================================

[Water Clean]
- Core process ổn định
- Không phải trạm gây lỗi chính

Focus:
- Loader / unloader (đời cũ)
- Transfer interface
- Scanner robustness

Rule:
- Không đổ lỗi WC nếu chưa có evidence bề mặt / handshake

--------------------------------------------------

[CPF]
- Main risk: glue instability (KHÔNG phải collision)

Focus:
- glue overflow
- dot weight variation
- valve / chamber wear
- nozzle trial
- process margin

Rule:
- FAI pass ≠ process stable

--------------------------------------------------

[Molding]
- System đa module:
  - handling
  - transfer
  - press
  - vacuum
  - compound supply

Logic:
- transfer abnormal → check mold incomplete / foreign material
- vacuum abnormal → check mold side FIRST
- output NG but machine OK → check mold surface
- no input > 12h → must re-FAI

--------------------------------------------------

[Jigsaw]
- Blade:
  - Machine 58: ~700 panel
  - Others: ~500 panel

- Brush:
  - replace every 108000 cycles
  - function: remove debris

- Cleaning:
  - 100% RO fresh water
  - no recycle

- Calibration:
  - every 3 months

Risk:
- blade wear → crack / burr
- chuck wear → micro crack

--------------------------------------------------

[Water Clean Chemical Control]
- N600: replace every 2 weeks
- Filter: 1–2 weeks

--------------------------------------------------

[Process Flow Rule]
- LTE → must go CDIC
- GPS → skip CDIC → go sputter
- Over Q-time → must curing again before sputter

==================================================
[EQUIPMENT]
==================================================

AM100 (PnP):
- Model: NM-EJM4D
- Dimension: 1970 × 2105 × 1500 mm
- Weight: 2780 kg
- Power: 3-phase AC 200–480V, 2.0 kVA
- Air: 0.5–0.8 MPa, 200 L/min
- Speed: 35800 cph
- Accuracy: ±40 µm

CCM-A201 (Intelume Dry Ice):
- Fully automatic dry ice cleaning machine
- Clean residue after laser
- Dual nozzle
- Integrated:
  - dust collection
  - heating
  - hot air circulation
  - product clamping
- Risk: condensation / frost
- Facility: NOT AVAILABLE

Hans Laser (HDZ-GL4030):
- Spec not available
- Need installation manual

Laser system:
- CT instability (vision NG)
- cooling connector fragile

==================================================
[ISSUE DATABASE]
==================================================

[Cold Jet #22]
Symptom:
- kg drop below spec
- intermittent

Mechanism:
- unstable flow (pressure + temp + feed)
- partial freezing

Root cause:
1. dry ice quality variation
2. partial nozzle freezing
3. CDA fluctuation

Quick check:
- change dry ice
- purge system
- check air pressure real-time
- run ≥3 cycles

Impact:
- cleaning NG
- yield risk
- hard to detect

Action:
- purge before run
- clean nozzle
- log kg trend

--------------------------------------------------

[Mold 147 Press 2]
Symptom:
- abnormal during cleaning

Mechanism:
- pin drop / contamination

Risk:
- mold damage

Action:
- isolate
- fix pin
- monitor daily

==================================================
[AUTOMATION / SFIS]
==================================================

Plasma 3:
- data send → OK
- IT routing → NOT DONE
- not online

System:
- Baymax ↔ machine
- TCP/IP
- send product string

Risk:
- missing traceability
- integration incomplete

==================================================
[WATCH – CURRENT LINE]
==================================================

Key points:

- Cold Jet #22 unstable
- Laser CT unstable (vision NG)
- Plasma 3 not online (SFIS incomplete)
- Jigsaw wear control needed
- Mold 147 monitoring
- Dry run ongoing

Conclusion:
→ issue mainly process/system
→ NOT hardware failure

==================================================
[HANA PROJECT]
==================================================

Context:
- share line with Watch

Machine status:
- 대부분 machine already available
- Exception: Vacuum baking → need transfer

Lab equipment missing (~8 weeks):
- J-Link Pro
- I2C/SPI board
- Battery simulator
- Chamber

Risk:
- capacity conflict (share with Watch)
- readiness gap
- ramp delay

Readiness classification:
1. Machine available
2. Need transfer
3. Need new buy
4. Share → need capacity control

==================================================
[DRY RUN CONTROL]
==================================================

Schedule:
- 09:00–11:00 → Molding → AVI
- 13:00–14:00 → Plasma → CPF
- 15:00–16:30 → Laser flow

Control:
- record CT
- track issue time
- log input quantity
- manual fallback allowed

==================================================
[FAILURE PRIORITY LOGIC]
==================================================

Troubleshooting order:

1. Mold / mechanical
2. Transfer / positioning
3. Sensor / detection
4. Control / actuator
5. Process condition
6. Human factor
7. Automation / IT / integration (if auto line)

==================================================
[CI – IMPROVEMENT]
==================================================

- Cold Jet → purge + repeatability check
- Plasma → verify direction before install
- Laser → protect connector
- Vision → add FAI stability check
- SFIS → define connection checklist

==================================================
"Mold 147 Press 2 encountered an abnormal issue during mold cleaning while preparing for the Automation Hades FRB run, and the press has already been stopped from use pending root-cause investigation.
The current Jigsaw washing method uses 100% fresh RO water, with no recycling, and the used cleaning water is discharged directly after operation.
The Jigsaw cleaning brush is a plastic part used to remove saw debris, and its defined replacement interval is once every 108,000 running cycles."
"Laser station currently includes two machine platforms, HANS and E&R, using the same laser source type, with more than 30 machines in total.
The most critical EQ focus is the laser head and working table, while the most difficult technical task is laser optical path adjustment.
Laser requires periodic calibration (every 6 months or when running a new model), uses Spectra software at 102000 Hz, is connected directly to SFIS, and requires water cooling to protect the laser head."

"focuses on understanding the Laser Combine machine structure, buyoff logic, and the key FAI items including recipe, parameter, FAI dimension, trench shift, and trench inspection before restart. 
The afternoon task is to perform FAI and release the line after the Sunday stop, with special attention to laser power, vacuum, chiller condition, and LT Dry Ice nozzle/feed settings
A key learning target is that Laser release depends on alignment, scanner/CCD accuracy, repeatability, beam profile, Z window, and power decay, not only on recipe confirmation."

"Focused on Laser Combine and Dry Ice Clean, covering machine structure, buyoff logic, and the key FAI checks required before restart after the Sunday stop. For Laser, the critical release items include recipe, parameters, FAI dimension, trench shift, and trench inspection; for LT Dry Ice, the key checks are recipe, air pressure, dry ice feed rate, nozzle speed, and nozzle angle. 

A key learning point is that Laser release is not only a recipe check. The technical training material shows that machine readiness also depends on X-Y table precision, scanner/CCD positioning accuracy, repeatability, beam profile, Z-parameter window, and laser power decay, which are all part of the buyoff logic


This afternoon, the main task is to complete FAI and restart production using the current technical baseline: Laser power/vacuum/air/chiller condition and Dry Ice nozzle/feed condition, while confirming that all actual values are aligned with the product-specific FAI/MOI before releasing the line back to MP."

"Today’s training focused on the Cutting Dry Ice Clean manual flow, including program confirmation, gas condition, initialization, software operation (Running System / InteChip), and the main process parameters and maintenance/log pages used for troubleshooting.
Based on today’s line notes, the main follow-up items were mold-chase readiness before FR4 run, oven over-temperature protection setup, QR code / scanner compatibility at WC, Laser 222 cold-jet out-of-spec recovery with FAI OK, and Jig Saw read-code issue related to unclean DIC surface condition.
The key learning is that Cutting Dry Ice must be controlled as a full system including recipe, gas, dry ice supply, scanner/software, and module-to-module handling, not only the dry ice spray section.
Today’s follow-up covered multiple BE issues across Molding, Oven, Water Clean, Laser, Jig Saw, and the Hades automation line.
A key update is that the inline plasma machines for the Hades automation line have already arrived at USI and are currently under installation/layout, with one unit before Molding and one unit before CPF.
This is an important integration step because the new inline plasma setup will directly affect surface preparation before both molding and glue dispensing processes."

"-Cutting/Trench Dry Ice, focusing on startup flow, key process parameters, alarm handling, and how to use maintenance/log pages in the system for troubleshooting.
-On-line notes today highlighted several follow-up items, including Plasma 3 setup verification, Auto shuttle recovery, a bent dust collector hose in laser cutting, loose screw after sputter part reassembly, and FAI/check sheet confirmation for DL2.
-A key learning point for Trench Dry Ice is that Cold Jet pressure is not allowed to be adjusted freely, and troubleshooting must follow machine spec, alarm list logic, vacuum/dust collector condition, and magazine/SFIS interface control.
-The reverse-loading/unloading unit of the plasma2 machine(Automation line) has been disassembled and is awaiting repair by the supplier to ensure it conforms to the correct production line layout."

"- Plasma 2 setup was completed today, Laser 153 completed the scheduled 6-month PM with no special issue found, and Dry Ice 22 mask replacement was verified OK with the related check sheet completed.
- Line verification today showed that molding passed FAI, and Inline Plasma 2 completed auto-line dry run successfully; however, the current status note indicates that only carrier-level running is OK and full magazine running is still pending.
- Additional follow-up items today include WC79 scanner connection abnormality, Saw 58 handling issue at the output side, and Laser CB cycle-time comparison showing about 190 s on auto line #230 versus 160 s on manual line, with a note that occasional vision NG / cannot-detect condition may be contributing."

"- Mold 146 had a pin-drop issue, with risk of the pin falling onto the mold chase surface and causing mold damage. The pin was re-fixed with glue, and daily monitoring is currently in place.
- CPF showed a Z-axis abnormality, while Laser 230 completed scheduled quarterly maintenance with actual cycle time around 11–15 seconds.
- Additional follow-up items today include Laser CB on the Hades auto line not detecting PCB mark, TDIC #43 vacuum/dust filter issue, and Plasma 3 QR scanner optimization."

"Press 3 mold maintenance was completed today with no abnormal issue found during the maintenance activity.


The main learning at Molding is that process readiness depends heavily on mold cleaning and mold surface smoothing/conditioning before FAI, not only on machine status. The mold maintenance SOP also emphasizes correct cleaning method, seal/O-ring check, vacuum path cleaning, and surface confirmation after maintenance.


Molding FAI is taken from the buyoff package, including clamp balance, cavity vacuum, mold temperature, cosmetic, thickness, warpage, shift, and chamfer checks. A key risk is that if the mold smoothing step is skipped, mold surface crack may occur and cannot be easily detected by naked eye, even though other checks may still look normal at first."

"Continued molding training under MP condition on machine 146 (small mold, 3 presses) and machine 158 (big mold, press 2 & 3), with focus on comparing press-to-press consistency in actual transfer, vacuum, clamp force, and temperature rather than only checking recipe setting.
Reviewed actual molding process data and confirmed that transfer pressure, cavity vacuum, and mold temperature were generally within the current molding FAI/release window; the key learning is that molding stability should be judged by both actual curve behavior and press-to-press variation, not only by static target values. 
Learned that molding readiness is strongly dependent on mold maintenance quality, especially mold cleaning and smoothing before FAI,FAI must be repeated before restarting production (for example, Monday morning after Sunday shutdown, 7 working days need maintenance mold 1 time)."

"Distinguish which MOI parameters are allowed to be adjusted, which are recipe/EAP control parameters, or EQ/engineering only parameters, to avoid incorrect adjustments that could disrupt the process.

After adjustments, don't just look at the setpoint; verify the actual value, process curve, FAI/visual, and downstream condition.
Understand the parameters that significantly affect molding quality, including: mold temperature, cavity/board vacuum, clamp force, transfer setting/profile, and cure time.
Understand why the same recipe can result in different actual values ​​between presses due to vacuum branch, mold condition, cleaning state, and sensor/hardware path.
Gain a better understanding of alarm maximum mold idle time/mold cleaning timer and the vacuum hardware structure for each press to better support troubleshooting."

"Reviewed actual molding conditions on machine 146/158 and learned to compare press-to-press consistency, not only recipe or target settings.
From the actual screens, transfer pressure and cavity vacuum remained within the current molding release window, while clamp force and temperature still showed small differences between presses that should be monitored.
The key learning is that molding stability must be judged by actual press behavior, especially transfer pressure, cavity vacuum, clamp force, and zone temperature, rather than by nominal parameter setting only.
Press 3 of molding machine 146 repeatedly failed to push the panel out to the cooling tray this afternoon, and the issue temporarily recovered after manual removal and brushing/cleaning.
Current suspicion is mold release/output contamination or a local release path issue on Press 3, since the problem repeats frequently and is not seen as a full machine breakdown."

"Today’s molding training focused on alarm-based troubleshooting, model-change verification, and production monitoring under MP condition, with emphasis on mold-side logic rather than only machine alarm text.
Key learning confirmed that transfer pressure/time deviation should first suspect mold incomplete/foreign material, vacuum abnormality should first suspect mold side, and model change release must verify mold chase, PR set, and recipe.
During production, machine 146 press 3 had a cavity vacuum abnormality and was isolated after O-ring replacement for night-shift re-FAI, while machine 158 press 3 showed a clamp-force abnormality and required parameter adjustment by ME and EQ."

"Molding release is controlled by the FAI package, which includes recipe confirmation, clamp balance, cavity vacuum, mold temperature, cosmetic, thickness, warpage, shift, and chamfer checks before production release.
The main molding process controls defined in the technical sheets are moldchase temperature 175 ± 5°C, cavity vacuum ≤ 30 hPa, clamp force, cure time, transfer pressure, and transfer time, and these parameters are used as the core release window for process verification.
The technical maintenance and alarm documents show that molding stability also depends on proper mold cleaning/maintenance, seal and vacuum path condition, and correct response to vacuum/transfer/pellet-related alarms, with abnormal mold-side conditions requiring EQ attention."

"Have 3 machine TTL, 2 IDLE 1 running.
Water clean no issue, foucus on N600 & parameter.
CPF no issue found, take care about load/unload, 12hour need change/replace new nozzle."

"Maintenance oven #472 after water clean machine. Plasma #78 machine wait free time cause conflict plan production - Hades MBO.
Oven Machine use CDA + N2. It is observed that CDA and N₂ gas lines use similar tubing and are located very close to each other, with limited visual differentiation. This creates a risk of misconnection during maintenance or setup. Since there is no detection mechanism, such errors may not trigger alarms but can significantly impact drying quality. It is recommended to implement clear color coding and physical differentiation to prevent human error.
Have air leake from connector inside machine, already open & fixed."

"1- Water Clean KED #37 normal running, SMT1 lane 1, SMT2 lane 2, No special issue.
2- During CPF maintenance, a deviation in pressure reading was found on machine #92(80) compared to others(85). Root cause was identified as gauge inconsistency rather than process issue. After swapping gauges, the system returned to normal. This highlights a risk in measurement reliability rather than equipment performance."

"CPF:  - Training for PD when replace new glue tube (HL issue CPF#78 Glue over flow)
- During production, warped panels were found to fail vacuum pressure requirements although the machine meets FAI conditions. Root cause is insufficient sealing due to panel warpage, not equipment performance. This indicates a gap between FAI condition and real production variation.
Oven control by OTMS - OK.
Plasma process critical for CPF performance, especially surface cleaning before filling.
Main issue:
- Chamber pressure < 0.2 caused by gasket misalignment or aging.
System gap:
- No inline verification of plasma effectiveness.
- Gas configuration not fully aligned with design.
Risk:
- Plasma NG leads to poor adhesion and CPF quality defect.
Action:
- Strengthen gasket inspection and replacement control
- Monitor pressure trend and leak condition
- Implement water contact angle as validation method"

"Maintenace W/C #38 - normal.
Top issue Water Clean:
- Flow imbalance
- Temp not reaching SV
- Conveyor misalignment
- Chemical drift
W/C #37 run for backup normal but have risk:
Finding:
- Input conveyor belt worn-out
- Misalignment between conveyor and WC belt
- Carrier stuck at interface zone
Action:
- Mechanical alignment adjustment (height + centerline)
- Fine tune transfer position from loader to WC
- Plan for belt replacement"

"🔴 1. Surface condition is multi-stage controlled (NOT only WC)
CPF bonding is affected by multiple preparation steps:
→ Water Clean → Plasma (before molding) → Plasma (before CPF)
Any instability in these stages
→ impacts final glue adhesion on molding surface
🟠 2. Process stability > spec compliance
FAI OK ≠ Stable production  
CPF nozzle(New buy) near spec (0.022–0.023)
+ WC process drift (temp / flow)
→ increases risk of sudden NG (bonding / void / weak adhesion)
🔵 3. Hidden risk: system NG without alarm
Surface-related issues often have NO alarm
Machine reads OK (WC / Plasma / CPF)
→ but real surface condition unstable
→ defect only appears downstream
🎯 Key Message
Control focus must be on surface stability across WC + Plasma + CPF,
not only machine performance at individual station"
"Date: 2026-06-03
Machine: Oven #472
Station: Water Clean
Issue: CDA và N2 dùng chung màu ống, đầu nối gần nhau khó phân biệt
R/C: Poor visual control (design issue)
Type: Design / Human error risk
Action: Đề xuất color coding + phân biệt vật lý đường khí
Risk: High
Remark/Report: Có nguy cơ nối nhầm khí, không có detection → ảnh hưởng chất lượng drying"
"Date: 2026-06-03
Machine: Oven #472
Station: Water Clean
Issue: Air leak tại connector trong máy
R/C: Loose connector
Type: Equipment / Mechanical
Action: Đã mở máy và fixing
Risk: Medium
Remark/Report: Đã xử lý xong, không ảnh hưởng tiếp"
"Date: 2026-06-03
Machine: KED #37
Station: Water Clean
Issue: No issue (normal running)
R/C: NA
Type: Status
Action: Continue monitoring
Risk: Low
Remark/Report: SMT1 lane trái, SMT2 lane phải, running ổn định"
"Date: 2026-06-03
Machine: CPF #92
Station: CPFilling
Issue: Sai lệch giá trị áp suất (80 vs 85 machine khác)
R/C: Gauge inconsistency (measurement error)
Type: Measurement system
Action: Swap gauge giữa máy → OK
Risk: High
Remark/Report: Không phải process issue, là lỗi đo lường → risk sai điều chỉnh parameter"
"Date: 2026-06-03
Machine: EQCPF00078
Station: CPFilling
Issue: Glue overflow (1 panel)
R/C: Chamber của valve bị wear → tube slip off
Type: Mechanical wear (end-of-life)
Action:
- Replace chamber valve #25
- Check toàn bộ valve → valve #09 cũng wear → replace
Risk: High
Remark/Report: Silent failure, không có alarm → cần chuyển sang preventive maintenance"
"Date: 2026-06-04
Machine: CPFilling (multiple machine)
Station: CPFilling
Issue: Panel cong (warpage) → không đạt áp suất vacuum theo FAI
R/C: Panel warpage gây hở gap giữa panel và vacuum table
Type: Process / Product + Mechanical interaction
Action: 
- Tăng cường kiểm tra flatness panel trước CPF
- Monitor vacuum pressure khi chạy thực tế
- Đánh giá lại vacuum design/fixture nếu cần
Risk: High
Remark/Report: Panel cong làm giảm sealing → vacuum không đủ → ảnh hưởng độ chính xác dispense và chất lượng sản phẩm"
"Machine: Plasma #78
Issue: HMI touch screen NG (cannot operate normally)
R/C: Hardware degradation / HMI failure
Type: Electrical / Interface
Risk: MEDIUM
Action:
- Replace touch screen
- Verify control interface after replacement"
"Machine: Plasma #78
Issue: Pressure measurement replaced previously
R/C: Old sensor instability / drift
Type: Measurement system
Risk: MEDIUM
Action:
- Calibrate new pressure sensor
- Verify reading consistency across machines
Insight:
- Pressure data reliability critical for plasma quality"
"Machine: Plasma
Issue: System designed for Ar / O2 / H2 but actual using ArH2 single line
R/C: Configuration simplification vs original design
Type: Process / Gas system
Risk: MEDIUM
Action:
- Verify gas composition stability
- Align process spec vs actual gas usage"
"Machine: Plasma + Measurement
Issue: Need verify plasma effectiveness
Method: Water contact angle measurement
R/C: Plasma surface energy change
Type: Process verification
Risk: HIGH (if not controlled)
Action:
- Measure contact angle after plasma
- Set acceptance threshold"
"Machine: Plasma
Issue: Chamber pressure < 0.2
R/C: 
- Lid gasket misalignment
- Gasket aging / wear
Type: Mechanical sealing failure
Risk: HIGH
Action:
- Check gasket alignment
- Replace gasket periodically
- Add vacuum leak inspection"
"Process: Plasma → CPF
Function:
- Clean laser trench
- Improve surface condition before glue filling
Risk if NG:
- Poor adhesion
- CPF defect (void / overflow / bonding issue)"
"Date: 2026-06-04
Machine: Oven
Station: Baking
Issue: Mở nhầm cửa lò trên/dưới
R/C: Nhầm thao tác do thiếu phân biệt
Type: Human error
Action: Label + training
Risk: Medium
Remark/Report: Có thể gây drop nhiệt độ"
"Date: 2026-06-04
Machine: Press #146
Station: Molding
Issue: Cavity vacuum before transfer error
R/C: Mold chase sealing issue (O-ring/gasket)
Type: Mechanical / Vacuum
Action: Replace O-ring + bảo dưỡng lại mold
Risk: High
Remark/Report: Đã isolate bằng swap mold chase
"
"Date: 2026-06-05
Station: Water Clean
Machine: WC #37 / #38
Issue:
Weekly PM for Water Clean system while machine #38 under maintenance, machine #37 used as backup.
Finding:
- Temperature PV lower than SV (cleaning & drying zones not reaching setpoint)
- Flow imbalance between upper (~0.4 MPa) and lower (~0.2 MPa)
Action:
- Perform full PM (tank, filter, nozzle)
- Verify pressure, temperature, chemical condition
- Monitor PV vs SV and flow distribution
Risk:
Cleaning effectiveness reduction → downstream Plasma / CPF impact"
"Date: 2026-06-01
Station: Water Clean Input
Machine: WC #37

Issue:
Carrier dragging/jamming at transfer point between loader conveyor and Water Clean metal belt.
Finding:
- Input conveyor belt worn-out
- Misalignment between conveyor and WC belt
- Carrier stuck at interface zone
Action:
- Mechanical alignment adjustment (height + centerline)
- Fine tune transfer position from loader to WC
- Plan for belt replacement
Risk:
Carrier jam → downtime / carrier damage / uneven cleaning → Plasma & CPF impact"
"Station: Molding
Machine: Press (single running)

Issue:
High WIP at molding due to production shortened working hour (stop at 5h)

Finding:
- Only 1 machine running
- PD stops early (cost-down, no overtime)
- Output cannot meet required production capacity

Action:
- Inform production planning (PD)
- Evaluate need to increase machine quantity or adjust working schedule

Risk:
WIP accumulation → downstream starvation (Laser / CPF / Sputter)  
→ line imbalance → target output miss"
"ISSUE:
High WIP at Molding due to reduced working hour (stop at 5h)

ROOT CAUSE:
- Only 1 molding machine running
- PD cuts overtime (cost reduction)

SYMPTOM:
- Output lower than required
- WIP accumulation at molding
- Downstream stations not supplied properly

ACTION:
1. Review production schedule with PD
2. Evaluate additional machine / extended run time
3. Balance capacity vs demand

RISK:
- Cannot meet production target
- Line imbalance (upstream vs downstream)
- Potential delay for Laser / CPF / Sputter

SYSTEM NOTE:
This is NOT equipment failure  
→ It is capacity / planning issue affecting whole line"
"Station: CPF (Glue filling)
Machine: CPF (multiple)

Issue:
New nozzle design validated OK but running near lower spec limit (0.022–0.023)

Condition:
- Design approved (FAI OK)
- Actual production values close to lower tolerance limit

Type:
Process + Design margin issue

Risk level:
HIGH (borderline performance)"
"LASER – OPERATION CONTROL NOTICE (#151)

ISSUE:
Machine operated under ENG mode during production (21:58 → 01:28)

ROOT CAUSE:
ENG account used to check normal 2D code alarm at loader
but not logged out after handling

SYMPTOM:
- ENG mode active during production
- Normal alarm handled by ENG instead of OP

ACTION:
1. Switch back to OP mode after IPQC audit
2. Restrict ENG account access (Engineer only)
3. Change ENG passwords regularly
4. Remind PD to handle normal alarm with OP account

RISK:
- Loss of traceability
- Potential misuse of engineering privileges
- Process control violation

SYSTEM NOTE:
Production operation must always use OP account  
ENG mode only for troubleshooting"
"LASER CUTTING – SHIFT ISSUE NOTICE (#152)

ISSUE:
Laser cutting position shifted (X,Y) causing NG panels (4 pcs scrap)

ROOT CAUSE:
Panel warpage → impact vacuum stability → fiducial mark shift (322um > spec 250um)

SYMPTOM:
- Cutting position offset
- X,Y shift exceed tolerance
- Occurs intermittently

ACTION:
1. Lock panels and perform 100% inspection at AVI
2. Reduce X,Y shift limit from 500um → 250um
3. Apply stricter limit (300um) on other machines

RISK:
- Cutting misalignment → scrap
- Hidden shift on marginal panels
- Downstream defect

SYSTEM NOTE:
Laser is not root cause  
→ upstream panel condition (warpage) drives position shift"
"DRY ICE CLEAN – OPERATION & SYSTEM CONTROL NOTICE (#27 & 28)

ISSUE:
- Mapping reply timeout
- Sips broken during operation

ROOT CAUSE:
1. System path mismatch between machine and PD computer
2. No X-out trial run after model/changeover
3. Carrier misplacement → mask collision → Sips broken

SYMPTOM:
- Mapping timeout alarm
- Carrier position not correct
- Physical damage (Sips broken)

ACTION:
1. Correct SFIS path and ensure system matching
2. Mandatory X-out trial run after any setup/change
3. Recheck carrier position before operation
4. Verify mask alignment before closing

RISK:
- Machine stop (mapping error)
- Product damage (Sips broken)
- Downtime + yield loss

SYSTEM NOTE:
System configuration + operation validation must go together  
Change without validation = high risk"
LASER CUTTING – BURR ISSUE NOTICE (#150) ISSUE: Burr found at sidewall → SIP not fit jig test (10 pcs NG) ROOT CAUSE: Laser power operating near lower limit (33.59W vs spec 33.5–34.5W) → Cutting energy insufficient → incomplete material removal SYMPTOM: - Sidewall burr observed - Jig test fail - Intermittent NG ACTION: 1. Monitor laser power continuously 2. Ensure power operates in center spec range 3. Request vendor support for machine verification 4. Review power stability trend RISK: - Cutting defect → assembly fail - Hidden burr may pass visual but fail downstream - Yield loss SYSTEM NOTE: Running near spec limit is unstable → must operate at center process window
CPF – BARCODE SCANNER FAILURE NOTICE (#99) ISSUE: Barcode scanner working but panel not recognized in SFIS system ROOT CAUSE: PC communication/configuration issue (COM port / software setup) SYMPTOM: - Scanner light active (green) - Barcode detected physically - SFIS does not receive panel information ACTION: 1. Check cable and COM connection 2. Verify scanner signal → OK 3. Reconfigure scanner software (IsCom2Key / mapping) 4. Replace PC and re-setup scanner 5. Re-teach barcode using Datalogic software RESULT: - Barcode successfully scanned to SFIS - Production running normally RISK: - Lost traceability - Production stop due to no data input - Manual bypass risk SYSTEM NOTE: Scanner hardware OK ≠ system OK PC and software communication is critical
FACTORY – POWER OUTAGE IMPACT NOTICE (01/01) ISSUE: Multiple machines abnormal after factory power outage ROOT CAUSE: Power interruption caused: - Long alarm duration - Equipment damage (Dry Pump, Screen) - System instability during restart SYMPTOM: - Machines not able to recover immediately - Long alarm duration recorded - Some machines cannot restart (SPT#50) - Physical damage on components ACTION: 1. Restart all machines after power recovery 2. Replace damaged parts (DP, screen) 3. Recheck system status via SMD system 4. Prepare repair plan for NG spare parts RISK: - Production delay - Equipment damage - High downtime - Hidden instability after restart SYSTEM NOTE: Power interruption must be followed by full system verification, not only machine restart
MOLDING – HEATING POWER ISSUE NOTICE ISSUE: Temperature alarm due to heating plate power cord damage ROOT CAUSE: Power cable damaged → loss of 220V supply to heater SYMPTOM: - Temperature error alarm - Heater not working properly - Machine stop ACTION: 1. Reconnect damaged cable (temporary fix) 2. Replace new power cord 3. Re-route cable and secure with tie/insulation RISK: - Heating instability → molding NG - Machine stop / downtime - Electrical safety risk (short circuit / burn) SYSTEM NOTE: Cable wear is a slow degradation failure → no alarm until failure occurs
AOI LOADER – CARRIER STACKING ISSUE ISSUE: 2 carriers stacked on top of each other at loader → panel broken ROOT CAUSE: Panel deviation from carrier → Sensor X16 cannot detect panel properly → Loader moves to next position while previous carrier still present SYMPTOM: - Sensor fails to detect panel - Loader continues movement - Two carriers overlap - Panel damage occurs ACTION: 1. Adjust X16 sensor position 2. Adjust conveyor width to stabilize carrier 3. Check sensor detection for panel vs carrier surface 4. Apply same adjustment to all AOI loaders RISK: - Panel damage (break) - Carrier stacking / jam - Production stop SYSTEM NOTE: Sensor detection must consider real panel condition (deviation) Not only ideal position
DRY ICE CLEAN – PRESSURE UNSTABLE ISSUE (#038) ISSUE: Dry ice pressure unstable → panel not cleaned properly (FAI NG) ROOT CAUSE: Cutter module bearing dirty and stuck → cutter rotation unstable → dry ice output fluctuating SYMPTOM: - Dry ice pressure over/unstable - Cleaning not effective - FAI NG ACTION: 1. Replace cutter module 2. Clean and lubricate bearing 3. Switch to another cold jet for fast recovery 4. Implement periodic maintenance for cutter system RISK: - Poor cleaning → downstream Plasma / CPF defect - Process instability without clear alarm - Output variation SYSTEM NOTE: Stable mechanical rotation is critical for dry ice consistency Mechanical instability → process variation
DRY ICE CLEAN – LANE A POWER LOSS NOTICE (#038) ISSUE: Lane A loss power → machine cannot home ROOT CAUSE: Loose / improper signal wiring → 24V power supply lost SYMPTOM: - Machine cannot home - Power reading abnormal (0V → 24V after fix) - Lane A not functioning ACTION: 1. Check 24V power supply 2. Reconnect signal wiring 3. Re-layout cable routing to avoid loose connection 4. Verify stability after repair RESULT: - Power restored - Machine running normal - FAI OK RISK: - Machine stop - Process interruption - Potential repeated failure if wiring not secured SYSTEM NOTE: Unstable wiring → intermittent power loss → causing unpredictable machine behavior
DRY ICE CLEAN – 2D READER UNSTABLE NOTICE (#038) ISSUE: Lane A 2D reader unstable, intermittent barcode reading failure ROOT CAUSE: Improper reader position and insufficient fine-tuning → 2D image blurred → unstable recognition SYMPTOM: - Intermittent read fail alarms - Scanner sometimes reads, sometimes fails - No issue found in FAI or material ACTION: 1. Clean scanner lens 2. Re-adjust reader position 3. Fine-tune focus and angle 4. Verify reading stability after adjustment RESULT: - Reading performance improved - Machine running normal RISK: - Lost traceability - Production interruption - Intermittent failure difficult to detect SYSTEM NOTE: Scanner failure is often due to setup quality, not hardware issue
JIGSAW – PCB SCRATCH ISSUE (#073) ISSUE: Scratches found on PCB surface (focus on side E&D) ROOT CAUSE: Water cutting nozzle (Z1) touching panel during machine movement → improper nozzle position / clearance SYMPTOM: - Scratch mark along cutting path - Issue concentrated on blade 1 - No alarm in machine or log ACTION: 1. Re-adjust water cutting nozzle position 2. Verify clearance between nozzle and panel during movement 3. Run test with bare panel 4. Create SOP for nozzle adjustment RISK: - Cosmetic defect (visible scratch) - Potential functional damage - Yield loss (137 pcs impacted) SYSTEM NOTE: Mechanical interference often occurs without alarm → must check physical clearance, not only system parameters
SPUTTER – COPPER EXPOSURE ISSUE (#58) ISSUE: Copper exposure detected after sputtering process (66 pcs NG at M9 chamber) ROOT CAUSE: DC7 power instability during manual test at chamber M8 → affects nearby chamber M9 due to proximity → causing abnormal sputtering / Cu exposure SYMPTOM: - DC7 power alarm triggered - Product abnormal after plating - No issue during FAI, but defect occurs later ACTION: 1. Check DC power stability before operation 2. Avoid performing manual test near active production chamber 3. Isolate testing area from production area 4. Ensure stable cathode condition before run RISK: - Film defect (copper exposure) - Hidden defect (not detected immediately) - Cross-chamber interference SYSTEM NOTE: Sputter process is extremely sensitive to power stability Nearby activity can affect adjacent chamber performance
CUTTING DRY ICE – ASSEMBLY ERROR NOTICE (#40) ISSUE: Mask cover installed in wrong direction (upside down) → abnormal product after sputter ROOT CAUSE: Incorrect installation during model change (Hades → Attis) → no verification after assembly SYMPTOM: - Product abnormal after downstream process - No machine alarm - Large quantity impacted (~7K pcs) ACTION: 1. Reinstall mask cover in correct orientation 2. Double-check by ME after installation 3. PD redo FAI before production 4. Create SOP for cover installation RISK: - Large quantity NG (mass impact) - Hidden defect not detected in machine - Process escape from setup stage SYSTEM NOTE: Assembly error at changeover can affect entire production batch → verification must be mandatory
MOLDING – PANEL STICK / INCOMPLETE ISSUE ISSUE: Panel stuck on cavity → incomplete molding (1 panel / 24 sips) ROOT CAUSE: Uneven cavity surface condition → left side and different positions show different performance → local compound sticking SYMPTOM: - Transfer pressure rises earlier than normal - Panel sticking at cavity (not consistent) - Issue not detected in FAI or material check ACTION: 1. Check and verify cavity surface condition 2. Ensure cleaning / surface uniformity 3. Monitor transfer pressure profile 4. Retrain maintenance and inspection procedure RISK: - Incomplete molding - Local defect (non-uniform behavior) - Hidden process instability SYSTEM NOTE: Cavity condition must be uniform across all positions Local difference → unpredictable defect
CUTTING DRY ICE – SIP CRACK ISSUE (ATTIS) ISSUE: SIP crack due to carrier misalignment and impact during loading ROOT CAUSE: Clamp arm imbalance → carrier not stable when placed on pedestal → SIPs shift out of carrier → impact with PIN table SYMPTOM: - SIP shift out from carrier - Carrier impact during placement - Intermittent alarm (vacuum / guide error) - Physical damage (crack / scrap) ACTION: 1. Re-balance clamp arm 2. Regrind clamping head to improve alignment 3. Double-check balance during pick/place 4. Monitor carrier stability during loading RISK: - SIP crack / scrap - Intermittent defect difficult to detect - Potential repeat failure if clamp not stable SYSTEM NOTE: Clamp stability directly affects product positioning Imbalance → dynamic misalignment → physical damage
CUTTING DRY ICE – SIP DROP ISSUE (#28) ISSUE: SIP dropped on pedestal → next carrier caused double SIP stacking ROOT CAUSE: Transfer clamp misalignment → carrier not placed flat on pedestal → SIP dropped during unloading SYMPTOM: - SIP falls on pedestal - Next carrier causes double SIP - No abnormal found in machine parameter / FAI ACTION: 1. Re-teach transfer position 2. Adjust positioning pin dimension 3. Ensure carrier placed flat on pedestal 4. Verify transfer alignment stability RISK: - SIP drop / stacking - Potential mis-processing or damage - Intermittent issue difficult to detect SYSTEM NOTE: Transfer positioning stability is critical to avoid cumulative failure
CUTTING DRY ICE – SIP BROKEN ISSUE (#28) ISSUE: SIP broken during operation (8 pcs scrap) ROOT CAUSE: Clamp arm misalignment → carrier not correctly aligned with positioning pin → SIP drops out from carrier → mask closing causes direct impact with SIP SYMPTOM: - SIP broken inside machine - No abnormal in parameter / air pressure / recipe - Alarm related to cover close detected ACTION: 1. Adjust and re-align clamp arm 2. Verify carrier positioning with pin hole 3. Perform X-out trial run after repair 4. Double-check alignment before production RISK: - Direct product damage (breakage) - Repeat failure if alignment not stable - Intermittent issue difficult to detect SYSTEM NOTE: Misalignment in handling system can lead to both drop and collision failure
AUTO PRESS – SIP STACKING ISSUE ISSUE: SIPs stacked on top of each other (~126 pcs impacted) ROOT CAUSE: Incorrect operator handling during machine alarm → carrier status not properly verified → SIP already present but next process still executed SYMPTOM: - Double SIP in same position - No abnormal in machine settings / FAI - Alarm present but not handled correctly ACTION: 1. Retrain operator on alarm handling procedure 2. Verify carrier status before restart 3. Follow correct alarm handling SOP 4. Perform trial run after reset RISK: - SIP stacking → potential damage or process NG - Hidden issue due to incorrect recovery action - High production impact SYSTEM NOTE: Operator action after alarm is critical Wrong decision → system continues in abnormal condition
LASER – CARRIER DROP ISSUE (#227) ISSUE: Carrier drop and SIP broken due to incomplete transfer out of laser table ROOT CAUSE: Laser out sensor installed too far from table edge → panel passes sensor but not fully out of table Operator switches to manual mode and stops conveyor → laser table continues moving → collision occurs SYMPTOM: - Panel jam at ULD - Laser alarm (PLC151.02) - Panel not fully out but system detects OK - Carrier drop and SIP break ACTION: 1. Adjust laser out sensor closer to edge of table 2. Ensure panel fully exits before next movement 3. Retrain operator on correct recovery procedure 4. Do not switch mode during transfer phase RISK: - Carrier drop → SIP broken - Collision inside machine - Repeat failure during abnormal recovery SYSTEM NOTE: Sensor detection must represent real physical position False OK signal = high risk condition
OVEN – ALARM SWITCH MISOPERATION NOTICE (#471) ISSUE: Alarm switch turned OFF → system no alarm during operation ROOT CAUSE: Operator turned off alarm switch during operation (door open alarm) → forgot to turn back ON before restarting machine SYMPTOM: - No alarm during operation period - Alarm system disabled unknowingly - Only detected by EQ check ACTION: 1. Retrain operator on alarm switch usage 2. Add pre-run checklist (alarm status verify) 3. Improve alarm logic (auto reset / delay mute) 4. Require EQ confirmation before production RISK: - Loss of safety protection - Hidden abnormal condition not detected - Potential quality risk SYSTEM NOTE: Disabling alarm system = removing safety layer Human control must NOT override critical safety function
DRY ICE – SMD FALSE ERROR NOTICE (#23) ISSUE: SMD system shows machine error status while machine is running normally ROOT CAUSE: Mismatch between actual machine status and SMD system feedback → incorrect signal mapping / logic causing false alarm SYMPTOM: - SMD shows alarm status - Machine status indicator = normal (green) - No real machine error - False alarm persists over time ACTION: 1. Verify machine actual condition vs SMD status 2. Recheck signal connection and mapping 3. Validate SMD parameter setting 4. Coordinate with SMD team for correction RISK: - False alarm reduces system reliability - Real issues may be ignored (alarm fatigue) - Misleading production monitoring SYSTEM NOTE: False alarm is more dangerous than no alarm → reduces trust in monitoring system
LASER – SPUTTER PEELING ISSUE (#177) ISSUE: Corner sputter peeling off observed (14 SIP affected) ROOT CAUSE: No abnormal found in machine / process / material All checks: - Laser power stable (32.65W within spec) - Vacuum / alignment / focus OK - Surface clean, no contamination - Maintenance OK STATUS: Root cause not yet identified ACTION: 1. Continue investigation with cross-team (ME / process) 2. Collect more data (trend / pattern) 3. Check upstream surface condition (cleaning / plasma) 4. Monitor for repeat occurrence RISK: - Adhesion failure (functional reliability) - Latent defect - Potential repeat without clear warning SYSTEM NOTE: If all machine and process parameters are OK → issue likely from interface condition or upstream process
WATER CLEAN – OVER TEMPERATURE ISSUE (#38) ISSUE: Rinse tank temperature increased to abnormal level (~100°C) ROOT CAUSE: Solid State Relay (SSR) failed in ON condition → heater cannot turn off after reaching setpoint SYMPTOM: - Temperature continues rising above setpoint (50°C) - No abnormal in sensor or PLC signal - Heater still active despite PV ≥ SV ACTION: 1. Turn off main power immediately for safety 2. Replace defective SSR 3. Reconnect and verify wiring 4. Check heater control behavior (ON below SP / OFF at SP) RISK: - Overheating → chemical damage / process NG - Safety risk (burn / equipment damage) - Production stop SYSTEM NOTE: Control loop failure can override normal system logic Component-level fault → system-level hazard
DRY ICE CLEAN – LIFT TABLE LIMIT SENSOR ISSUE (#026) ISSUE: Lift table limit sensor NG → unstable signal and machine alarm ROOT CAUSE: 1. Limit sensor internal break → signal unstable 2. Scanner lane A loose due to high air pressure → intermittent code reading SYMPTOM: - Machine alarm on limit sensor - Unstable lift table signal - Intermittent barcode reading error - Machine behavior not consistent ACTION: 1. Replace defective limit sensor 2. Fix scanner mounting and alignment 3. Optimize air pressure to reduce vibration 4. Perform FAI and verify machine stability RISK: - Machine stop / unstable operation - Wrong position detection - Downstream process error (misplacement / wrong reading) SYSTEM NOTE: Sensor + mounting stability are critical for reliable detection Loose installation → intermittent failure
	Machine	Issue	Root Cause	Action	Type	Risk
WC38 – Rinse tank over temperature	Water Clean EQDIW00038	Over temp ~100C	SSR stuck ON	Replace SSR; verify heater loop	Electrical/Control	High
Laser #227 – Carrier drop	Laser EQLAS00227	Carrier drop	Sensor too far + wrong recovery	Adjust sensor; retrain OP	Sensor/Human	High
Auto Press – SIP stacking	Auto Press	Double SIP	Wrong alarm handling	Retrain OP; SOP	Human	High
DIC#028 – SIP broken	Dry Ice EQDIC00028	SIP broken	Clamp misalignment	Adjust clamp	Mechanical	High
DIC#040 – SIP dirty	Dry Ice EQDIC00040	Dirty SIP	Process unstable + OP error	Improve SOP	Process/Human	High
AOI Loader – stacking	AOI Loader	Carrier stacking	Sensor miss detect	Adjust sensor	Sensor	High
Laser #150 – Burr	Laser EQLAS00150	Sidewall burr	Low power margin	Adjust power	Process	Medium
CPF – Scanner NG	CPF EQCPF00099	Barcode NG	PC config	Reconfig PC	IT	Medium
Oven – Alarm OFF	Oven EQOVN00471	Alarm disabled	OP forgot	Training	Human	Medium
DIC#026 – Sensor NG	Dry Ice EQDIC00026	Limit sensor NG	Sensor break + loose	Replace	Sensor	High
Dry Ice #038 – Pressure	Dry Ice EQDIC00038	Pressure unstable	Bearing stuck	Replace module	Mechanical	High
DIC#038 – Power loss	Dry Ice EQDIC00038	24V loss	Loose wiring	Fix wiring	Electrical	High
DIC#038 – Reader unstable	Dry Ice EQDIC00038	Read NG	Position not tuned	Adjust focus	Sensor	Medium
Power outage	Multi	Machine stop	Utility failure	Restart check	Utility	High
Molding – Heater cable	Molding EQMLD00157	Temp alarm	Cable damage	Replace cable	Electrical	High
AOI Loader – stacking 2	AOI Loader	Panel break	Sensor setup	Adjust position	Sensor	High
Laser #177 – peeling	Laser EQLAS00177	Peeling	Unknown interface	Investigate upstream	Process/Unknown	High
DryIce23 – false alarm	Dry Ice EQDIC00023	False alarm	Signal mismatch	Check mapping	IT	Medium
DIC#028 – SIP drop	Dry Ice EQDIC00028	SIP drop	Clamp misalign	Re-teach	Mechanical	Medium
DIC#040 – SIP crack	Dry Ice EQDIC00040	SIP crack	Clamp imbalance	Rebalance	Mechanical	High


END
==================================================
