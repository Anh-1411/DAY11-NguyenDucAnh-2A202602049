# Tự soát

- adasind_001320.jpg L7: chiều cao < H (xem lại phạm vi)
- adasind_012570.jpg L2: chiều cao < H (xem lại phạm vi)
- adasind_012570.jpg L9: chiều cao < H (xem lại phạm vi)
- adasind_012570.jpg L10: chiều cao < H (xem lại phạm vi)
- adasind_036720.jpg L4: chiều cao < H (xem lại phạm vi)
- adasind_036720.jpg L5: chiều cao < H (xem lại phạm vi)
- adasind_036720.jpg L6: chiều cao < H (xem lại phạm vi)
- adasind_036720.jpg L8: chiều cao < H (xem lại phạm vi)
- adasind_036720.jpg L9: chiều cao < H (xem lại phạm vi)
- Tên task thiếu raw_fisheye

**Kết quả xem xét:** đã kiểm trực tiếp trong CVAT ngày 2026-09-28. Tên task hiện tại là `Day11 · ADASIND · B1-dense · raw_fisheye`. Các box có chiều cao dưới H=40 đã được xem xét và quyết định giữ nguyên theo yêu cầu của học viên; cần giải thích quyết định này nếu QA đặt câu hỏi.

## Checklist thủ công
- [x] Phạm vi H=40 và vật cần vẽ
- [x] lens_border và ego_body
- [x] Class sáu nhãn
- [x] Rider và Bike
- [x] Geometry trên ảnh fisheye gốc
- [x] truncated và occluded
- [x] Vật thiếu hoặc box trùng
- [x] ignore_region có reason
- [x] Tên task raw_fisheye và export CVAT 1.1

