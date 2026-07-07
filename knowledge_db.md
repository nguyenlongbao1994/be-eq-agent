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
Water Clean → Baking → Plasma → Molding → Laser → Trend Dry Ice → Plasma → CPF → Curing → Jigsaw/Lasercut → cutting Dry Ice → Tape → Sputter → AVI

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

### Machine family
Trạm Water Clean hiện sử dụng **2 loại máy chính**:
- **TZ-8500 Flip-chip de-flux cleaner**
- **AC-7000 online PCBA Cleaning Machine**

=> Khi support / viết incident / review issue, phải xác nhận rõ machine family là **TZ-8500** hay **AC-7000** trước khi kết luận nguyên nhân hoặc lookup manual.

### Understanding
Water Clean là trạm tương đối ổn định, nhưng failure thực tế không chỉ đến từ “rửa không sạch”.
Issue thường đi theo full chain:
- transfer / conveyor / chain / jam
- liquid chemistry / concentration / mixing
- spray / pump / nozzle / pressure
- DI rinse / overflow / resistivity
- air knife / blower / drying
- interface / online-offline / no-board detect
- human operation / post-maintenance release gap

=> Không nên default quy lỗi về washing quality nếu chưa loại trừ transfer / chain / liquid / pressure / drying / sensor chain.

### Core engineering principle
- Physical reality before signal
- Nếu alarm jam / block:
  - ưu tiên xác thực **thật sự có board/card stuck hay chỉ false alarm**
- Nếu cleaning NG:
  - ưu tiên xem lại concentration / pressure / heating / DI quality / drying
- Nếu máy chạy nhưng output bất ổn:
  - ưu tiên check filter / nozzle / chain / overflow / pump / blower
- Nếu issue sau PM / cleaning / chemical change:
  - ưu tiên nghi release gap / wrong setup / incomplete restore trước

### Main machine structure
#### TZ-8500
Process chain điển hình:
- solvent soak
- chemical high pressure spray 1
- chemical high pressure spray 2
- DI natural rinse
- high pressure DI rinse 1
- high pressure DI rinse 2
- DI natural rinse
- blower drying

Main utility / module:
- raw liquid tank
- mixing tank
- DI water switch
- waste liquid discharge path
- pressure display
- chain speed display
- temperature controller
- conductivity / concentration display
- heater / blower / pump / EMO / lighting

#### AC-7000
Process chain điển hình:
- Cleaning 1
- Cleaning 2
- Chemical Isolation
- Raising 1
- Raising 2
- Raising 3
- Final Spraying (DI)
- Air-knife Drying 1
- Air-knife Drying 2
- Hot Air Drying

Main utility / module:
- chemical cleaning tank
- pre-rinse tank
- rinse tanks
- final DI spray
- air-knife isolation
- hot air drying chamber
- DI water inlet / outlet / drainage
- flow meter / resistivity meter
- pressure gauges
- heaters / blowers / pumps
- PLC + touch panel
- online / offline interface

### Process / chemistry focus
#### TZ-8500
- current solvent concept:
  - **N600 + DI water** mixed solvent
- mixing tank must keep stirring during production to prevent stratification
- first blending requires manual blending
- DI first, then raw solvent
- stir around 3 minutes before use
- concentration check required
- ionic contamination check required

#### AC-7000
- select suitable cleaning solution by product
- fill cleaning tank to target level
- fill DI water to rinse tanks
- set recipe / formula before run
- key formula items:
  - cleaning temperature
  - pre-rinse temperature
  - rinse temperature
  - drying temperature
  - mesh belt speed
  - pressure deviation alarm
  - resistivity alarm
  - substrate sensing time
  - stagnation / shielding / online timing
  - concentration ratio / replenish timing

### Key parameters / ranges
#### TZ-8500 practical focus
- chain speed setting:
  - **10 mm/s**
- station 1-6 temperature:
  - **60 ± 5 °C**
- drying section:
  - **85 °C**
- pure water tank:
  - **65 °C** (preheat purpose)
- spray pump motor frequency:
  - start from **30 Hz**
- upper spray pressure:
  - **0.55 – 0.65 MPa**
- lower spray pressure:
  - **0.45 – 0.55 MPa**

#### AC-7000 practical focus
- working speed:
  - **10 – 150 cm/min**
- suggested speed:
  - **60 cm/min**
- cleaning / rinse working pressure:
  - **0.1 – 0.4 MPa**
- final DI spray pressure:
  - **0.3 – 0.4 MPa**
- final DI water usage:
  - typically **8 – 12 L/min**
- DI resistivity must be monitored continuously
- inverter frequency range:
  - **10 – 50 Hz**
- pressure alarm uses deviation after startup reference

