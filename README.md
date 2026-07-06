# BE EQ Agent Knowledge Base

Repository này là nguồn dữ liệu chính cho **BE EQ troubleshooting, incident conversion, reporting, training và pattern analysis**.

Mục tiêu:
- Hỗ trợ kỹ sư line debug issue nhanh hơn
- Chuẩn hóa cách mô tả symptom / mechanism / root cause / action
- Dùng làm knowledge source cho Agent / Copilot
- Hạn chế trả lời generic, nhầm case, hoặc reuse dữ liệu cũ
- Hỗ trợ phân tích cho **Watch** và **Hana**

---

## 1. Repository này dùng để làm gì

Repository này không chỉ lưu issue history.  
Repository này phải giúp kỹ sư và Agent:

1. hiểu đúng **failure mechanism**
2. phân biệt **machine failure** với:
   - process instability
   - sensor / detection gap
   - interface / communication failure
   - human operation error
3. tái sử dụng **failure patterns** đã từng xảy ra
4. viết report / incident / troubleshooting note theo cùng một chuẩn
5. tránh:
   - nhầm case
   - reuse case cũ
   - lệch slug giữa incident register và file detail

---

## 2. Core BE Principle

### 2.1 Main Process Flow
Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

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

### 2.3 Typical Failure Chain
Small issue → misalignment → false clear / wrong transfer → drop / stacking / collision → defect

---

## 3. Current Watch Points

### Cold Jet #22
- Output / weight có hiện tượng tụt dưới spec
- Hướng nghi chính:
  - dry ice quality variation
  - partial nozzle freezing
  - CDA fluctuation

### Plasma 3 SFIS
- Machine-side data sending đã OK
- IT routing chưa hoàn tất
- Station chưa fully online

### Laser CT instability
- Có machine gây CT cao hơn
- Có liên quan đến vision NG / cannot detect

### Mold 147 Press 2
- Abnormal trong lúc cleaning
- Đã isolate, đang điều tra nguyên nhân

### Jigsaw
- Blade và brush phải kiểm soát theo lifetime
- Machine 58: ~700 panel / blade
- Other machines: ~500 panel / blade
- Brush: replace every 108000 runs

---

## 4. Hana Project Context

Hana đang dùng chung nhiều nguồn lực / line context với Watch.

Phân loại readiness nên theo 4 nhóm:
1. Machine available
2. Need transfer
3. Need new buy / long lead time
4. Can share with Watch but must control capacity

Điểm đã biết:
- Hầu hết machine MP đã có sẵn
- Vacuum Baking là hạng mục cần transfer
- Một số EE lab item có lead time dài

---

## 5. Repository Structure

### README.md
Tổng quan repository, governance dữ liệu, rule sử dụng và điều hướng file

### instruction.md
Rule cho Agent / Copilot:
- cách suy luận
- cách đọc case mới
- cách tránh reuse case cũ
- cách tạo incident code
- cách kiểm tra duplicate

### knowledge_db.md
Tri thức chuẩn hóa theo:
- station
- equipment / process
- failure patterns
- automation / integration
- Watch / Hana context

### troubleshooting.md
Playbook line-ready:
- quick check
- failure chain
- troubleshooting order
- report format
- incident conversion rule

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
- Automation / SFIS / interface follow-up
- Converting images / slides into incident markdown

---

## 7. Key Station Notes

### Water Clean
- Core process tương đối ổn định
- Theo dõi loader / unloader / scanner robustness

### CPF
- Rủi ro chính là glue-related instability
- FAI pass không đồng nghĩa margin đủ rộng

### Molding
- Transfer abnormal → kiểm mold side / contamination / mold incomplete
- Vacuum abnormal → ưu tiên nghi mold side
- No input > 12h → redo FAI

### Laser
- Trọng tâm kỹ thuật:
  - laser head
  - working table
  - optical path
- Có liên kết SFIS và yêu cầu cooling control
- Transfer / ULD / lift / conveyor interface là nguồn rủi ro lớn
- Out signal có thể “clear” nhưng panel chưa thật sự ra khỏi table

### Dry Ice / LT Dry Ice / Cutting Dry Ice
- Không chỉ là nozzle
- Phải nhìn cả:
  - dry ice source
  - CDA
  - vacuum
  - magazine / carrier / conveyor
  - scanner / SMD / status sync

### Jigsaw
- Lifetime control rất quan trọng
- Blade / brush / cleaning water ảnh hưởng trực tiếp đến quality
- Blade-nozzle gap và panel flatness có thể gây scratch / vision stop / dimension issue

### Sputter
- DC power / cathode / clamp / chamber contamination là pattern quan trọng
- Transmission / coupling / belt / motor / timeout cũng là recurring pattern

---

## 8. Data Governance Rules

### 8.1 Only validated data
- Chỉ dùng dữ liệu đã được xác nhận trong:
  - image
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
1. Check với case ngay trước đó
2. So machine / station / mechanism / issue chain
3. Nếu cùng machine + cùng mechanism → kiểm tra xem có phải repeat issue
4. Nếu khác machine nhưng cùng mechanism → mention “related pattern”

### 8.4 Incident Link Rule
Trong `incidents/README.md`, cột cuối luôn dùng relative link dạng:
./YYYY/YYYY-MM-DD-issuexxx.md
## 9. Agent Rules Summary
Agent phải:

đọc case mới từ đầu
không reuse machine/date/slug từ case trước
ưu tiên physical reality before system assumption
phân biệt:

Machine issue
Process issue
Sensor / false clear
Interface / no feedback
Human override / manual reset
Capacity / readiness issue

## 10. Maintainer Note
This repository is intended to support practical BE EQ work:

real line troubleshooting
real report writing
real automation risk follow-up
real project readiness comparison between Watch and Hana
incident standardization for Agents
