---
title : "Dọn Dẹp Tài Nguyên"
date: 2025-06-19
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Tổng quan về dọn dẹp
⚠️ **Warning**: Để tránh phát sinh chi phí không cần thiết, bạn cần xóa tất cả tài nguyên theo thứ tự sau.
{{% notice warning %}}
Do workshop sử dụng **2 Region (us-east-1 và us-west-2)**, hãy kiểm tra và xóa tài nguyên ở cả hai vùng
{{% /notice %}}
#### Xóa Transit Gateway Attachments
1. **Truy cập VPC Management Console**
    - Mở **VPC Management Console**
    - Chọn **Transit Gateway Attachments**
2. **Xóa Attachments**
    - Chọn tất cả **Attachments** liên quan
    - Nhấn **Actions** > **Delete**
    - Đợi 1-2 phút để hoàn tất việc xóa

#### Xóa Transit Gateway
1. **Truy cập VPC Management Console**
    - Mở **VPC Management Console**
    - Chọn **Transit Gateway**
2. **Xóa Transit Gateway**
    - Chọn tất cả **Transit Gateway** liên quan
    - Nhấn **Actions** > **Delete**
    - Đợi 1-2 phút để hoàn tất việc xóa

⚠️ **Warning**: Bạn phải đợi tất cả Transit Gateway Attachments được xóa hoàn toàn trước khi xóa Transit Gateway.
#### Xóa VPC Peering Connection
1. **Truy cập VPC Management Console**
    - Mở **VPC Management Console**
    - Chọn **Peering Connections**
2. **Xóa Peering Connections**
    - Chọn tất cả **Peering Connections** liên quan
    - Nhấn **Actions** > **Delete VPC Peering Conenction**
#### Xóa CloudFormation Stack
1. **Truy cập CloudFormation**
    - Mở **CloudFormation Management Console**
    - Chọn **Stacks**
2. **Xóa Stacks**
    - Chọn tất cả **Stacks** liên quan
    - Nhấn **Delete**