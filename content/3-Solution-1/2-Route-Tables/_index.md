---
title : "Cập nhật Route tables"
date: 2025-06-19
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Cấu hình Route tables

ℹ️ **Information**: Trong phần này, ta sẽ chỉ cập nhật **Route Table** cho **Management-vpc**, **WebApp-vpc**, **Database-vpc** vì **Hub-vpc** đã được cấu hình trực tiếp đến 3 **VPC** còn lại
#### Cập nhật Route Table cho Management-vpc
1. **Mở VPC Management Console tại N. Virginia (us-east-1)**
    - Chọn **Route Tables**
    - Chọn **Management-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/workshop-full-mesh/7.png?featherlight=false&width=90pc)

2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/workshop-full-mesh/8.png?featherlight=false&width=90pc)

{{% notice note %}}
Lặp lại các bước với **Management-public-rt**
{{% /notice %}}
#### Cấu hình Route Table cho Webapp-vpc
1. **Mở VPC Management Console tại N. Virginia (us-east-1)**
    - Chọn **Route Tables**
    - Chọn **Webapp-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/workshop-full-mesh/9.png?featherlight=false&width=90pc)
2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/workshop-full-mesh/10.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Webapp-public-rt**
{{% /notice %}}
#### Cấu hình Route Table cho Database-vpc
1. **Mở VPC Management Console tại Oregon (us-west-2)**
    - Chọn **Route Tables**
    - Chọn **Database-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/workshop-full-mesh/11.png?featherlight=false&width=90pc)
2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/workshop-full-mesh/12.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Database-public-rt**
{{% /notice %}}

