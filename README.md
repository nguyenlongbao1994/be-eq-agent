# BE EQ Agent Knowledge Base

Repository này là nguồn tri thức chính cho **BE EQ troubleshooting, incident conversion, reporting, training, pattern analysis và Agent grounding**.

Mục tiêu:
- Hỗ trợ kỹ sư line debug issue nhanh hơn
- Chuẩn hóa cách mô tả **symptom / mechanism / root cause / action**
- Dùng làm **knowledge source** cho Agent / Copilot
- Hạn chế trả lời generic, nhầm case, hoặc reuse dữ liệu cũ
- Hỗ trợ phân tích cho **Watch** và **Hana**
- Tạo nền tảng chung cho:
  - line troubleshooting
  - incident writing
  - report review
  - readiness review
  - repeat prevention

---

## 1. Repository này dùng để làm gì

Repository này **không chỉ lưu issue history**. Repository này phải giúp kỹ sư và Agent:

1. hiểu đúng **failure mechanism**
2. phân biệt **machine failure** với:
   - process instability
   - sensor / detection gap
   - interface / communication failure
   - human operation error
   - transfer / positioning issue
   - capacity / readiness issue
   - system / traceability mismatch
3. tái sử dụng **failure patterns** đã từng xảy ra
4. viết report / incident / troubleshooting note theo cùng một chuẩn
5. tránh:
   - nhầm case
   - reuse case cũ
   - lệch slug giữa incident register và file detail
   - kết luận “machine breakdown” quá sớm

---

## 2. Core BE Principle

### 2.1 Main Process Flow
Water Clean → Baking → Plasma → Molding → Laser → Trend Dry Ice → Plasma → CPF → Curing → Jigsaw / Lasercut → Cutting Dry Ice → Tape → Sputter → AVI

> Lưu ý: trong thực tế line, một số flow có thể khác theo model / routing / automation design. Khi phân tích issue, luôn xét **upstream / downstream interaction**, không chỉ nhìn cục bộ theo station.

### 2.2 Main Troubleshooting Principle
Phần lớn lỗi **không phải machine breakdown**.

Nguồn lỗi chính thường đến từ:
- Process instability
- Sensor / detection gap
- Mechanical wear / misalignment
- System integration issue
- Human operation error
- Transfer / positioning issue
- Interface / communication failure
- Traceability / system-state mismatch
- Capacity / readiness mismatch

### 2.3 Typical Failure Chain
Typical chain thường gặp tại BE:

```text
Small issue
→ false clear / wrong timing / missing feedback
→ jam / collision / drop / stacking / defect
```

Ví dụ recurring chain trong line:
- downstream fail but upstream still run
- manual override trong khi transfer chưa complete
- machine physical OK nhưng upper system vẫn abnormal
- maintenance xong nhưng release / verify chưa hoàn chỉnh

### 2.4 Physical Reality First
Nguyên tắc quan trọng nhất:

```text
Physical reality > system assumption
```

Luôn kiểm tra trước:
- panel đã thật sự ra khỏi table chưa?
- carrier đã thật sự cleared chưa?
- conveyor / lift / ULD có thật sự chạy không?
- downstream có thật sự ready không?
- alarm chỉ clear ở machine hay đã clear ở upper system?

---

## 3. Current Watch Points

### Cold Jet #22
- Output / weight có hiện tượng tụt dưới spec
- Hướng nghi chính:
  - dry ice quality variation
  - partial nozzle freezing
  - CDA fluctuation
- Đây là pattern **intermittent utility / process instability**, không nên mặc định là hỏng phần cứng

### Plasma 3 SFIS
- Machine-side data sending đã OK
- IT routing chưa hoàn tất
- Station chưa fully online
- Đây là case điển hình của **traceability / routing gap**, không phải machine process fail

### Laser CT instability
- Có machine gây CT cao hơn
- Có liên quan đến vision NG / cannot detect
- Phải tách rõ:
  - machine-side motion overhead
  - vision detect instability
  - automation sequence inefficiency

### Mold 147 Press 2
- Abnormal trong lúc cleaning
- Đã isolate, đang điều tra nguyên nhân
- Không nên kết luận press NG nếu chưa check mold side / residue / handling effect

