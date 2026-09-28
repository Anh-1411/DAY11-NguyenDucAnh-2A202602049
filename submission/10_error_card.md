# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B1 | BOX_GEOMETRY | 1 |
| center | B1 | MISSING | 5 |
| center | B1 | SPURIOUS | 10 |
| center | B3 | DUPLICATE | 1 |
| center | B3 | WRONG_CLASS | 1 |
| edge | B1 | MISSING | 2 |
| edge | B1 | SPURIOUS | 4 |
| edge | B3 | IGNORE_SCOPE | 1 |
| mid | B1 | MISSING | 3 |
| mid | B1 | SPURIOUS | 1 |
| mid | B3 | SPURIOUS | 1 |

## Top defects
- SPURIOUS: 16 (ví dụ frame adasind_036720.jpg)
- MISSING: 10 (ví dụ frame adasind_012570.jpg)
- BOX_GEOMETRY: 1 (ví dụ frame adasind_012570.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: `SPURIOUS` nổi bật chủ yếu do model có nhiều `M_only` và một số box learner dưới H=40; mẫu lặp lại ở cả ba frame hỗ trợ giả thuyết `E4_model_domain`, nhưng các ca learner vẫn phải xem riêng theo R01. `MISSING` tập trung ở center, gồm lỗi model và hai ca learner thiếu trong `adasind_012570.jpg`.
- Cách sửa và ai nhận việc (`owner`): annotator rework hai ca P1 thiếu theo reference; QA xác nhận ca `L1+M12` trước khi sửa teaching reference; `ai_team` phân tích M_only/LR_noM theo zone và không biến model thành ground truth.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `submission/screenshots/adasind_012570-evidence.jpg`, `submission/screenshots/adasind_036720-evidence.jpg`, các dòng `r3_diag` trong `findings.csv`, R01/R02 và `r3_diag/model_compare.html`.
