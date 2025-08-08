---
title : "Cấu Hình Transit Gateway Route Tables"
date: 2025-06-19
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Tổng quan Transit Gateway về Route Tables

ℹ️ **Information**: Trong phần này, bạn sẽ cấu hình **Route Table** cho **Transit Gateway** để quản lý luồng **traffic** giữa các **VPC**.
#### Cấu hình Transit Gateway Route Table tại region N. Virginia (us-east-1)
📌 **Mục đích**: Cho phép VPC ở **us-east-1** định tuyến traffic tới Database VPC qua TGW peering.
1. **Đăng nhập vào VPC Management Console tại region N. Virginia (us-east-1)**
    - Mở **VPC Management Console**
    - Chọn **Transit Gateway Route Tables**
    - Chọn **Route Tables** đã được tạo từ **Transit Gateway**
    - Chọn tab **Routes**
    - Chọn **Creat static route**.
![alt text](/images/workshop-transit/17.png?featherlight=false&width=90pc)

2. **Tạo Static route**.
    - **CIDR**: `10.2.0.0/16` CIDR block của Database-vpc
    - **Choose attachment**: Chọn attachment **TWG-Peering-East-West**
    - Chọn **Creat static route**
![alt text](/images/workshop-transit/18.png?featherlight=false&width=90pc)
#### Cấu hình Transit Gateway Route Table tại region Oregon (us-west-2)
📌 Mục đích: Cho phép Database-vpc định tuyến traffic tới VPC trong **us-east-1** qua TGW peering.
1. **Chuyển sang Oregon (us-west-2)**
    - Chọn **Route Tables** đã được tạo từ **Transit Gateway**
    - Chọn tab **Routes**
    - Chọn **Creat static route**.
![alt text](/images/workshop-transit/19.png?featherlight=false&width=90pc)

2. **Tạo Static route**.
    - **CIDR**: `10.1.0.0/16` CIDR block của WebApp-vpc
    - **Choose attachment**: Chọn attachment **TWG-Peering-East-West**
    - Chọn **Creat static route**
![alt text](/images/workshop-transit/20.png?featherlight=false&width=90pc)

3. **Tặp lại các bước cho CIDR block của Hub-vpc `10.0.0.0/16` và Management-vpc `10.3.0.0/16`**.
{{% notice note %}}
✅ Đây là phần quan trọng để đảm bảo **kết nối 2 chiều hoạt động** trong kiến trúc multi-region!
{{% /notice %}}
