# Quan sát vạch ô đỗ

- Các `parking_line` nằm trên các đoạn sơn trắng phân chia ô đỗ ở tiền cảnh và vùng giữa ảnh core; export hiện có 28 polyline, nhiều hơn mức tối thiểu hai vạch.
- Không coi mép bãi, hàng rào hoặc biên giữa mặt đường và phần ngoài bãi là `parking_line`, vì chúng không phải vạch sơn phân chia từng ô đỗ. Ảnh contrast đã được loại khỏi bản nộp.
- Polygon `free_space` bao phần asphalt trống nhìn thấy ở nửa dưới ảnh core, dừng trước dải xa có chiếc xe đỏ và không đi vào vùng ngoài mặt đường.
- Ca chưa chắc cần hỏi người soát: cần soát lại bằng mắt 28 polyline để bảo đảm không có vạch dừng, mép đường hoặc dấu sơn khác bị gán nhầm thành vạch chia ô.