### Main failure families
- board / panel stuck
- conveyor / chain abnormal
- nozzle blockage
- pump pressure unstable
- water / chemical level low
- filter element blocked
- spray pressure low / unstable
- poor cleaning effect
- cleaning chemistry concentration low
- DI quality poor / resistivity low
- overflow insufficient / contamination accumulation
- blower / air knife weak
- drying insufficient
- heating not reaching set point
- online handshake issue
- false jam / false detect / no-board logic issue
- post-maintenance setup restore incomplete

### Main failure mechanism
Typical Water Clean chain:
small contamination / wrong concentration / filter block / nozzle choke / chain wear
→ pressure drift / spray coverage loss / drying instability / slow transport / false jam
→ cleaning NG / board stuck / repeat alarm / unstable output

Another common chain:
manual recovery / partial reset / parameter not restored after PM
→ machine can run but state no longer matches physical reality
→ intermittent jam / poor cleaning / false confidence release

### Quick checks
1. Confirm machine family first:
   - TZ-8500 or AC-7000

2. Physical reality first:
   - really stuck board?
   - chain smooth?
   - conveyor clear?
   - nozzles actually spraying?
   - blower actually running?
   - any leakage / overflow / splash abnormal?

3. Check liquid / chemistry:
   - correct chemical?
   - concentration in range?
   - mixing completed?
   - tank level normal?
   - liquid too dirty?
   - replacement interval overdue?

4. Check spray / pump / filter:
   - pressure stable?
   - upper/lower pressure in range?
   - filter blocked?
   - nozzle clogged?
   - pump current / relay / inverter normal?

5. Check DI / rinse / quality:
   - DI inlet open?
   - flow enough?
   - resistivity normal?
   - rinse tank changed / cleaned according rule?
   - overflow enough to prevent contamination build-up?

6. Check heating / drying:
   - cleaning temp reached?
   - drying temp reached?
   - air knife strong enough?
   - blower filter dirty?
   - drying fan running?
   - hot air actually circulating?

7. Check transfer / interface:
   - upstream/downstream ready?
   - online/offline mode correct?
   - stagnation / substrate length setting correct?
   - board detect sensors normal?

8. Check post-maintenance / post-change release gap:
   - nozzle reinstalled correctly?
   - filter replaced and locked?
   - valves reopened correctly?
   - sensor / float / thermocouple shifted?
   - pressure / speed / recipe uploaded again?

### Special jam handling rule
If Water Clean jam / stuck is found:
1. Press emergency stop
2. Turn off heaters
3. Open doors / improve ventilation if needed
4. Remove stuck board and all boards inside machine
5. Re-clean affected boards on another machine within local control rule if oxidation risk exists
6. Focus check on chain / transfer / blocking position
7. Repair damaged area
8. Dry run machine
9. Redo FAI before normal production

If alarm says jam but no actual stuck board found:
- acknowledge / mute alarm only after physical verification
- resume auto run
- observe continuously for at least 30 minutes before release

### Maintenance / PM focus
#### Daily
- keep machine surface clean
- check chain / conveyor status
- inspect spray status
- inspect pressure gauges
- inspect tank level
- clean table / visible residues
- for TZ-8500:
  - confirm DI switch open
  - confirm waste valve in correct state
- for AC-7000:
  - verify alarm / resistivity / flow display normal

#### Shift / routine
- chemical tank circulation / filtering
- rinse tank water replacement
- clean all filter screens
- inspect nozzles and ensure flow smooth
- inspect blower inlet filter
- inspect overflow / drainage / leakage

#### Weekly
- clean chemical / rinse tank
- clean box filter screen
- clean nozzles
- inspect fan filter
- inspect chain tension / chain teeth / lubrication
- inspect level sensor / float / thermocouple
- inspect air knife / spray rod / filter element

#### Monthly
- include all daily + weekly items
- full DI water flushing cycle
- clean all tanks thoroughly
- check overheat protection
- replace filter element as needed
- grease chains / bearings / transmission
- inspect motor / relay / inverter / blower condition

### Rule for incident / repository
Khi viết incident hoặc update knowledge cho Water Clean, bắt buộc ghi rõ:
- machine family
- model
- chemical type
- concentration status
- DI quality / resistivity
- pressure status
- chain / conveyor condition
- filter / nozzle status
- heating / drying status
- online-offline / interface condition
- whether issue happened after PM / cleaning / chemical change / jam recovery

### Interpretation rule
Water Clean issue không nên default là “wash not clean”.
Ưu tiên phân tích theo thứ tự:
- transfer / chain / real jam
- liquid level / concentration / contamination
- filter / nozzle / pressure / pump
- DI rinse / resistivity / overflow
- blower / air knife / drying
- sensor / interface / online setting
- human release gap / PM restore gap
- only then conclude machine hardware failure
---

## 2.2 CPF

### Understanding
CPF chủ yếu là nền tảng dispense của dòng **Nordson Asymtek Spectrum S-900 / S2-900**.
Rủi ro cốt lõi của CPF là **glue-related instability**, không phải mặc định machine breakdown.

