# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ: chưa thể xác nhận vì `submission/parking/annotations.xml` chưa có trong repo.
- Một vạch/dấu sơn hoặc biên không vẽ: không coi mép cỏ/vỉa hè trong ảnh đối chiếu là `parking_line`, vì đó không phải vạch sơn phân chia từng ô đỗ.
- Polygon `free_space`: chưa thể xác nhận hình học khi chưa có XML; khi làm lại phải dừng tại curb, xe, cây và vùng bị che, không xuyên qua các vật này.
- Ca chưa chắc cần hỏi người soát: cần hỏi lại vị trí hai vạch trên ảnh core và export lại đúng task chỉ chứa `parking-lot-core.jpg`.
