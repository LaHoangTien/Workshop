---
title : "Giải Pháp 1: Fully Meshed Peering"
date: 2025-06-19
weight : 3
chapter : false
pre : " <b> 3. </b> "
---
#### Giới thiệu mô hình Kiến trúc **Fully Meshed Peering**
Mô hình **Full Meshed** là một kiến trúc mạng trong đó mọi **VPC** đều được kết nối trực tiếp với nhau thông qua các **VPC Peering** riêng biệt. Kiến trúc này loại bỏ hoàn toàn sự phụ thuộc vào một **VPC** trung tâm như trong mô hình **Hub-and-Spoke**, giúp đảm bảo rằng mọi **VPC** đều có thể giao tiếp với nhau mà không bị giới hạn bởi định tuyến chuyển tiếp.

Trong môi trường **Cloud**, đặc biệt là với **AWS**, mô hình **Full Meshed** thường được áp dụng khi cần:
- Kết nối trực tiếp, hai chiều giữa các dịch vụ phân bố trong nhiều **VPC**.
- Tối ưu hóa độ trễ và luồng dữ liệu, tránh đi qua trung gian.
- Tăng tính sẵn sàng, không bị phụ thuộc vào một **VPC** trung tâm.

Tuy nhiên, mô hình này cũng có những nhược điểm nhất định:
- Độ phức tạp quản trị tăng theo cấp số nhân khi số lượng **VPC** tăng (n VPC sẽ cần n(n-1)/2 kết nối peering).
- Khó mở rộng khi áp dụng cho môi trường lớn hoặc đa vùng **(multi-region)**.
- Tăng rủi ro bảo mật, do mọi **VPC** đều có thể trực tiếp truy cập lẫn nhau nếu không cấu hình đúng **Security Group** và **Route Table**.
![Hub-and-Spoke Diagram](/images/1/002.png?featherlight=false&width=90pc)
#### Các bước thực hiện
1. [Tạo kết nối Peering](3-Solution-1/1-Creat-VPC-Peering)
2. [Cấu hình Route tables](3-Solution-1/2-Route-Tables)
3. [Kiểm tra kết nối](3-Solution-1/3-Check-Result)