Machine family / platform chính:
- Spectrum S-900 / S-900N series
- Spectrum II S2-900 / S2-900P / S2-9XXC series

Ứng dụng phổ biến:
- underfill
- dam & fill
- encapsulation
- lid seal
- cavity fill
- silicone / reagent dispense

### Core engineering principle
- FAI pass không đồng nghĩa process margin đủ rộng
- CPF issue thường bắt đầu từ material / pressure / viscosity / calibration chain
- Physical reality before signal:
  - glue age
  - air bubble
  - pressure stability
  - valve/nozzle condition
  - scale / flow-rate calibration
- Đừng default quy lỗi cho software/vision nếu chưa loại trừ material, air, valve và scale

### Main machine / process structure
CPF là hệ thống tích hợp nhiều khối:
- dispensing valve / jet / needle
- fluid reservoir / bulk fluid / syringe
- fluid pressure / valve pressure / cooling-coaxial pressure
- vision / fiducial / workpiece alignment
- height sensing
- service station:
  - dispense tile
  - tactile sensor
  - purge station
  - scale
- conveyor / lane / queue station
- heater / substrate heating / CpH
- software recipe / Fluidmove / fluid file / vision file / recipe file

### Main machine families / feature focus
#### S-900 / S-900N
- inline dispense platform cho semiconductor / assembly
- hỗ trợ underfill, cavity fill, die attach, encapsulation
- mechanical height sensor là base, laser height sensor là option
- MFC là option ở một số cấu hình
- programmable fluid / valve pressure tiêu biểu trên S-92X

#### S2-900 / Spectrum II
- high-volume inline dispensing system
- cấu hình linh hoạt hơn, support nhiều valve/jets hơn
- scale / MFC / CPJ / Monocle vision / Fids-on-the-Fly / programmable pressure mạnh hơn
- cleanroom, pre/post queue, CpH, lift table là các option quan trọng

### Supported valves / applicators
Các manual xác nhận CPF support nhiều loại valve / jet, trong đó các loại đáng chú ý:
- DJ / DispenseJet
- DV series
- NexJet
- IntelliJet
- DJ-9000 / DJ-9500 là nhóm hay gặp
- needle dispensing và jet dispensing có logic calibration khác nhau

### Critical technical focus
- glue / fluid condition
- pressure stability
- valve / nozzle / seat / o-ring condition
- scale accuracy / MFC / CPJ / dot weight
- vision-to-valve offset / fiducial / local machine offset
- heater / temperature / viscosity control
- low fluid / low pressure detection chain
- purge / priming / vacuum / suckback condition

### Software / traceability
CPF dùng **Fluidmove / FmXP** và file structure điển hình gồm:
- `.flu` = fluid file
- `.fmw` = dispense program
- `.avw` = vision file
- `.rcp` = recipe
- `.log` = production statistics / logging

Phần mềm hỗ trợ:
- Fluid Manager
- valve setup
- height sensor setup
- scale setup
- conveyor setup
- vision setup
- prompted setup / scripted setup
- machine offsets / local machine offsets
- setup logging / SPC data logging
- barcode support / RFID / scanner setup
- user levels: Service / System / Production

### Main troubleshooting logic
Khi CPF có issue, ưu tiên nghĩ theo chuỗi:
small issue →
pressure / viscosity / bubble / offset / calibration mismatch →
dispense amount drift / dot-line instability / false alert →
quality NG / intermittent defect / batch instability

Nếu output CPF bất thường, ưu tiên check:
- glue age / potlife / batch history
- pressure setting thực tế và pressure response
- valve/nozzle contamination, wear hoặc mismatch
- scale và flow-rate calibration
- heater / substrate heat / viscosity condition
- vision / offset / fiducial setup
- low fluid / low pressure detection threshold

### Main watch points
- glue overflow
- dot weight instability
- valve / chamber wear
- process margin sensitivity
- nozzle validation / trial
- batch-to-batch viscosity drift
- priming / purge không đủ
- intermittent air / bubble / stale glue pattern
- scale drift sau move / cleaning / maintenance
- sensor low fluid / low pressure báo không đúng timing

### High-risk failure families in CPF
- glue-related instability
- pressure instability
- stale / expired / out-of-potlife material
- air bubble / incomplete priming
- valve degradation / seat-o-ring wear
- scale / MFC / CPJ calibration drift
- vision / valve offset mismatch
- manual override / force run khi chưa re-offset / recalibrate
- false low fluid / false low pressure detection
- FAI pass nhưng batch margin thực tế quá sát

### Main failure mechanisms
- batch margin quá sát:
  - FAI pass nhưng không đại diện cho MP
- glue ngậm khí / ngậm ẩm:
  - tạo intermittent output, khó lặp lại nếu chỉ spot-check
- valve / nozzle wear:
  - dot-line không đồng đều, lệch lượng bơm
- scale drift hoặc chưa recalibrate:
  - MFC / CPJ bù sai → lượng keo sai
