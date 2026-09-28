# QA review · B3-mid

Mã khóa: 9010-7D53

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_128310.jpg | L5 | R04 | Đối tượng tại khoảng `(340,942)-(396,997)` có hình dáng xe ba bánh/auto-rickshaw nhưng đang gán `Car`; cần đổi sang `ThreeWheeler` nếu ảnh gốc xác nhận. |
| adasind_128310.jpg | L6 | R09 | Box `Truck` ở mép trái chồng mạnh với vùng người/ego và box `Pedestrian`; cần kiểm phần diện tích nằm trong `ego_body` và xác nhận đây có thật là một xe tải riêng hay không. |
| adasind_140160.jpg | L2 | R01 | Box `Bike` cao khoảng 28.3 px, dưới ngưỡng H=40 nên không thuộc phạm vi bắt buộc và theo R01 không nên có box. |
| adasind_140160.jpg | L3 | R01 | Box `Truck` cao khoảng 23.1 px, dưới H=40; đồng thời nằm gần như bên trong box `Truck` L4 nên cần kiểm khả năng gán trùng cùng một vật. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
