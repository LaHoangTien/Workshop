---
title : "Kiểm tra kết nối"
date: 2025-06-19
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---
#### Kiểm tra kết nối
ℹ️ **Information**: Sau khi hoàn tất việc triển khai mô hình kiến trúc **Hub-and-Spoke** với các kết nối **VPC Peering** cần thiết, bước tiếp theo là xác minh khả năng giao tiếp mạng giữa các **VPC** để đảm bảo cấu hình định tuyến, bảo mật và **Peering** đã đúng chức năng.
1. **Kiểm tra kết nối giữa các VPC**.
- Kết nối SSH đến EC2 trong Management-vpc
- Ping đến IP private của EC2 trong Hub-vpc
![alt text](/images/VPC-Peering/pinghub.png?featherlight=false&width=90pc)
{{% notice info %}}
Ping thành công vì Management và Hub được thiết lập Peering trực tiếp.
{{% /notice %}}
- Tiếp tục Ping đến IP private của EC2 trong Management-vpc và Database-vpc
![alt text](/images/VPC-Peering/pingweb.png?featherlight=false&width=90pc)
![alt text](/images/VPC-Peering/pingdata.png?featherlight=false&width=90pc)
{{% notice info %}}
Ping không thành công vì đây chính là giới hạn của VPC Peering, không hỗ trợ định tuyến chuyển tiếp (transitive). Nếu không thiết lập Peering trực tiếp sẽ không thể giao tiếp.
{{% /notice %}}
2. **SSH đến EC2 trong Hub-vpc từ máy Management**.
```
chmod 400 workshop-keypair.pem
ssh -i workshop-keypair.pem ec2-user@<IP-Private-Hub-Router>
```
![alt text](/images/VPC-Peering/ssh.png?featherlight=false&width=90pc)
- Ping đên IP private của các EC2 còn lại
![alt text](/images/VPC-Peering/pingall.png?featherlight=false&width=90pc)
{{% notice info %}}
Khác với Management thì Hub router ping được đến tất cả các máy vì Hub được thiết lập Peering trực tiếp đến tất cả các VPC
{{% /notice %}}
#### Kết luận 
Qua quá trình kiểm tra, ta thấy rằng mặc dù các kết nối peering giữa các VPC trong mô hình Hub-and-Spoke đều hoạt động đúng chức năng, tuy nhiên một hạn chế cốt lõi của **VPC Peering là không hỗ trợ định tuyến chuyển tiếp (transitive routing)**.

Cụ thể, **khi Management VPC đã kết nối với Hub VPC và Hub VPC kết nối với WebApp VPC, ta vẫn không thể ping hoặc SSH trực tiếp từ Management sang WebApp nếu không thiết lập thêm một peering trực tiếp giữa hai VPC này**.

👉 Từ đây, chúng ta tiến hành đánh giá và so sánh hai giải pháp khắc phục vấn đề không hỗ trợ transitive routing:

**Solution 1**. [Fully Meshed Peering: Thiết lập peering trực tiếp giữa tất cả các VPC.](3-Solution-1)

**Solution 2**. [AWS Transit Gateway: Sử dụng một dịch vụ trung tâm để kết nối và định tuyến toàn bộ VPC.](4-Solution-2)

Hai mô hình này sẽ được triển khai và đánh giá chi tiết trong các bước tiếp theo của workshop.