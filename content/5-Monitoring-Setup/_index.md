---
title : "Cấu Hình Giám Sát"
date: 2025-06-19
weight : 5
chapter : false
pre : " <b> 5. </b> "
---


#### Giám sát lưu lượng mạng với VPC Flow Logs & CloudWatch
Sau khi triển khai kiến trúc kết nối giữa các **VPC** bằng mô hình **Hub-and-Spoke**, **Full Meshed**, và **Transit Gateway**, bước tiếp theo là thiết lập cơ chế giám sát lưu lượng mạng, nhằm:
- Theo dõi hoạt động kết nối thực tế giữa các **VPC**,
- Xác định các vấn đề về kết nối, bảo mật hoặc hiệu năng,
- Và phục vụ việc kiểm tra, đánh giá sau triển khai.
Trong phần này, chúng ta sẽ sử dụng hai dịch vụ chính của **AWS**:
- **VPC Flow Logs**: Ghi lại thông tin chi tiết về các lưu lượng mạng đi vào, đi ra và nội bộ giữa các ENI (Elastic Network Interface) trong **VPC**.
- **Amazon CloudWatch**: Dịch vụ theo dõi và phân tích dữ liệu hoạt động, nơi chúng ta có thể lưu trữ log, tạo bảng điều khiển (dashboard) và thiết lập cảnh báo (alarm).

Việc cấu hình đúng các công cụ giám sát không chỉ giúp đảm bảo kết nối đang hoạt động như kỳ vọng, mà còn hỗ trợ giải quyết sự cố và nâng cao khả năng vận hành hệ thống về lâu dài.

#### Cấu hình VPC Flow Logs
{{% notice note %}}
Lưu ý: Việc cấu hình **Flow Logs** nên thực hiện ít nhất tại **VPC trung tâm (Hub)** để ghi lại toàn bộ lưu lượng đi qua nếu bạn sử dụng mô hình **Transit Gateway**. Với mô hình **Full Meshed**, bạn nên bật **Flow Logs** ở mỗi **VPC** cần giám sát.
{{% /notice %}}
1. **Đăng nhập vào VPC Management Console tại region N. Virginia (us-east-1)**
    - Mở **VPC Management Console**
    - Chọn **Your VPC**
    - Chọn **Hub-vpc**
    - Chọn **Actions**
    - Chọn **Creat flow log**.
![alt text]({{ "/images/monitoring/1.png?featherlight=false&width=90pc" | relURL }})

2. **Tạo Flow Logs**.
    - **Cấu hình như ảnh**
    - Nhấn **Creat flow log**
![alt text](/images/monitoring/2.png?featherlight=false&width=90pc)
    
#### Cấu hình CloudWatch
1. **Đăng nhập vào CloudWatch Management Console tại region N. Virginia (us-east-1)**
    ![alt text](/images/monitoring/3.png?featherlight=false&width=90pc)
2. **Creat Dashboards**
    - Chọn **Dashboards**
    - Chọn **Creat dashboard**
    ![alt text](/images/monitoring/4.png?featherlight=false&width=90pc)
3. **Trong giao diện Tạo Creat new dashboard**
    - Nhập **Name**: `VPC-Peering-Workshop-Dashboard`
    - Chọn **Creat dashboard**
![alt text](/images/monitoring/5.png?featherlight=false&width=90pc)
4. **Thêm Widget**
    - Chọn **CloudWatch**
    - Chọn **Metrics**
    - Chọn dạng **Line**
    - Chọn **Next**
![alt text](/images/monitoring/6.png?featherlight=false&width=90pc)
    - Chọn **EC2**
    - Chọn **Per-Instance Metrics**
![alt text](/images/monitoring/7.png?featherlight=false&width=90pc)
    - Lọc theo **MetricName="CPUUtilization"**
    - Chọn **3 Instance** như ảnh 
![alt text](/images/monitoring/8.png?featherlight=false&width=90pc)
{{% notice note %}}
Bạn có thể cấu hình thêm dashboard cho **Database-VPC** nếu muốn.
{{% /notice %}}

