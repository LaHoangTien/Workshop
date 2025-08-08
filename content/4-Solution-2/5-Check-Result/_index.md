---
title : "Kiểm tra kết nối"
date: 2025-06-19
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---
#### Kiểm tra kết nối
ℹ️ **Information**: Sau khi hoàn tất việc triển khai mô hình kiến trúc Hub-and-Spoke với các kết nối **VPC Peering** cần thiết, bước tiếp theo là xác minh khả năng giao tiếp mạng giữa các VPC để đảm bảo cấu hình định tuyến, bảo mật và Peering đã đúng chức năng.
1. **Kiểm tra kết nối giữa các VPC.**
- Kết nối SSH đến EC2 trong Management-vpc
- Ping đến IP private của EC2 trong Hub-vpc, Webapps-vpc và Database-vpc
![alt text](/images/workshop-transit/26.png?featherlight=false&width=90pc)
{{% notice info %}}
Ping thành công tất cả VPC.
{{% /notice %}}

2. **SSH đến EC2 trong Webapp-vpc từ máy Management.**
    ```
    chmod 400 workshop-keypair.pem
    ssh -i workshop-keypair.pem ec2-user@<IP-Private-Webapp-Router>
    ```
    - Ping đên IP private của EC2 trong Hub-vpc và Database-vpc
![alt text](/images/workshop-transit/28.png?featherlight=false&width=90pc)
3. **SSH đến EC2 trong Database-vpc từ máy Management.**
    ```
    chmod 400 workshop-keypair-west.pem
    ssh -i workshop-keypair-west.pem ubuntu@<IP-Private-Database-Router>
    ```
    ![alt text](/images/workshop-transit/27.png?featherlight=false&width=90pc)

#### Kết luận
Việc triển khai **AWS Transit Gateway** đã chứng minh được những ưu điểm vượt trội trong việc đơn giản hóa kết nối mạng giữa nhiều **VPC**, đặc biệt là khi so sánh với các mô hình truyền thống như **Hub-and-Spoke hoặc Full Meshed.**

Với chỉ một kết nối duy nhất từ mỗi **VPC** đến **Transit Gateway**, kiến trúc trở nên:

- Dễ mở rộng hơn khi thêm mới **VPC** hoặc tài khoản,

- Dễ quản trị hơn nhờ cấu hình định tuyến tập trung,

- Và an toàn hơn thông qua kiểm soát lưu lượng mạng ở mức **Transit Gateway Route Table.**

Ngoài ra, khả năng hỗ trợ định tuyến chuyển tiếp (transitive routing) giúp khắc phục hoàn toàn hạn chế lớn nhất của **VPC Peering**, đồng thời chuẩn bị sẵn cho các tình huống kiến trúc phức tạp hơn như **multi-region, multi-account, hoặc hybrid cloud.**