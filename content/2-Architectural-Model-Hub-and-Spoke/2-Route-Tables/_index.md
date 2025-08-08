---
title : "Cấu hình Route tables"
date: 2025-06-19
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Cấu hình Route tables

ℹ️ **Information**: Trong phần này, bạn sẽ cấu hình **Route Table** cho từng **VPC**.

⚠️ **Warning**: Chúng ta có tổng cộng **8 Route Table** ( 6 từ region **N. Virginia (us-east-1)** và 2 từ **Oregon (us-west-2)**), Các **Route Table** được đặt theo tên **VPC** để dễ theo dõi và hãy đảm bảo thực hiện đầy đủ các bước kiểm tra để xác nhận kết nối hoạt động chính xác.

Region **N. Virginia (us-east-1)**
- **Hub-private-rt, Hub-public-rt** = Route Table của **Hub-vpc**
- **Management-private-rt, Management-public-rt** = Route Table của **Management-vpc**
- **WebApp-private-rt, WebApp-public-rt** = Route Table của **WebApp-vpc**
![alt text](/images/VPC-Peering/11.png?featherlight=false&width=90pc)

Region **Oregon (us-west-2)**
- **Database-private-rt, Database-public-rt** = Route Table của **Database-vpc**
![alt text](/images/VPC-Peering/20.png?featherlight=false&width=90pc)
#### Cấu hình Route Table cho Hub-vpc
1. **Chọn Route Table**.
    - Mở **VPC Management Console** tại **N. Virginia (us-east-1)**
    - Chọn **Route Tables**
    - Chọn **Hub-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/VPC-Peering/12.png?featherlight=false&width=90pc)

2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/VPC-Peering/13.png?featherlight=false&width=90pc)
3. **Xác nhận route**
    - Kiểm tra route mới đã được thêm
![alt text](/images/VPC-Peering/14.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Hub-public-rt**
{{% /notice %}}
#### Cấu hình Route Table cho Management-vpc
1. **Chọn Route Table**.
    - Mở **VPC Management Console** tại **N. Virginia (us-east-1)**
    - Chọn **Route Tables**
    - Chọn **Management-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/VPC-Peering/15.png?featherlight=false&width=90pc)
2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/VPC-Peering/16.png?featherlight=false&width=90pc)
3. **Xác nhận route**
    - Kiểm tra route mới đã được thêm
![alt text](/images/VPC-Peering/17.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Management-public-rt**
{{% /notice %}}
#### Cấu hình Route Table cho Webapp-vpc
1. **Chọn Route Table**.
    - Mở **VPC Management Console** tại **N. Virginia (us-east-1)**
    - Chọn **Route Tables**
    - Chọn **Webapp-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/VPC-Peering/18.png?featherlight=false&width=90pc)
2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/VPC-Peering/19.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Webapp-public-rt**
{{% /notice %}}
#### Cấu hình Route Table cho Database-vpc
1. **Chọn Route Table**.
    - Mở **VPC Management Console** tại **Oregon (us-west-2)**
    - Chọn **Route Tables**
    - Chọn **Database-private-rt**
    - Nhấn **Edit routes**
![alt text](/images/VPC-Peering/21.png?featherlight=false&width=90pc)
2. **Thêm route**.
    - Chọn **Add route**
    - Cấu hình **Destination** và **Target** theo ảnh
    - Chọn **Save changes**
![alt text](/images/VPC-Peering/22.png?featherlight=false&width=90pc)
{{% notice note %}}
Lặp lại các bước với **Database-public-rt**
{{% /notice %}}
#### Kiểm tra cấu hình **Security Group**
1. **Kiểm tra Database-SG**
    - Chỉ cho phép **SSH** từ máy **Management**
![alt text](/images/VPC-Peering/26.png?featherlight=false&width=90pc)
2. **Kiểm tra Webapp-SG** 
    - Chỉ cho phép **SSH** từ máy **Management**
![alt text](/images/VPC-Peering/23.png?featherlight=false&width=90pc)
3. **Kiểm tra Management-SG** 
    - Chỉ cho phép **SSH** từ IP của bạn
![alt text](/images/VPC-Peering/24.png?featherlight=false&width=90pc)
4. **Kiểm tra **Hub-SG** 
    - Chỉ cho phép **SSH** từ máy **Management**
![alt text](/images/VPC-Peering/25.png?featherlight=false&width=90pc)