- offset giữa camera / valve / scale lệch sau thay đầu, cleaning hoặc maintenance
- low fluid / low pressure threshold không khớp:
  - machine báo sai hoặc báo trễ

### Quick checks
1. Check material first:
   - glue lot / expiry / potlife / storage / warm-up
2. Check physical dispense chain:
   - syringe / reservoir / cap sealing / air bubble / priming / purge
3. Check pressure:
   - main air
   - fluid pressure
   - valve pressure
   - cooling/coaxial pressure
   - vacuum / suckback nếu có
4. Check valve / nozzle:
   - contamination
   - wear
   - wrong type / wrong setup
5. Check scale / calibration:
   - recent MFC / CPJ / flow-rate / dot-weight calibration
   - scale level / scale condition
6. Check heater / viscosity:
   - substrate heating
   - needle/nozzle heater
   - CpH / preheat / cool-down logic
7. Check vision / offsets:
   - fiducial
   - camera
   - local machine offset
   - valve bias / master offset
8. Check software / human factors:
   - wrong fluid file / recipe
   - manual override
   - force run
   - skipped setup after maintenance / cleaning / valve change

### Maintenance / PM focus
#### Daily
- check air / water trap / clean dry air
- check purge cup / scale cup / purge boot
- verify glue handling / reservoir / line cleanliness
- verify pressure gauges / digital gauge status
- verify no abnormal leak / drip / overflow
- keep service station and dispense area clean

#### Weekly / routine
- verify scale level / scale calibration condition
- verify board sensor / height sensor / tactile sensor
- inspect valve/nozzle wear and contamination
- inspect cable / linear guide / belt / conveyor condition
- inspect water trap và drain moisture
- verify heater and needle heater condition

#### After maintenance / cleaning / hardware touch
- re-check offsets
- re-check scale / MFC / CPJ
- re-check valve setup
- re-check pressure response
- re-check vision / fiducial / teaching
- do not release machine if these are skipped

### Rule
FAI pass does **not** mean process margin is stable enough.

Bắt buộc extract khi ghi incident CPF:
- machine model / platform
- valve / nozzle type
- fluid lot / expiry / potlife
- pressure setting
- scale / MFC / CPJ status
- heater status
- calibration / offset history
- time since maintenance / cleaning / valve change

### Interpretation rule
CPF issue nên ưu tiên interpret là:
- Process instability
- Material / glue margin issue
- Pressure / valve / nozzle issue
- Sensor / detection mismatch
- Calibration / offset drift
- Human setup / post-maintenance release gap

Không default là machine breakdown nếu chưa loại trừ:
- glue
- pressure
- calibration
- heater
- offset
- manual operation effect
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
Trạm Laser hiện sử dụng **2 loại máy chính**:
- **E&R (LM series)**: LM-101AL, LM-101LT, LM-201LC
- **Hans (CL series)**: HNDZ-CL4030 và các máy Hans cùng họ CL/FPC

=> Khi troubleshooting hoặc viết incident, phải **xác nhận rõ machine family là E&R hay Hans** trước khi kết luận nguyên nhân hoặc tham chiếu manual.

### Main machine structure
#### E&R
- Load / Laser / Unload
- Một số cấu hình có AOI riêng
- XY table
- CCD alignment
- 2D code reader / tray mapping / handler interface
- Dust extraction / vacuum / chiller / ion air

#### Hans
- PLC / panel / software control
- XY working table
- CCD / mark / template / 2D teaching
- Laser control software
- Conveyor / stopper / clamp / vacuum cylinder
- Chiller / dust filtering / safety door / interlock

### Critical technical focus
- laser head / optical path
- XY table / motion repeatability
- CCD / mark / 2D / template
- cooling / chiller / water quality
- vacuum / dust extraction / airflow
- transfer / loader-unloader / interface with handler
- software file / traceability / logging

### Software / traceability
#### E&R
- dùng flow teaching theo DXF
- hỗ trợ Fiducial teaching
- hỗ trợ 2D teaching
- có Operator / Engineer / Supervisor mode
- có log, account setting, parameter setting
- liên quan trực tiếp đến mapping / 2D / handler-laser interface

#### Hans
- dùng phần mềm HansLCS / HansSoft
- hỗ trợ file dxf / plt / hs và các định dạng hình ảnh
- hỗ trợ barcode / QR / DataMatrix
- có CCD operation, BOX calibration, offset calibration
- có user management và log vận hành
- phù hợp cho marking / cutting / split / auto alignment

### Operation / calibration / teaching
#### Common logic
- phải kiểm tra đúng file sản phẩm / template / mark / 2D rule trước khi chạy
- phải kiểm tra safety door, vacuum, khí nén, chiller, dust exhaust trước run
- sau model change hoặc setup mới phải verify:
  - alignment
  - mark
  - 2D
  - auto-run path
  - file / template đúng theo machine family

