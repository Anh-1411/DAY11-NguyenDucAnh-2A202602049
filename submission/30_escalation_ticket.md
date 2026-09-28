# Escalation ticket

## Ticket 1

- **Frame:** `adasind_012570.jpg`, đối tượng `L1+M12` (`LM_noR`).
- **Ảnh chụp:** `submission/screenshots/adasind_012570-evidence.jpg`.
- **Expected impact:** nếu teaching reference thiếu vật thật thì phép so ghi nhãn người gán là spurious và làm giảm precision không đúng; quyết định rework cũng có thể xóa một nhãn hợp lệ.
- **Owner:** `qa`.
- **Recommendation:** một người QA thứ hai mở ảnh gốc và overlay, xác nhận vật có cao ≥40 px và thuộc class `Bike`; nếu đồng ý thì sửa teaching reference và chạy lại compare/local-quality. Không gọi reference là gold trước khi xác nhận.
