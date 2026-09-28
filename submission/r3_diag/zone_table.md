# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 9 | 1 | 1 | 3 | 7 | BOX_GEOMETRY (1) |
| mid | 7 | 0 | 0 | 3 | 1 | — |
| edge | 3 | 0 | 0 | 2 | 4 | — |

## Nhận xét

- Người gán nhãn (L) gãy nhiều nhất ở `center`: thiếu 2 và thừa 1; `mid` và `edge` không có lỗi L theo bảng. Model (M) cũng gãy nhiều nhất ở `center`, với 3 thiếu và 7 thừa; ở `mid` là 3 thiếu/1 thừa và ở `edge` là 2 thiếu/4 thừa.
- Giả thuyết chính là model đóng băng không thích nghi tốt với ảnh fisheye, các vật nhỏ/chồng lấp và phần ảnh gần vùng ignore; hiện tượng M thiếu/thừa lặp lại ở cả ba frame và nhiều zone. Riêng khác biệt L tại `center` có thể do box chưa khớp hình học và hai vật bị bỏ sót theo teaching reference. Kết luận chỉ dựa trên ba frame của một slice, teaching reference chưa phải gold set và kết quả thay đổi theo IoU (ở center, L matched giảm từ 8 tại IoU 0.30 xuống 6 tại 0.70), nên chưa đủ để suy rộng sang toàn bộ dữ liệu hay hệ thống bốn camera.