#### E&R watch points
- DXF teaching
- Fiducial mark teaching
- 2D teaching
- orientation teaching
- auto/online-offline logic
- parameter enable/disable theo chức năng máy

#### Hans watch points
- calibration bắt buộc trước marking/cutting
- CCD calibration / offset correction / BOX calibration là cốt lõi
- template / mark / focus / file format phải đúng
- user Hans system có logic riêng, tránh sửa sai quyền hạn

### High-risk failure families in Laser
- post-maintenance alignment release gap
- false-clear transfer issue
- ULD / lift / conveyor communication gap
- manual override during transfer
- CT / vision instability
- mark / CCD / template mismatch
- 2D read fail / duplicate code / wrong mapping
- chiller / cooling instability
- dust extraction / vacuum effectiveness drop

### Main troubleshooting groups
- laser source / controller not ready
- 2D code read error
- duplicate 2D code
- mark / positioning / CCD capture issue
- motion card / servo / driver / I/O issue
- stage / home / limit / origin mismatch
- safety door / interlock abnormal
- software-not-ready / wrong file / path / exchange folder / SFIS issue
- vacuum / air / clamp / cylinder state abnormal
- chiller / water / cooling alarm

### Quick checks
1. Confirm machine family first: **E&R or Hans**
2. Physical reality first:
   - product clear?
   - conveyor / stopper / clamp / table position normal?
3. Check utility:
   - power / air / chiller / dust exhaust / vacuum
4. Check sensor / detection:
   - mark / 2D / door / in-position / CCD / reader connectivity
5. Check control / interface:
   - Handler ↔ Laser I/O
   - software path / exchange folder / SFIS
6. Check recipe / file / teaching:
   - DXF / hs / template / ROI / score / calibration file
7. Check post-maintenance / post-model-change release gap

### Maintenance
#### Daily
- check cooling fan / abnormal sound
- check air pressure / vacuum status
- check safety door function
- clean dust collector outer area
- verify ion / airflow / dust extraction
- check conveyor foreign objects / belt damage / motor noise
- check XY table / servo abnormal sound
- verify nozzle / suction / fixture / kit cleanliness
- check sensor cleanliness and response

#### Weekly
- check safety labels / tower light / monitor
- check dust filter condition
- check dust hose / airflow
- clean all sensors
- clean and lubricate ballscrew / moving mechanism
- clean optical scale / CCD lens / CCD body
- check vacuum solenoid / tube leakage
- check stopper / pusher / cylinder looseness
- check conveyor belt tension

#### Quarterly
- inspect pressure gauges / muffler / solenoid / air tubing / fittings
- clean vacuum pump exterior
- clean fan / dust collector / filter bin
- lubricate slide rail / screw / linkage / cylinder / linear bush
- check motor belt tightness

### Lifecycle / calibration rule
- recalibration every 6 months
- recalibration required when running a new model
- high precision use requires more frequent alignment / box / offset review

### Rule for incident / repository
Khi ghi incident hoặc update knowledge cho trạm Laser, bắt buộc thêm:
- **Machine family: E&R / Hans**
- **Model**
- **Software / template type (nếu biết)**
- **manual tham chiếu đúng theo loại máy**

### Interpretation rule
Laser issue không nên default là laser source fault.
Ưu tiên phân tích theo thứ tự:
- transfer / interface / readiness
- CCD / mark / 2D / template
- motion / servo / I/O / control card
- utility / chiller / vacuum / dust
- software / file / SFIS / exchange path
- chỉ sau đó mới nghi laser head / optical source

---

## 2.5 Dry Ice / Trench Dry Ice / Cutting DIC

### Understanding
Dry Ice / Trench Dry Ice / Cutting DIC phải được xem là **full cleaning system**, không chỉ là nozzle.
Failure thường đến từ toàn chuỗi:
- dry ice source
- CDA / compressed air quality
- feeder / shaver / chute / nozzle
- N2 / hot air / heating / drying
- vacuum / chuck / clamp / pedestal / cleaning table
- dust collector / exhaust / ventilation
- scanner / 2D / camera / SECS / SFIS / software / host
- loader / unloader / magazine / carrier / conveyor / robot interface

### Machine family
Dry Ice trên line có thể gặp các họ máy chính:
- Cold Jet dry ice cleaning system (ví dụ MicroClean / shaved dry ice type)
- E&R custom Dry Ice Cleaner / Trench Dry Ice line
- Intelume CCM-A200 / CCM-A201 Auto Dry Ice Cleaning system

### Core engineering principle
- Physical reality before signal
- Dry Ice issue không nên mặc định coi là nozzle fault
- Phần lớn lỗi bắt đầu từ:
  - moisture / humidity
  - weak / unstable air
  - poor dry ice feeding
  - shaver / blade / chute wear
  - wrong recipe / wrong path / wrong process
  - scanner / host / interface mismatch
- Humidity / condensation là top repeat mechanism đối với clog, output drop, unstable cleaning và intermittent alarm

