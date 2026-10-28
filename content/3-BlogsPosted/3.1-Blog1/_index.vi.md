---
title: "Blog 1"
date: 2026-10-20
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# AMAZON ECS GATEWAY: GIẢI PHÁP INGRESS MẠNG QUẢN LÝ TOÀN DIỆN CHO CONTAINER

Amazon ECS vừa chính thức ra mắt **Amazon ECS Gateway**, một tài nguyên ở cấp độ tài khoản (account-level) giúp đơn giản hóa toàn bộ hạ tầng mạng đầu vào (ingress networking) cho các ứng dụng container. Tính năng này tự động cấp phát, cấu hình và quản lý vòng đời của Application Load Balancer (ALB), chứng chỉ ACM, DNS hostname và Security Group trực tiếp trong tài khoản AWS của bạn, giải quyết triệt để nút thắt cổ chai khi phải dựng hạ tầng mạng thủ công cho từng microservice.

Các điểm chính cần nắm:

- **Tách bạch trách nhiệm rõ ràng:** Platform team định nghĩa các tiêu chuẩn mạng (Subnet, Security Group, WAF web ACL, TLS certificate) tập trung tại một nơi; Application team chỉ cần thêm tham số `gateway connector` vào service definition mà không cần kiến thức chuyên sâu về mạng.
- **Tối ưu chi phí nhờ chia sẻ ALB:** Hỗ trợ định tuyến dựa trên máy chủ (host-based routing), cho phép tối đa 25 services dùng chung một Application Load Balancer.
- **Tự động cấp phát tài nguyên theo nhu cầu:** ECS tự động khởi tạo ALB khi service đầu tiên kết nối, tự mở rộng thêm ALB khi đạt ngưỡng dung lượng, và tự thu hồi (deprovision) khi không còn service nào sử dụng.
- **Cung cấp điểm cuối tức thì:** Mỗi service khi kết nối đều nhận được một DNS hostname duy nhất và chứng chỉ ACM tương ứng, sẵn sàng nhận traffic ngay khi quá trình triển khai hoàn tất.
- **Mối quan hệ linh hoạt (Many-to-Many):** Một gateway có thể liên kết với tối đa 10,000 cluster, và mỗi cluster có thể gắn tối đa 5 gateway (ví dụ phân tách gateway nội bộ VPC và gateway công khai ra Internet).
- **Hỗ trợ toàn diện và áp dụng mượt mà:** Khả dụng cho mạng `awsvpc` trên cả EC2, AWS Fargate và ECS Managed Instances. Cho phép các service có sẵn gắn thêm gateway connector để chạy song song kiểm thử trước khi gỡ bỏ load balancer cũ.

Tính năng này đặc biệt hữu ích cho các doanh nghiệp chạy kiến trúc Microservices quy mô lớn trên ECS, giúp rút ngắn thời gian phát hành phần mềm và ngăn ngừa sai lệch cấu hình hạ tầng mạng giữa các nhóm phát triển.

**Hình ảnh:**

![Amazon ECS Gateway Architecture](/images/3-Blog/Blog01.png)

**Link:** https://www.facebook.com/share/p/18m9M4gdzv/

