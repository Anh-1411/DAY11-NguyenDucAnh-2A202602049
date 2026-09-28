# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `adasind_012570.jpg` / center | 1 BOX_GEOMETRY, 2 missing theo reference, 1 LM_noR và nhiều M_only | Đây là frame duy nhất làm local quality giảm: TP=7, FP=1, FN=2; cần phân biệt lỗi người gán với lỗi reference | Ảnh gốc, `compare.html`, `model_compare.html`, tọa độ L/R/M và ảnh `submission/screenshots/adasind_012570-evidence.jpg` |
| `adasind_036720.jpg` / edge và vật nhỏ | nhiều box dưới H=40; model có 4 M_only và bỏ sót vật L/R | Méo fisheye và vật sát biên dễ gây box lỏng, bỏ sót hoặc đưa vật ngoài phạm vi vào đánh giá | Ảnh gốc, polygon lens/ego, số đo H, IoU sweep và `submission/screenshots/adasind_036720-evidence.jpg` |

Giới hạn của kết luận từ ba frame ADASIND: slice quá nhỏ, cùng một camera và teaching reference chưa phải gold set; các tỷ lệ TP/FP/FN chỉ mô tả ba frame, không đại diện toàn bộ ADASIND hay hệ thống bốn camera.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: lấy mẫu theo camera × normal/hard, giới hạn số frame liên tiếp từ cùng một cảnh và giữ ID cảnh để tránh coi các frame gần nhau là mẫu độc lập. Kế hoạch ưu tiên hard nhiều hơn để tìm lỗi hiếm; vì không lấy mẫu ngẫu nhiên theo tỷ trọng vận hành nên không dùng 200 frame này để ước lượng tỷ lệ lỗi của toàn bộ 50.000 frame.
