---
title : "Giải pháp 2: AWS Transit Gateway"
date: 2025-06-19
weight : 4
chapter : false
pre : " <b> 4. </b> "
---


#### Giới thiệu mô hình Kiến trúc sử dụng AWS Transit Gateway

**AWS Transit Gateway** (TGW) là một dịch vụ được thiết kế để đơn giản hóa việc kết nối mạng giữa nhiều **Amazon VPC** và hệ thống **on-premises**. Thay vì thiết lập kết nối **peering** riêng lẻ giữa từng **VPC** như mô hình Full Meshed, tất cả các **VPC** chỉ cần kết nối đến một **Transit Gateway** trung tâm – nơi điều phối toàn bộ lưu lượng mạng.
![AWS Support](/images/1/003.png?featherlight=false&width=90pc)
####  Cơ chế hoạt động:
**Transit Gateway** đóng vai trò như một router đám mây có khả năng định tuyến chuyển tiếp (transitive routing). Nó giúp các **VPC** kết nối gián tiếp với nhau thông qua TGW mà không cần thiết lập peering trực tiếp.
#### Ưu điểm nổi bật:
- Hỗ trợ định tuyến chuyển tiếp: Giải quyết triệt để hạn chế của **VPC Peering**.
- Tối giản số lượng kết nối: Với n VPC, chỉ cần n kết nối đến TGW thay vì n(n-1)/2 kết nối peering.
- Khả năng mở rộng cao: Thiết kế phù hợp với hệ thống lớn, multi-account và multi-region.
- Quản lý tập trung: Route table và policy có thể cấu hình tại một nơi duy nhất.

Trong phần tiếp theo của workshop, chúng ta sẽ triển khai kiến trúc này để kiểm chứng các ưu điểm thực tế về hiệu quả kết nối, độ đơn giản khi quản trị và khả năng mở rộng so với các mô hình trước đó.
#### Các bước thực hiện
1. [Tạo Transit Gateway](4-Solution-2/1-creat-transit-gateways)
2. [Tạo Transit Gateway Attachments](4-Solution-2/2-creat-transit-gateways-attachments/)
3. [Cấu Hình Transit Gateway Route Tables](4-Solution-2/3-config-transit-gateways-route-table)
4. [Cập Nhật VPC Route tables](4-Solution-2/4-config-vpc-route-table)
5. [Kiểm tra kết nối](4-Solution-2/5-check-result)