### Jigsaw
- Blade và brush phải kiểm soát theo lifetime
- Machine 58: ~700 panel / blade
- Other machines: ~500 panel / blade
- Brush: replace every 108000 runs
- Ngoài lifetime, còn phải theo dõi:
  - blade-nozzle gap
  - panel flatness
  - table condition
  - hidden quality drift before alarm appears

---

## 4. Hana Project Context

Hana đang dùng chung nhiều nguồn lực / line context với Watch.

### 4.1 Readiness classification
Phân loại readiness nên theo 4 nhóm:
1. Machine available
2. Need transfer
3. Need new buy / long lead time
4. Can share with Watch but must control capacity

### 4.2 Known points
- Hầu hết machine MP đã có sẵn
- Vacuum Baking là hạng mục cần transfer
- Một số EE lab item có lead time dài

### 4.3 Risk themes
Khi support Hana, luôn xét thêm:
- shared-line capacity conflict
- readiness gap
- long lead time items
- ramp timing risk
- lab / validation dependency

---

## 5. Repository Structure

### `README.md`
Tổng quan repository, governance dữ liệu, rule sử dụng và điều hướng file

### `instruction.md`
Rule cho Agent / Copilot:
- cách suy luận
- cách đọc case mới
- cách tránh reuse case cũ
- cách tạo incident code
- cách kiểm tra duplicate
- cách reset context khi user gửi ảnh case mới

### `knowledge_db.md`
Tri thức chuẩn hóa theo:
- station
- equipment / process
- failure patterns
- automation / integration
- Watch / Hana context
- recurring lessons

### `troubleshooting.md`
Playbook line-ready:
- quick check
- failure chain
- troubleshooting order
- report format
- incident conversion rule
- station-specific checklist

### `incidents/README.md`
Master incident register

### `incidents/YYYY/*.md`
Mỗi issue thực tế = **1 file markdown riêng**

---

## 6. Recommended Usage

Use this repository for:
- Daily / weekly BE EQ reporting
- Incident review and troubleshooting reference
- Training new engineers / PD support
- Watch / Hana readiness review
- Automation / SFIS / OTMS / interface follow-up
- Converting images / slides into incident markdown
- Comparing new issue with old issue before concluding root cause

---

## 7. Key Station Notes

### Water Clean
- Core process tương đối ổn định
- Theo dõi:
  - loader / unloader
  - transfer interface
  - scanner robustness
  - carrier condition / top cover
  - tank / pump / solenoid / heater / SSR
- Recurring patterns:
  - carrier stacked do sensor fail detect
  - missing / dropped panel do carrier không có top cover
  - motor mixing pump overload
  - bearing / shaft damaged
  - external tank water leak
  - rinse tank heating abnormal

### CPF
- Rủi ro chính là glue-related instability
- FAI pass không đồng nghĩa margin đủ rộng
- Phải xét cả:
  - valve / nozzle / holder / collar / solenoid wire
  - scale / measurement abnormal
  - PC / LPT / RS232 / barcode path
  - glue tube connection
  - center lift table contamination
- Recurring patterns:
  - glue on back surface of panel
  - valve cannot production
  - dot weight unstable
  - input conveyor error
  - new PC cannot scan barcode

### Molding
- Transfer abnormal → kiểm mold side / contamination / mold incomplete
- Vacuum abnormal → ưu tiên nghi mold side
- No input > 12h → redo FAI
- Đây là multi-module system, cần nhìn cả:
  - handling
  - transfer
  - press
  - vacuum
  - pellet / compound
  - mold chase / clamp / cavity / venting / cull

### Laser
- Trọng tâm kỹ thuật:
  - laser head
  - working table
  - optical path
- Có liên kết SFIS và yêu cầu cooling control
- Transfer / ULD / lift / conveyor interface là nguồn rủi ro lớn
- Out signal có thể “clear” nhưng panel chưa thật sự ra khỏi table
- Recurring patterns:
  - false clear
  - no feedback from downstream
  - panel drop / pop-out / collision
  - post-maintenance release gap
  - config / PC / scanner / barcode issue

