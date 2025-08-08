---
title : "Các bước chuẩn bị"
date: 2025-06-19
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

#### Các bước chuẩn bị
ℹ️ **Information**: Ở phần này, bạn sẽ sử dụng CloudFormation Template để tạo hạ tầng mạng có kết nối với Internet một cách thuận tiện rồi sau đó tạo thêm hai máy ảo ở hai public subnet của hai VPC.

💡 **Pro Tip**: CloudFormation Template giúp tự động hóa việc tạo và quản lý tài nguyên AWS, giúp tiết kiệm thời gian và giảm thiểu lỗi khi triển khai.

🔒 **Security Note**: Đảm bảo rằng bạn đã cấu hình đúng các security groups và network ACLs để bảo vệ các tài nguyên của bạn.

#### Yêu cầu hệ thống

1. **Tài khoản AWS:**
    - Tài khoản **AWS** có quyền truy cập vào các dịch vụ: **VPC, EC2, CloudFormation**
    - Đủ quyền để tạo các tài nguyên cần thiết
2. **Kiến thức cơ bản:**
    - Hiểu biết về **VPC** và các thành phần của nó
    - Kiến thức về networking cơ bản
    - Quen thuộc với **AWS Management Console**
3. **Công cụ cần thiết:**
    - Trình duyệt web hiện đại
    - SSH client ([MobaXterm](https://mobaxterm.mobatek.net/download.html))


#### Các bước thực hiện

1. [Tạo Key Pair](1-Prerequisites/1.1-Generate-KeyPair)
2. [Khởi tạo CloudFormation Template](1-Prerequisites/1.2-Initialize-CloudFormation)

<!-- need to remove parenthesis for path in Hugo 0.88.1 for Windows-->