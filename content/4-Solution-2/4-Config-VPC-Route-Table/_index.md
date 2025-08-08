---
title : "Cập Nhật VPC Route tables"
date: 2025-06-19
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Cấu hình Route tables

ℹ️ **Information**: Trong phần này, bạn sẽ cập nhật lại route tables của tất cả các **VPC** chuyển sang sử dụng **Transit Gateway.**
#### Cập nhật Route Table cho Hub-vpc
1. **Đăng nhập vào VPC Management Console tại region N. Virginia (us-east-1)**
    - Mở **VPC Management Console**
    - Chọn **Route Tables**
    - Chọn **Hub-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/VPC-Peering/12.png?featherlight=false&width=90pc)

2. **Cập nhật route**.
    - Cập nhật lại **Target** cho **tất cả route** thành **Transit Gateway**
    - Chọn **Transit Gateway** đã tạo
    - Chọn **Save changes**
![alt text](/images/workshop-transit/21.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Hub-public-rt**
{{% /notice %}}
#### Cập nhật Route Table cho Management-vpc
1. **Đăng nhập vào VPC Management Console tại region N. Virginia (us-east-1)**
    - Mở **VPC Management Console**
    - Chọn **Route Tables**
    - Chọn **Management-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/workshop-full-mesh/7.png?featherlight=false&width=90pc)

2. **Cập nhật route**.
    - Cập nhật lại **Target** cho **tất cả route** thành **Transit Gateway**
    - Chọn **Transit Gateway** đã tạo
    - Chọn **Save changes**
![alt text](/images/workshop-transit/22.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Management-public-rt**
{{% /notice %}}
#### Cập nhật Route Table cho WebApp-vpc
1. **Đăng nhập vào VPC Management Console tại region N. Virginia (us-east-1)**
    - Mở **VPC Management Console**
    - Chọn **Route Tables**
    - Chọn **WebApp-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/workshop-full-mesh/9.png?featherlight=false&width=90pc)

2. **Cập nhật route**.
    - Cập nhật lại **Target** cho **tất cả route** thành **Transit Gateway**
    - Chọn **Transit Gateway** đã tạo
    - Chọn **Save changes**
![alt text](/images/workshop-transit/23.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **WebApp-public-rt**
{{% /notice %}}
#### Cập nhật Route Table cho Database-vpc
1. **Đăng nhập vào VPC Management Console tại region Oregon (us-west-2)**
    - Mở **VPC Management Console**
    - Chọn **Route Tables**
    - Chọn **Database-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/workshop-full-mesh/11.png?featherlight=false&width=90pc)

2. **Cập nhật route**.
    - Cập nhật lại **Target** cho **tất cả route** thành **Transit Gateway**
    - Chọn **Transit Gateway** đã tạo
    - Chọn **Save changes**
![alt text](/images/workshop-transit/25.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Database-public-rt**
{{% /notice %}}

