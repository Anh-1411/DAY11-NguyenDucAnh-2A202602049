# Guideline patch

- **Rule mới đề xuất:** bổ sung quy trình đo H=40 trên ảnh gốc: dùng chiều cao phần nhìn thấy của box sau khi bám sát vật, không tính phần suy đoán bị che; giá trị dưới 40 px không tạo box, trường hợp sát ngưỡng 39–41 px phải ghi bằng chứng đo và để QA xác nhận.
- **Áp dụng cho:** mọi rectangle thuộc sáu class, đặc biệt vật nhỏ ở `center`/`mid` và vật bị che.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R01 nêu ngưỡng nhưng chưa mô tả cách đo ca bị che hoặc cách xử lý sai số sát ngưỡng. Slice B1-dense có nhiều box 19–39.6 px và dẫn đến quyết định giữ/xóa không nhất quán.
- **`rules_version` mới:** v1.0.0 → v1.1.0.
- **Hiệu lực từ:** vòng gán nhãn tiếp theo sau khi Lab Coach duyệt; không áp dụng hồi tố cho bản đã khóa.