### Main machine structure
#### Common full system blocks
- dry ice machine / dry ice source
- feeder / pusher / shaver / chute
- nozzle / nozzle angle / nozzle spacing
- robot / motion path / cleaning path
- cleaning table / vacuum / lift / clamp / gate
- preheat station
- drying lane / hot air / ion / N2 / chamber gas control
- dust collector / negative pressure / filter
- carrier / loader / unloader / conveyor / cassette / magazine
- scanner / 2D / camera / recipe / SECS-GEM / SFIS / host if integrated

#### Intelume CCM-A200 / CCM-A201 focus
- loading / unloading area
- preheat area
- cleaning area
- dry lane
- input/output robot arms
- dual dry ice machines / dual nozzles
- nozzle spacing axis / nozzle angle control
- 2D code reading for tray and product
- process page / path page / account / record / alarm / maintenance page

#### E&R Dry Ice Cleaner focus
- LD / ULD / runway / chamber
- cleaning A/B zones
- fixed nozzle / movable nozzle
- hot air / N2 / Dust Collector / CO2 concentration monitor
- vacuum detect / gate / side clamp / panel detect
- host local-remote / recipe / parameter / log / alarm detail

### Utility / facility rule
Dry Ice chỉ ổn nếu utility chain đúng:
- dry ice source / media condition
- compressed air / CDA clean and dry
- adequate pressure and flow
- exhaust / ventilation available
- dust collector available
- vacuum system healthy
- humidity under control
- if equipped: N2, hot air, heater, CO2 monitor, camera/reader, robot ready

#### Common utility thinking
- Nếu air line có nước hoặc dew point không tốt, feeder/chute/nozzle rất dễ đóng băng
- Nếu dust exhaust yếu hoặc filter block, cleaning quality và alarm chain sẽ xấu
- Nếu CO2 concentration cao, phải ưu tiên safety / ventilation trước khi nghĩ tới production

### Operation / startup / shutdown
#### Common startup logic
1. Confirm power / UPS / PC / software normal
2. Confirm air / CDA / N2 / vacuum / dust collector / dry ice machine ready
3. Confirm trough / feeder / chute / nozzle area dry and clean
4. Purge air before loading or before restarting after long idle / break
5. Add dry ice correctly, push pusher plate to proper contact position
6. Confirm recipe / process / path / product program / host mode correct
7. Confirm safety doors closed and alarm-free
8. Run initialization / home / servo-on / origin search where required
9. Only then allow auto run

#### Common shutdown logic
- stop auto mode first
- stop dry ice output
- remove remaining dry ice if required
- clean feeder / trough / machine interior
- depressurize / bleed line if applicable
- stop software / PC / machine power by standard sequence

### Process / recipe / teaching focus
Dry Ice machine có thể có process hoặc path setup, không được coi là “fixed machine”:
- product recipe / process name
- path / route / robot movement count
- nozzle angle
- nozzle spacing
- output wait time / pre-spray logic
- cleaning speed / move speed
- single-unit vs full-panel clean
- dry ice detect threshold
- dry ice minimum quantity per cycle
- idle timeout / pre-spray after idle
- preheat / clean table / hot air / drying time
- pressure / flow / humidity / CO2 alarm thresholds
- 2D reader positions / tray code / product code / SFIS path / host mode

### Main failure families
- dry ice output weak / intermittent
- no dry ice output
- chute / feeder / nozzle clogging
- dry ice low / empty / insufficient for one cycle
- air pressure low / air flow abnormal
- dry ice machine idle timeout
- dry ice machine power off / ready missing
- dry ice spray abnormal based on IR or temperature detect
- nozzle angle mismatch
- vacuum abnormal on cleaning table / pedestal / chuck
- dust collector negative pressure too low / too high
- filter blocked
- chamber / humidity / condensation issue
- CO2 concentration abnormal
- hot air / preheat / clean table temperature abnormal
- loader-unloader / conveyor / arm / robot / gate / cylinder abnormal
- 2D reader / tray code / material code / host / SFIS mismatch

### Main failure mechanism
Typical Dry Ice chain:
small moisture / poor air / dirty trough / worn shaver / long idle
→ ice build-up / feeding unstable / pressure-drop / output delay
→ nozzle clog / false low-ice / false spray-abnormal / cleaning miss
→ quality NG / stop line / repeated restart / repeat issue

For Cutting Dry Ice, a second common chain is:
wrong path / wrong angle / wrong nozzle spacing / wrong detect threshold
→ spray misses target or output judged abnormal
→ machine stop / partial clean / repetitive alarm / false debug loop

### Main watch points
- humidity trend vs clogging trend
- moisture in line / trap / feeder / water bucket
- blast/air pressure drop during run
- air flow deviation
- dry ice detect stability
- dry ice consumption per run
- dual dry ice machine balance
- nozzle angle drift
- nozzle spacing drift
- IR temp detect alignment
- vacuum / negative pressure trend
- filter blockage trend
- dry ice machine idle time
- preheat / clean table / hot air temperature drift
- scanner / 2D / host / SFIS read fail trend
- manual clear / manual override frequency after alarm

