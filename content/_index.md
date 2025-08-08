---
title: "VPC Peering Advanced Patterns"
date: 2025-07-09
weight: 2
chapter: false
---

# Workshop VPC Peering Advanced Patterns

#### Tổng quan

Theo mặc định, các **VPC (Virtual Private Cloud)** trong AWS là hoàn toàn cách ly với nhau. Các tài nguyên như EC2 hoặc RDS trong một VPC **không thể giao tiếp** trực tiếp với tài nguyên trong một VPC khác nếu không có kết nối mạng rõ ràng.  

Trong bài lab này, bạn sẽ thực hiện kết nối **VPC Peering** giữa các VPC thông qua mô hình **Hub-and-Spoke**, nhằm cho phép các tài nguyên trong các VPC con có thể **liên lạc gián tiếp thông qua một VPC trung tâm (Hub VPC)**.  

Đây là bước đầu tiên để hiểu rõ kiến trúc mạng phân tán và khả năng mở rộng trong môi trường đa tài nguyên AWS.

---

### Mô hình kiến trúc ban đầu: Hub-and-Spoke

Chúng ta sẽ tạo ra 4 VPC:
- **WebApp VPC** (us-east-1)
- **Management VPC** (us-east-1)
- **Hub VPC** (us-east-1)
- **Database VPC** (us-west-2)

Sau đó, thiết lập các kết nối **VPC Peering** từ các **Spoke VPC** đến **Hub VPC**.  

{{% notice note %}}
**Lưu ý**: Việc kết nối VPC Peering là **point-to-point** và **không hỗ trợ định tuyến xuyên tiếp (transitive routing)**.
{{% /notice %}}

![Hub-and-Spoke Diagram](/images/1/001.png?featherlight=false&width=90pc)

---

### Vấn đề gặp phải: Không hỗ trợ Transitive Routing

Trong mô hình trên:

- **WebApp VPC** có thể kết nối với **Database VPC** thông qua Hub?
  **Không**. Mặc dù cả hai đều kết nối với **Hub**, nhưng do **Peering** không hỗ trợ định tuyến xuyên tiếp, các gói tin từ **WebApp VPC** không thể đi qua **Hub VPC** để đến **Database VPC**.
{{% notice note %}}
Đây chính là **giới hạn** của **VPC Peering connection**.
{{% /notice %}}
---

### Giải pháp 1: Fully Meshed Peering

Trong mô hình này, mỗi VPC sẽ tạo một kết nối **Peering** với **tất cả các VPC còn lại**. Điều này cho phép các **VPC** giao tiếp trực tiếp mà không phụ thuộc vào **routing** qua **Hub**.

Với **4 VPC**, bạn cần tạo 6 kết nối **Peering**:
- **WebApp ↔ Management**
- **WebApp ↔ Hub**
- **WebApp ↔ Database**
- **Management ↔ Hub**
- **Management ↔ Database**
- **Hub ↔ Database**

![Fully Meshed Diagram](/images/1/002.png?featherlight=false&width=90pc)

➡️ **Ưu điểm**:
- Đảm bảo mọi VPC có thể giao tiếp trực tiếp
- Không phụ thuộc vào transitive routing

➡️ **Nhược điểm**:
- Quản lý phức tạp khi số lượng VPC tăng
- Chi phí và cấu hình routing table tăng theo số kết nối

---

### Giải pháp 2: AWS Transit Gateway (TGW)

TGW cho phép kết nối nhiều VPC thông qua một **trung tâm kết nối tập trung**, cho phép **transitive routing tự nhiên**. Mỗi VPC chỉ cần gắn vào Transit Gateway, và bạn có thể định tuyến qua lại giữa tất cả các VPC.

![Transit Gateway Diagram](/images/1/003.png?featherlight=false&width=90pc)

➡️ **Ưu điểm**:
- Đơn giản hóa routing
- Hỗ trợ mở rộng quy mô lớn
- Cho phép transitive routing

➡️ **Nhược điểm**:
- TGW là dịch vụ trả phí ($/attachment/hour)
- Không hỗ trợ tất cả region, cần cân nhắc cho **cross-region**

---


#### Main Content

1. [Các bước chuẩn bị](1-Prerequisites)
2. [Mô hình kiến trúc: Hub-and-Spoke](2-Architectural-Model-Hub-and-Spoke)
3. [Giải Pháp 1: Fully Meshed Peering](3-Solution-1)
4. [Giải pháp 2: AWS Transit Gateway](4-Solution-2)
5. [Cấu Hình Giám Sát](5-Monitoring-Setup)
6. [Dọn Dẹp Tài Nguyên](6-Clean)
<!-- need to remove parenthesis for path in Hugo 0.88.1 for Windows-->