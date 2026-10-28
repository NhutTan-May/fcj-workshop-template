---
title: "Worklog Tuần 5"
date: 2026-10-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:
- Tạo tài nguyên tự động với CloudFormation
- Tìm hiểu Lambda và quản lý đăng nhập SSO

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :--- |
| **2** | - Tìm hiểu Infrastructure as Code (IaC)<br>- Chạy thử file mẫu tạo tài nguyên tự động trên AWS CloudFormation | 12/10/2026 | 12/10/2026 | <https://000017.awsstudygroup.com/vi/> |
| **3** | - Tạo hàm AWS Lambda đơn giản trên Console<br>- Hẹn giờ bằng EventBridge tự động tắt EC2 ban đêm tiết kiệm chi phí | 13/10/2026 | 13/10/2026 | <https://000019.awsstudygroup.com/vi/> |
| **4** | - Cấu hình IAM Role cho AWS Systems Manager (SSM)<br>| 14/10/2026 | 14/10/2026 | <https://000012.awsstudygroup.com/vi/> |
| **5** | - Kích hoạt AWS IAM Identity Center (Amazon SSO)<br> | 15/10/2026 | 15/10/2026 | <https://000024.awsstudygroup.com/vi/> |
| **6** | - Cấu hình IAM Permission Boundary giới hạn quyền tối đa<br> | 16/10/2026 | 16/10/2026 | <https://000025.awsstudygroup.com/vi/> |

---

### Kết quả đạt được tuần 5:
- Tự động tạo và xóa hạ tầng bằng AWS CloudFormation
- Tự động tắt máy chủ ngoài giờ bằng Lambda và EventBridge
- Đăng nhập tập trung qua SSO và quản lý máy chủ an toàn qua Session Manager

Dịch vụ AWS đã sử dụng:
- AWS CloudFormation
- AWS Lambda & Amazon EventBridge
- AWS Systems Manager (Session Manager)
- AWS IAM Identity Center (SSO)

Kỹ năng đạt được:
- Tạo hạ tầng bằng code mẫu
- Tự động hóa tác vụ vận hành không máy chủ
- Quản trị bảo mật danh tính người dùng