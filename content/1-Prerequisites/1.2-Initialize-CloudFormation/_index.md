---
title : "Khởi tạo CloudFormation Template"
date: 2025-06-19
weight : 2
chapter : false
pre : " <b> 1.2 </b> "
---

{{% notice tip %}}
Trước hết bạn phải tải [CloudFormation Template](https://github.com/LaHoangTien/AWS-Workshop/archive/refs/heads/main.zip) và tiến hành giải nén.
{{% /notice %}}
#### Khởi tạo Stack cho region **Oregon (us-west-2)**
1. **Vẫn ở region Oregon (us-west-2) truy cập đến CloudFormation Management Conole bằng cách gõ CloudFormation vào thanh tìm kiếm**.
![alt text](/images/Initialize-CloudFormation/1.png?featherlight=false&width=90pc)

2. **Trong giao diện CloudFormation**
    - Chọn **Stacks**
    - Chọn **Create stack**
![alt text](/images/Initialize-CloudFormation/2.png?featherlight=false&width=90pc)

3. **Trong giao diện Create stack**
    - Chọn **Choose an existing template**
    - Chọn **Upload a template file**
    - Chọn **Choose file** chọn **vpc-peering-database-template.yaml** từ file đã tải về trước đó
    - Chọn **Next**
![alt text](/images/Initialize-CloudFormation/3.png?featherlight=false&width=90pc)

4. **Trong trang Specify stack details**
    - Nhập tên stack `FCJ-Workshop-West`
    - Chọn **Instance type**
    - Chọn **Keypair** của bạn
    - Chọn **Next**
![alt text](/images/Initialize-CloudFormation/4.png?featherlight=false&width=90pc)
    - Tiếp tục **Next** và chọn **Submit**
5. **Khởi tạo stack FCJ-Workshop-West thành công**
![alt text](/images/Initialize-CloudFormation/5.png?featherlight=false&width=90pc)

6. **Kiểm tra EC2 Intances**
    - Nhập **EC2** trên thanh tìm kiếm
    - Chọn **EC2**
![alt text](/images/Initialize-CloudFormation/6.png?featherlight=false&width=90pc)

7. **Trong giao diện EC2**
    - Chọn **Intances** sẽ thấy **Database-Server** đã được tạo
![alt text](/images/Initialize-CloudFormation/7.png?featherlight=false&width=90pc)
#### Khởi tạo Stack cho region **N. Virginia (us-east-1)**
1. **Chuyển sang region N. Virginia (us-east-1) truy cập đến CloudFormation Management Conole**
![alt text](/images/Initialize-CloudFormation/8.png?featherlight=false&width=90pc)

2. **Trong giao diện CloudFormation**
    - Chọn **Stacks**
    - Chọn **Create stack**
![alt text](/images/Initialize-CloudFormation/9.png?featherlight=false&width=90pc)

3. **Trong giao diện Create stack**
    - Chọn **Choose an existing template**
    - Chọn **Upload a template file**
    - Chọn **Choose file** chọn **vpc-peering-main-template.yaml** từ file đã tải về trước đó
    - Chọn **Next**
![alt text](/images/Initialize-CloudFormation/10.png?featherlight=false&width=90pc)

4. **Trong trang Specify stack details**
    - Nhập tên stack `FCJ-Workshop-East`
    - Chọn **Keypair** của bạn
    - Nhập **IP SSH của bạn** *(là IP máy của bạn dùng để truy cập vào máy ảo)*
    - Chọn **Next**
![alt text](/images/Initialize-CloudFormation/11.png?featherlight=false&width=90pc)
{{% notice tip %}}
Mở **Command Prompt** trên máy bạn và nhập `curl ipinfo.io/ip` để lấy **IP SSH access**
{{% /notice %}}
![alt text](/images/Initialize-CloudFormation/myip.png?featherlight=false&width=90pc)
    - Tiếp tục **Next** và chọn **Submit**
5. **Khởi tạo stack FCJ-Workshop-East thành công**
![alt text](/images/Initialize-CloudFormation/12.png?featherlight=false&width=90pc)

6. **Tiếp tục tạo stack thứ 2 cho region N. Virginia (us-east-1)**
    - Chọn **Create stack**
    - Chọn **With new resources (standard)**
![alt text](/images/Initialize-CloudFormation/12.1.png?featherlight=false&width=90pc)
7. **Trong giao diện Create stack**
    - Chọn **Choose an existing template**
    - Chọn **Upload a template file**
    - Chọn **Choose file** chọn **vpc-peering-instances-template.yaml** từ file đã tải về trước đó
    - Chọn **Next**
![alt text](/images/Initialize-CloudFormation/13.png?featherlight=false&width=90pc)

8. **Trong trang Specify stack details**
    - Nhập tên stack `FCJ-Workshop-East-2`
    - Chọn **InstanceType**
    - Chọn **Keypair** của bạn
    - Nhập **MainStackName** `FCJ-Workshop-East`
    - Nhập **IP SSH của bạn** *(là IP máy của bạn dùng để truy cập vào máy ảo)*
    - Chọn **Next**
![alt text](/images/Initialize-CloudFormation/14.png?featherlight=false&width=90pc)

    - Tiếp tục **Next** và chọn **Submit**
9. **Khởi tạo stack FCJ-Workshop-East-2 thành công**
![alt text](/images/Initialize-CloudFormation/15.png?featherlight=false&width=90pc)

10. **Kiểm tra EC2 Intances**
    - Nhập **EC2** trên thanh tìm kiếm
    - Chọn **EC2**
![alt text](/images/Initialize-CloudFormation/16.png?featherlight=false&width=90pc)

11. **Trong giao diện EC2**
    - Chọn **Intances** sẽ thấy 3 Intances đã được tạo
![alt text](/images/Initialize-CloudFormation/17.png?featherlight=false&width=90pc)
    - Chọn **Management-Bastion**
    - Copy **Public IP**
![alt text](/images/Initialize-CloudFormation/18.png?featherlight=false&width=90pc)
12. **Đến thư mục bạn đã lưu Keypair ở bước trước**
    - Chạy **command prompt** tạo thư mục đó
    - Nhập `scp -i <key name truy cập> <key name cần gửi> ec2-user@<public ip Management>:`
![alt text](/images/Initialize-CloudFormation/chuyenkey.png?featherlight=false&width=90pc)
{{% notice tip %}}
Bước này dùng để gửi 2 file **keypair** vào mày ảo **Management-Bastion** thuận tiện cho các bước tiếp theo
{{% /notice %}}