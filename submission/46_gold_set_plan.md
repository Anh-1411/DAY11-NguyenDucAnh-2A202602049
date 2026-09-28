# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Vật xa, chồng lấp, ngược sáng và vật đi vào seam hai góc trước | Box nhỏ và méo làm giảm IoU; cùng vật có thể xuất hiện ở camera bên | Giữ ảnh raw từng camera, calibration nội tại/ngoại tại, timestamp và cả nhãn trong image space; BEV chỉ là sản phẩm dẫn xuất | Hai annotator độc lập, QA phân xử, kiểm calibration và xác nhận từng hard case trước khi đóng phiên bản |
| rear | Xe áp sát, vật bị ego che, vật rời trường nhìn | Truncated/occluded dễ nhầm và phần thân xe có thể che vật | Giữ raw rear, lens mask, ego mask, timestamp và transform sang hệ xe | Double review các ca sát biên; kiểm lại trên chuỗi frame trước/sau rồi sign-off |
| left | Xe hai bánh/người đi bộ sát curb và seam trước-trái/sau-trái | Méo fisheye mạnh, vật mảnh và giao cắt seam | Giữ image-space box/polygon, camera ID, calibration version và liên kết ứng viên cross-camera | Soát ảnh từng camera trước, sau đó so cặp seam bằng timestamp và hình học chiếu |
| right | Curb, người đi bộ, xe máy và vật bị cắt ở hai seam phải | Dễ bỏ sót vật nhỏ hoặc đếm đôi giữa camera | Giữ raw right, ignore regions, timestamp, calibration và provenance người sửa | Peer agreement rồi QA phân xử; không tự động hợp nhất chỉ vì hai box gần nhau trong BEV |

- Khi nào cần refresh gold set: khi đổi camera/lens/vị trí lắp, cập nhật calibration, thay annotation space hoặc rules version, thay miền vận hành đáng kể, hay drift làm hard-case coverage không còn phù hợp.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: phải có camera IDs, timestamp đồng bộ, calibration cùng phiên bản, vùng overlap hợp lệ và bằng chứng chiếu về cùng vị trí/vật trong hệ xe; hai box giống nhau bằng mắt chưa đủ.
- Peer agreement hoặc quality report trên một camera chỉ kiểm tính nhất quán trong image space của camera đó; nó không kiểm đồng bộ thời gian, calibration, seam policy hay lỗi ghép/đếm đôi giữa bốn camera.