### Dry Ice / LT Dry Ice / Cutting Dry Ice
- Không chỉ là nozzle
- Phải nhìn cả:
  - dry ice source
  - CDA
  - vacuum
  - magazine / carrier / conveyor
  - scanner / SMD / status sync
  - robot / initialization / battery (nếu có)
- Recurring patterns:
  - SIP fall / broken by handling mismatch
  - lane reader unstable
  - SMD false alarm
  - intermittent Cold Jet instability
  - automation CT issue

### Jigsaw / Saw
- Lifetime control rất quan trọng
- Blade / brush / cleaning water ảnh hưởng trực tiếp đến quality
- Blade-nozzle gap và panel flatness có thể gây:
  - scratch
  - vision stop
  - dimension issue
  - crack / burr / hidden defect

### Sputter
- DC power / cathode / clamp / chamber contamination là pattern quan trọng
- Transmission / coupling / belt / motor / timeout cũng là recurring pattern
- Cần tách rõ:
  - EMO / safety-triggered stop do người thao tác
  - equipment-side fault thật
- Recurring patterns:
  - DC1 / DC4 / DC5 / DC7 alarm
  - cathode short
  - clamp peeling
  - transport timeout / M8 malfunction
  - coupling loose

### Baking / Curing / OTMS
- Phải tách actual oven / heating / door issue khỏi traceability / OTMS / IT issue
- Recurring patterns:
  - OTMS cannot auto pass station
  - UOP lock because abnormal S/N still remained in system
  - temperature profile not recorded while oven still ran normal
  - oven door open due to steel-key / lock geometry issue

---

## 8. Data Governance Rules

### 8.1 Only validated data
- Chỉ dùng dữ liệu đã được xác nhận trong:
  - image
  - slide
  - note
  - log
  - training
  - report
- Không tự suy đoán root cause nếu chưa có evidence

### 8.2 If data is missing
Khi không có dữ liệu xác nhận, phải ghi rõ:
- `Data not available in current knowledge`

### 8.3 Duplicate Check Rule
Trước khi tạo incident mới:
- Check với case ngay trước đó
- So machine / station / mechanism / issue chain
- Nếu cùng machine + cùng mechanism → kiểm tra xem có phải repeat issue
- Nếu khác machine nhưng cùng mechanism → mention “related pattern”

### 8.4 Incident Link Rule
Trong `incidents/README.md`, cột cuối luôn dùng relative link dạng:
```md
./YYYY/file-name.md
```

### 8.5 Incident Conversion Consistency Rule
Khi output Code 1 / Code 2 / Code 3:
- Code 1 là row cho register
- Code 2 là path file
- Code 3 là detail markdown
- **Code 1 và Code 2 phải match 100% slug**
- Nếu lệch 1 ký tự cũng phải sửa trước khi trả lời

### 8.6 New-image reset rule
Mỗi ảnh mới phải được đọc lại từ đầu. Không được reuse machine/date/root cause/slug từ case trước.

---

## 9. Agent Rules Summary

Agent phải:
- đọc case mới từ đầu
- không reuse machine/date/slug từ case trước
- ưu tiên **physical reality before system assumption**
- phân biệt:
  - Machine issue
  - Process issue
  - Sensor / false clear
  - Interface / no feedback
  - Human override / manual reset
  - Capacity / readiness issue
  - Traceability / routing / OTMS / SFIS issue

Ngoài ra, Agent phải:
- so với related history trước khi kết luận
- ưu tiên actionable checks tại line
- luôn nói rõ confirmed root cause vs working hypothesis vs unknown

---

## 10. Maintainer Note

This repository is intended to support practical BE EQ work:
- real line troubleshooting
- real report writing
- real automation risk follow-up
- real project readiness comparison between Watch and Hana
- incident standardization for Agents
- repeat pattern learning across stations

Mục tiêu cuối cùng là để Agent và kỹ sư có thể:
- trả lời đúng case
- không nhầm case
- áp dụng đúng mechanism
- rút ngắn thời gian debug tại line
- giảm blind trial-and-error
