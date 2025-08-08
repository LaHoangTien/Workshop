---
title : "Kiểm tra kết nối"
date: 2025-06-19
weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---
#### Kiểm tra kết nối
ℹ️ **Information**: Sau khi hoàn tất việc triển khai mô hình kiến trúc **Hub-and-Spoke** với các kết nối **VPC Peering** cần thiết, bước tiếp theo là xác minh khả năng giao tiếp mạng giữa các **VPC** để đảm bảo cấu hình định tuyến, bảo mật và **Peering** đã đúng chức năng.
1. **Kiểm tra kết nối giữa các VPC.**
    - Kết nối SSH đến **EC2 trong Management-vpc**
    - Ping đến **IP private** của **EC2 trong Hub-vpc, Webapps-vpc và Database-vpc**
![alt text](/images/workshop-full-mesh/13.png?featherlight=false&width=90pc)
{{% notice info %}}
Đã Ping thành công tất cả VPC.
{{% /notice %}}

2. **SSH đến EC2 trong Webapp-vpc từ máy Management**.
    ```
    chmod 400 workshop-keypair.pem
    ssh -i workshop-keypair.pem ec2-user@<IP-Private-Webapp-Router>
    ```
    - Ping đên IP private của các EC2 còn lại
![alt text](/images/workshop-full-mesh/14.png?featherlight=false&width=90pc)
3. **SSH đến EC2 trong Database-vpc từ máy Management.**
    ```
    chmod 400 workshop-keypair-west.pem
    ssh -i workshop-keypair-west.pem ubuntu@<IP-Private-Database-Router>
    ```
    ![alt text](/images/workshop-full-mesh/15.png?featherlight=false&width=90pc)

#### Kết luận 
Sau khi hoàn tất triển khai mô hình **Full Meshed Peering**, chúng ta có thể nhận thấy rằng giải pháp này **khắc phục được hạn chế về định tuyến chuyển tiếp trong mô hình Hub-and-Spoke**. Các **VPC** hiện tại có thể giao tiếp trực tiếp với nhau, giúp đảm bảo kết nối toàn phần giữa các thành phần trong hệ thống.

Tuy nhiên, mô hình này cũng nhanh chóng bộc lộ các thách thức thực tế khi áp dụng ở quy mô lớn:
- **Tốn công quản trị:** Mỗi cặp **VPC** cần một kết nối **peering** riêng, dẫn đến số lượng kết nối và **route table** tăng nhanh theo cấp số nhân.

- **Khó kiểm soát bảo mật:** Với nhiều kết nối đồng cấp, việc cấu hình và duy trì các **Security Group**, **NACL** và **Route Table** trở nên phức tạp hơn.

- **Giới hạn về khả năng mở rộng:** Trong môi trường **multi-region** hoặc có nhiều tài khoản **AWS (multi-account)**, kiến trúc **Full Mesh** trở nên khó duy trì và dễ lỗi cấu hình.
 
 👉Chính vì vậy, trong phần tiếp theo, chúng ta sẽ tiếp cận giải pháp tối ưu hơn cho việc mở rộng kết nối mạng giữa nhiều VPC. đó là **AWS Transit Gateway**, một dịch vụ trung tâm giúp đơn giản hóa việc kết nối, định tuyến và kiểm soát lưu lượng mạng trong các hệ thống phân tán hiện đại.