### Quick checks
1. Confirm machine family first:
   - Cold Jet / E&R / Intelume CCM-A200 / CCM-A201

2. Physical reality first:
   - dry ice present?
   - feeder / pusher / shaver / chute free?
   - nozzle clogged?
   - trough wet?
   - dry ice sticking / melting / bridging?
   - product / tray / carrier physically in correct position?

3. Check utility:
   - CDA / air pressure
   - air flow
   - hose size / line restriction
   - moisture trap / aftercooler / dryer
   - dust collector / negative pressure
   - vacuum pump
   - N2 / hot air / heater if used
   - CO2 ventilation / safety condition

4. Check output path:
   - nozzle angle
   - nozzle spacing
   - robot path / route / movement count
   - pre-spray / idle handling
   - dry ice detect sensor / IR sensor position

5. Check integrated mechanism:
   - lift / gate / clamp / cylinder / conveyor / robot arm
   - clean table vacuum and tray clamp
   - preheat / dry lane motion
   - loader-unloader ready and no jam

6. Check software / interface:
   - process recipe
   - path file / route program
   - local / remote / host mode
   - SECS / SFIS / scanner / 2D / material code path
   - program damaged or wrong product loaded

7. Check repeat mechanism:
   - long idle?
   - high humidity?
   - after maintenance?
   - after filter change / blade change / nozzle clean?
   - after product/path change?

### Maintenance / PM focus
#### Daily
- keep feeder / chute / trough dry and clean
- remove remaining dry ice and moisture
- inspect nozzle / hose / cable / fitting
- inspect dry ice machine power / ready state
- inspect water bucket / condensation
- inspect safety doors / covers / interlocks
- verify vacuum / dust collector / airflow
- verify scanner / 2D / indicator / alarm-free startup

#### Weekly / routine
- inspect shaver / blade / skate life
- inspect feeder / pusher / chute wear
- inspect dust collector filter / negative pressure trend
- inspect air line water / trap / filter / dryer
- inspect nozzle angle / spacing / teaching values
- inspect vacuum cups / seals / clamp / gate / cylinders
- inspect heater / preheat / hot air / clean table temperatures
- inspect reader positions and code reading quality

#### After maintenance / cleaning / long idle
- purge air first
- confirm no ice build-up
- confirm nozzle path and angle
- confirm pressure / flow / detect thresholds
- confirm vacuum and filter state
- confirm process / path / recipe / scanner settings
- do not release machine if these are skipped

### Safety / interlock rule
- CO2 is an asphyxiation risk under poor ventilation
- dry ice can injure skin and eyes
- static / bonding / grounding may matter depending on line condition
- never bypass safety door, interlock, ventilation or CO2 alarm logic
- if CO2 concentration abnormal, treat as safety-first issue, not nuisance alarm
- if Dust Collector / vacuum / filter alarms exist, do not assume cleaning quality is still okay

### Rule for incident / repository
Khi ghi incident hoặc update knowledge cho Dry Ice / Cutting Dry Ice, bắt buộc ghi rõ:
- machine family
- model
- dry ice source / media type
- air quality condition
- pressure / flow
- humidity / condensation condition
- nozzle / shaver / blade condition
- recipe / path / angle / spacing condition
- vacuum / dust collector / filter condition
- scanner / 2D / host / SFIS / SECS condition if integrated
- whether issue happened after long idle / maintenance / cleaning / product change

### Interpretation rule
Dry Ice issue không nên default là nozzle issue.
Ưu tiên phân tích theo thứ tự:
- air quality / moisture / humidity
- dry ice media and feeding
- shaver / blade / feeder wear
- nozzle / angle / spacing / detect alignment
- vacuum / dust / exhaust / CO2 safety chain
- robot / path / gate / clamp / tray handling
- scanner / host / SFIS / SECS / software
- only then conclude local hardware failure
---

## 2.x Jigsaw

### Machine family
Trạm Jigsaw sử dụng cutting equipment với các platform chính:
- Jigsaw cutting machine (multi-axis cutting system)
- Spindle option:
  - 1.8 kW
  - 2.2 kW
- Vacuum system:
  - external vacuum unit 2.2 kW

=> Khi support / viết incident phải ghi rõ:
- spindle type (1.8 / 2.2 kW)
- vacuum unit condition

### Understanding
Jigsaw là trạm **mechanical cutting + motion control + vacuum removal system**.

Failure không chỉ là “cut không đẹp”, mà thường đến từ:
- blade condition
- spindle vibration
- panel flatness / clamp / vacuum
- alignment / CCD offset
- motion axis stability

=> Đây là trạm có ảnh hưởng trực tiếp đến:
- burr
- crack
- scratch
- edge quality
- hidden defect

