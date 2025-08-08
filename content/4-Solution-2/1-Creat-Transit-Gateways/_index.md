---
title : "Tạo Transit Gateway"
date: 2025-06-19
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

#### Tạo Transit gateways

ℹ️ **Information**: Trong phần này, bạn sẽ tạo một AWS Transit Gateway để làm hub trung tâm kết nối các VPC.

#### Tạo Transit gateways cho region **N. Virginia (us-east-1)**
1. **Đăng nhập vào AWS Management Console tại region N. Virginia (us-east-1)**
    - Tìm **VPC**
    - Chọn **VPC**
![alt text](/images/VPC-Peering/1.png?featherlight=false&width=90pc)

2. **Trong giao diện VPC**.
    - Chọn **Transit gateways**
    - Chọn **Create transit gateway**
![alt text](/images/workshop-transit/3.png?featherlight=false&width=90pc)

3. Trong giao diện **Create transit gateway**
    - Nhập **Name** `TGW-east`
    - Nhập **Desciption** `TGW-east`
    - Nhập **ASN**  ` 64512`
    - Tick chọn như hình
    - Chọn **Creat transit gateway**
![alt text](/images/workshop-transit/4.png?featherlight=false&width=90pc)
#### Tạo Transit gateways cho region **Oregon (us-west-2)**
1. **Trong giao diện VPC**.
    - Chuyển sang region **Oregon (us-west-2)**
    - Chọn **Transit gateways**
    - Chọn **Create transit gateway**
![alt text](/images/workshop-transit/5.png?featherlight=false&width=90pc)

2. **Trong giao diện Create transit gateway**
    - Nhập **Name** `TGW-west`
    - Nhập **Desciption** `TGW-west`
    - Nhập **ASN**  ` 64513`
    - Tick chọn như hình
    - Chọn **Creat transit gateway**
![alt text](/images/workshop-transit/6.png?featherlight=false&width=90pc)


