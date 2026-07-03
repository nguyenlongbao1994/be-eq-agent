# BE EQ Knowledge Base

Repository này dùng làm **knowledge base cho BE EQ troubleshooting, báo cáo, đào tạo và theo dõi tích hợp automation line**.

Mục tiêu chính:
- Lưu tri thức kỹ thuật cho dây chuyền BE
- Gom issue history, failure pattern và action logic
- Hỗ trợ phân tích cho **Watch** và **Hana**
- Làm nguồn dữ liệu để Agent/Copilot trả lời theo logic EQ thực tế

---

## 1. Main BE Process Flow

Water Clean → Baking → Plasma → Molding → Laser → Dry Ice → Plasma → CPF → Curing → Jigsaw → Tape → Sputter → AVI

---

## 2. Core Troubleshooting Principle

Phần lớn lỗi **không phải machine breakdown**.

Nguồn lỗi chính thường đến từ:
- Process instability
- Sensor / detection gap
- Mechanical wear
- System integration issue
- Human operation error
- Transfer / positioning issue

Failure chain thường gặp:

Small issue → misalignment → drop → stacking → collision → defect

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
Tóm tắt tổng quan, watch point và điều hướng

### troubleshooting.md
Lịch sử issue, symptom, mechanism, root cause, quick check, action

### knowledge_db.md
Tri thức chuẩn hóa theo station / equipment / process / automation / project

### instruction.md
Logic trả lời và tư duy troubleshooting cho Agent

---

## 6. Recommended Usage

Use this repository for:
- Daily / weekly BE EQ reporting
- Issue review and troubleshooting reference
- Training new engineers / PD support
- Watch / Hana readiness review
- Automation / SFIS integration follow-up

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

### Dry Ice / Trench Dry Ice
- Không chỉ là nozzle
- Phải nhìn cả dry ice source, CDA, vacuum, magazine, scanner, SFIS

### Jigsaw
- Lifetime control rất quan trọng
- Blade / brush / cleaning water ảnh hưởng trực tiếp đến quality

---

## 8. Current Data Rule

- Chỉ dùng dữ liệu đã được xác nhận trong note / chat / training
- Không tự suy đoán root cause nếu chưa có evidence
- Khi không có dữ liệu xác nhận, phải ghi rõ:
  - `Data not available in current knowledge`

---

## 9. Next Expansion

Possible future files:
- `watch_status.md`
- `hana_readiness.md`
- `issue_library.md`
- `.github/copilot-instructions.md`

---

## 10. Maintainer Note

This repository is intended to support practical BE EQ work:
- real line troubleshooting
- real report writing
- real automation risk follow-up
- real project readiness comparison between Watch and Hana
