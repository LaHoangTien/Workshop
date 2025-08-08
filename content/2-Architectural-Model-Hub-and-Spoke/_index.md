---
title : "Mô hình kiến trúc: Hub-and-Spoke"
date: 2025-06-19
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Giới thiệu mô hình Kiến trúc Hub-and-Spoke

Mô hình **Hub-and-Spoke** là một kiến trúc mạng phổ biến được áp dụng rộng rãi trong môi trường **Cloud** để tổ chức, phân tách và kiểm soát lưu lượng mạng giữa các hệ thống. Trong kiến trúc này, một **VPC** trung tâm được gọi là **Hub** đóng vai trò làm điểm điều phối chính, trong khi các **VPC** còn lại được gọi là **Spoke**, kết nối trực tiếp với **Hub** nhưng không kết nối ngang hàng với nhau.

Trong workshop này, mô hình được áp dụng với:
- **Hub VPC**: Trung tâm định tuyến và giám sát lưu lượng.
- **WebApp VPC**: Mô phổng chạy ứng dụng frontend.
- **Management VPC**: Truy cập quản trị và vận hành.
- **Database VPC** (khác vùng - cross-region): Lưu trữ dữ liệu backend.

![Hub-and-Spoke Diagram](/images/1/001.png?featherlight=false&width=90pc)
#### Các bước thực hiện
1. [Tạo kết nối Peering](2-Architectural-Model-Hub-and-Spoke/1-Creat-VPC-Peering)
2. [Cấu hình Route tables](2-Architectural-Model-Hub-and-Spoke/2-Route-Tables)
3. [Kiểm tra kết nối](2-Architectural-Model-Hub-and-Spoke/3-Check-Result)