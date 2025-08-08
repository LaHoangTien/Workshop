---
title : "Khởi tạo Key pair"
date: 2025-06-19
weight : 1
chapter : false
pre : " <b> 1.1 </b> "
---

#### Tạo Key Pair
{{% notice tip %}}
Trong workshop này, chúng ta sẽ sử dụng N. Virginia (us-east-1) và Oregon (us-west-2). Nếu bạn muốn sử dụng Region khác , hãy đảm bảo chuyển Region về Region bạn muốn sử dụng khi tạo các tài nguyên liên quan tới workshop.
{{% /notice %}}
1. **Thực hiện tạo Key Pair ở N. Virginia (us-east-1)**
    - Đăng nhập vào **AWS Management Console**
    - Chuyển sang **Region N. Virginia**
    - Tìm **EC2**
    - Chọn **EC2**
![alt text](/images/Generate-KeyPair/1.png?featherlight=false&width=90pc)

2. **Trong giao diện EC2**
    - Chọn **Keypair**
    - Chọn **Create key pair**
![alt text](/images/Generate-KeyPair/2.png?featherlight=false&width=90pc)

3. **Trong giao diện Create key pair**
    - **Name**, nhập `workshop-keypair`
    - **Key pair type**, chọn RSA
    - **Private key file format**, chọn .pem
    - Chọn **Create key pair**
![alt text](/images/Generate-KeyPair/3.png?featherlight=false&width=90pc)

4. **Tạo key pair thành công ở N. Virginia (us-east-1)**
![alt text](/images/Generate-KeyPair/4.png?featherlight=false&width=90pc)

5. **Thực hiện tạo keypair ở Oregon (us-west-2)**
    - Chuyển sang region **Oregon (us-west-2)**
    - Chọn **Create key pair**
![alt text](/images/Generate-KeyPair/5.png?featherlight=false&width=90pc)

6. **Trong giao diện Create key pair**
    - **Name**, nhập `workshop-keypair-west`
    - **Key pair type**, chọn RSA
    - **Private key file format**, chọn .pem
    - Chọn **Create key pair**
![alt text](/images/Generate-KeyPair/6.png?featherlight=false&width=90pc)

7. **Tạo key pair thành công ở Oregon (us-west-2)**
![alt text](/images/Generate-KeyPair/7.png?featherlight=false&width=90pc)