### Core engineering principle
- Physical reality before signal
- Cutting issue = combination của:
  - blade
  - spindle
  - table/vacuum
  - alignment
  - path/motion

=> Không được default là “blade bad” nếu chưa check:
- vacuum hold
- panel flatness
- alignment offset
- spindle stability
- axis deviation

### Main machine structure
#### Alignment system
- CCD alignment
- fiducial detection
- offset correction

#### Motion system
- X1 / X2 axis
- Y1 / Y2 axis
- Z1 / Z2 axis
- Theta1 / Theta2 (rotation)
- MY1 / MY2 (auxiliary axis)

=> Multi-axis coordination quyết định:
- path accuracy
- cutting quality

#### Cutting system
- spindle motor (1.8 kW / 2.2 kW)
- cutting blade
- wheel cover

#### Table system
- jig table
- vacuum holding
- flatness control

#### Cleaning / debris handling
- remnant discharge brush
- debris removal path
- water / cooling (if equipped)

#### Vacuum system
- external vacuum unit (2.2 kW)
- dust / particle removal during cutting

#### Operation system
- touch panel
- USB / program input
- status indicator

### Key technical focus
- blade wear / sharpness
- spindle vibration / noise
- vacuum holding strength
- panel flatness / warpage
- alignment accuracy
- axis position repeatability
- cutting path correctness
- debris removal effectiveness

### Startup / operation / shutdown
#### Startup
1. Power ON machine + vacuum unit
2. Confirm air/vacuum normal
3. Home all axis
4. Check blade condition
5. Load program / path
6. Verify alignment
7. Dry run (if needed)
8. Start auto run

#### Operation
- Monitor:
  - spindle sound
  - cutting vibration
  - debris removal
  - panel movement
- Avoid:
  - manual intervention during cutting
  - skipping alignment after change

#### Shutdown
- Stop cutting
- Turn off spindle
- Stop vacuum
- Clean debris
- Inspect blade and table

### High-risk failure families
- burr / edge roughness
- panel crack / micro-crack
- edge chipping
- scratch on surface
- incomplete cut
- path deviation
- vibration-induced defect
- vacuum failure → panel movement
- debris accumulation → secondary scratch
- misalignment → wrong cut position

### Main failure mechanism
Typical Jigsaw chain:

blade wear / vacuum weak / panel not flat  
→ vibration / displacement during cut  
→ uneven force / mis-cut / debris accumulation  
→ burr / crack / scratch / hidden defect  

Another pattern:

alignment offset / wrong path  
→ cut position shifted  
→ product NG or latent defect

### Quick checks
1. Physical check first:
   - panel flat?
   - vacuum holding OK?
   - jig stable?
   - debris accumulated?

2. Blade / spindle:
   - blade worn?
   - spindle noise abnormal?
   - vibration present?

3. Alignment:
   - CCD detect correct?
   - offset changed?
   - fiducial clear?

4. Motion:
   - axis jitter?
   - repeatability issue?
   - path correct?

5. Vacuum / debris:
   - vacuum unit running?
   - suction enough?
   - dust collector blocked?

6. Process condition:
   - wrong program?
   - wrong product?
   - after blade change / maintenance?

7. Post-maintenance check:
   - alignment redone?
   - vacuum restored?
   - spindle rechecked?

### Maintenance / PM focus
#### Daily
- clean table and debris
- check vacuum unit running
- check blade condition
- check abnormal vibration/noise
- check jig surface

#### Weekly
- inspect spindle condition
- inspect axis movement
- check alignment accuracy
- inspect vacuum piping / leakage
- clean dust path

#### Monthly
- check spindle wear
- check motor and coupling
- check axis calibration
- replace blade if needed
- inspect vacuum motor performance

### Safety / interlock
- rotating blade = high injury risk
- never open cover during cutting
- vacuum must be on before cutting
- emergency stop must work correctly
- avoid manual intervention during auto run

### Lifetime / vendor logic
- blade = lifetime-controlled item
- spindle = performance degrade over time
- vacuum motor = degradation affects yield indirectly
- axis accuracy = drift over long-term use

=> Vendor logic cần tôn trọng:
- blade change interval
- spindle maintenance interval
- vacuum system maintenance

### Rule for incident / repository
Khi ghi incident cho Jigsaw, bắt buộc gồm:
- machine model
- spindle type (1.8 / 2.2 kW)
- blade condition
- vacuum condition
- alignment status
- panel type / flatness
- defect type (burr / crack / scratch / mis-cut)
- whether issue after maintenance / blade change

### Interpretation rule
Jigsaw issue không nên default là blade issue.

Ưu tiên phân tích theo thứ tự:
- vacuum / panel holding / flatness
- blade / spindle condition
- alignment / offset
- motion / axis stability
- debris / dust removal
- process / path / setup
- human / post-maintenance release gap
- only then conclude hardware failure
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
