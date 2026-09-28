# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Không tự coi là `DUPLICATE`; cần policy cross-camera riêng vì hai box có thể là hai quan sát hợp lệ của cùng vật. Chỉ hợp nhất sau khi có camera ID, timestamp, calibration và bằng chứng chiếu qua vùng overlap/seam.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Giữ cùng track ID khi còn cùng vật trong một camera và nội suy giữa các keyframe vẫn hợp lý; thêm keyframe khi hình học/thuộc tính đổi, và đặt Outside ở frame đầu vật không còn hiện diện. Qua hai camera cần timestamp đồng bộ, calibration, overlap/seam policy và bằng chứng nhận dạng/chuyển động; không nối chỉ vì hai box gần nhau.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Ở `adasind_012570.jpg`, `L1+M12` xuất hiện trong learner/model nhưng teaching reference không có. Tôi giữ nhãn với lý do, đánh dấu `E0_reference_defect` và escalate cho QA thay vì xóa theo reference. Nếu làm lại, tôi sẽ đo H ngay trên ảnh gốc, kiểm từng vật theo thứ tự trái-sang-phải và lưu screenshot trước khi khóa để giảm tranh luận sau QA.
