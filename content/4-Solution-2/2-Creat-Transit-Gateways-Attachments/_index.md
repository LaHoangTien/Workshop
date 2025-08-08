---
title : "Tạo Transit Gateway Attachments"
date: 2025-06-19
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Tạo Transit Gateway Attachments

ℹ️ **Information**: Trong phần này, bạn sẽ cấu hình các **Transit Gateway Attachments** để kết nối các **VPC** với **Transit Gateway** đã tạo.
#### Tạo Transit Gateway Attachments Peering-East-West
1. **Đăng nhập vào VPC Management Console tại region N. Virginia (us-east-1)**
    - Mở **VPC Management Console**
    - Chọn **Transit Gateway Attachments**
    - Chọn **Create Transit Gateway Attachment**
![alt text](/images/workshop-transit/7.png?featherlight=false&width=90pc)

2. **Cấu hình Transit Gateway Attachment**.
    - **Name Tag**: `TGW-Peering-East-West`
    - **Transit Gateway ID**: Chọn ID của Transit Gateway đã tạo
    - **Attachment type**: Chọn Peering Connection
    - **Account**: Chọn My Account
    - **Region**: Chọn Oregon (us-west-2)
    - Chọn **Transit Gateway** của Oregon (us-west-2)
    - Chọn **Create transit gateway attachment**
![alt text](/images/workshop-transit/8.png?featherlight=false&width=90pc)

3. **Xác thực Transit Gateway Attachment**
    - Chuyển sang **Oregon (us-west-2)**
    - Chọn **Attachments** vừa tạo
    - Chọn **Actions**
    - Chọn **Accept transit gateway attachment**
![alt text](/images/workshop-transit/10.png?featherlight=false&width=90pc)

{{% notice note %}}
Vì đây là **Attachment Peering** giữa **N. Virginia (us-east-1)** và **Oregon (us-west-2)** Nên cần xác thực **Attachment**
{{% /notice %}}
#### Tạo Transit Gateway Attachments Database
1. **Tạo Transit Gateway Attachments Database tại region Oregon (us-west-2)**.
    - Ở lại region **Oregon (us-west-2)**
    - Chọn **Create Transit Gateway Attachment**
![alt text](/images/workshop-transit/12.png?featherlight=false&width=90pc)

2. **Cấu hình Transit Gateway Attachment**.
    - **Name Tag**: `Database-TGW-Attachment`
    - **Transit Gateway ID**: Chọn ID của Transit Gateway đã tạo 
    - **Attachment type**: Chọn VPC
    - Chọn **DNS support**
    - Chọn **Security Group Referencing support**
    - Chọn **VPC ID** Database-vpc
    - Chọn **Create transit gateway attachment**
![alt text](/images/workshop-transit/13.png?featherlight=false&width=90pc)

#### Tạo Transit Gateway Attachments Hub
1. **Tạo Transit Gateway Attachments Hub tại region N. Virginia (us-east-1)**.
    - Quay về region **N. Virginia (us-east-1)**
    - Chọn **Create Transit Gateway Attachment**
![alt text](/images/workshop-transit/14.png?featherlight=false&width=90pc)

2. **Cấu hình Transit Gateway Attachment**.
    - **Name Tag**: `Hub-TGW-Attachment`
    - **Transit Gateway ID**: Chọn ID của Transit Gateway đã tạo 
    - **Attachment type**: Chọn VPC
    - Chọn **DNS support**
    - Chọn **Security Group Referencing support**
    - Chọn **VPC ID** Hub-vpc
    - Chọn **Create transit gateway attachment**
![alt text](/images/workshop-transit/15.png?featherlight=false&width=90pc)
#### Tạo Transit Gateway Attachments WebApp và Management
1. **Lặp lại các bước tạo Tạo Transit Gateway Attachments Hub cho `WebApp-TGW-Attachment` và `Management-TGW-Attachment`**
![alt text](/images/workshop-transit/16.png?featherlight=false&width=90pc)
