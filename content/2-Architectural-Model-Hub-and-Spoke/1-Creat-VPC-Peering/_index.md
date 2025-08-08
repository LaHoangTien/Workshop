---
title : "Tạo kết nối Peering"
date: 2025-06-19
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Tạo kết nối Peering

ℹ️ **Information**: Ở Bước này, bạn sẽ tạo kết nối **VPC Peering (VPC Peering Connection)**.
- **WebApp ↔ Hub**
- **Management ↔ Hub**
- **Hub ↔ Database**

💡 **Pro Tip**: **VPC Peering** cho phép các tài nguyên trong hai **VPC** khác nhau giao tiếp với nhau như thể chúng đang nằm trong cùng một mạng.

1. **Đăng nhập vào AWS Management Console**
      - Tìm **VPC**
      - Chọn **VPC**
![alt text](/images/VPC-Peering/1.png?featherlight=false&width=90pc)

2. **Trong giao diện VPC**.
      - Chọn **Peering Connections**
      - Chọn **Create Peering Connection**
![alt text](/images/VPC-Peering/2.png?featherlight=false&width=90pc)

3. **Trong giao diện Create Peering Connection**
      - Nhập **Name** `Hub-to-WebApp`
      - Chọn **VPC ID (Requester)** Hub-vpc
      - Chọn **My account**
      - Chọn **This Region (us-east-1)**
      - Chọn **VPC ID (Accepter)** Web-App-vpc
      - Chọn **Creat peering connection**
![alt text](/images/VPC-Peering/3.png?featherlight=false&width=90pc)

4. **Accept request cho Peering Connection**
      - Chọn **Actions**
      - Chọn **Accept request**
![alt text](/images/VPC-Peering/4.png?featherlight=false&width=90pc)

5. **Tiếp tục lập lại các bước trên với `Hub-to-Management`**
![alt text](/images/VPC-Peering/5.png?featherlight=false&width=90pc)
      - Chọn **Actions**
      - Chọn **Accept request**

6. **Tiếp tục tạo Peering Cross-region giữa Hub và Database**.

      6.1. Lấy **ID Database-vpc**.
      - Chuyển sang region **Oregon (us-west-2)**
      - Chọn **Your VPC**
      - Copy **VPC ID Database-vpc**
![alt text](/images/VPC-Peering/7.png?featherlight=false&width=90pc)

      6.2. Tạo **Peering Cross-region**.
      - Quay về **N. Virginia (us-east-1)**
      - Chọn **Peering Connections**
      - Chọn **Create Peering Connection**
![alt text](/images/VPC-Peering/6.png?featherlight=false&width=90pc)
      - Nhập **Name** `Hub-to-Database-CrossRegion`
      - Chọn **VPC ID (Requester)** Hub-vpc
      - Chọn **My account**
      - Chọn **Another Region**
      - Chọn **Oregon (us-west-2)**
      - Dán **VPC ID Database-vpc** đã copy từ **Oregon (us-west-2)**
      - Chọn **Creat peering connection**
![alt text](/images/VPC-Peering/8.png?featherlight=false&width=90pc)

      6.3. Accept request cho **Hub-to-Database-CrossRegion**.
      - Chuyển sang region **Oregon (us-west-2)**
      - Chọn **Actions**
      - Chọn **Accept request**
![alt text](/images/VPC-Peering/9.png?featherlight=false&width=90pc)    
7. **Kiểm tra kết quả.**
      - Quay về **N. Virginia (us-east-1)**, sẽ thấy 3 Peering Connection được tạo.

![alt text](/images/VPC-Peering/10.png?featherlight=false&width=90pc)
