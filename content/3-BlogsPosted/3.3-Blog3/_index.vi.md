---
title: "Blog 3"
date: 2026-11-05
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS ACCOUNT ACCESS MANAGER: QUẢN LÝ TRUY CẬP TẬP TRUNG KẾT HỢP LINH HOẠT IAM ROLE

AWS vừa công bố **AWS Account Access Manager (AAM)**, một tính năng mới của AWS IAM giúp kết nối giữa khả năng quản trị truy cập nhân sự tập trung qua AWS IAM Identity Center và sự linh hoạt chi tiết của từng IAM Role trong mỗi tài khoản AWS. Tính năng này xóa bỏ sự đánh đổi lâu nay giữa việc dùng Permission Sets tập trung (khó tùy biến sâu theo từng tài khoản) với việc tự cấu hình federation thủ công, giúp doanh nghiệp kiểm soát quyền truy cập nhất quán trên quy mô lớn.

Các điểm chính cần nắm:

- **Ánh xạ trực tiếp IAM Role từ thư mục người dùng tập trung:** Tích hợp với **AWS IAM Identity Center** cấp tổ chức (đã đồng bộ user và group từ các IdP doanh nghiệp như Okta, Ping Identity, Cisco Duo hoặc Microsoft Entra ID), cho phép quản trị viên gán thẳng các IAM Role sẵn có trong từng tài khoản AWS cho người dùng và nhóm từ một màn hình quản lý duy nhất.
- **Giữ nguyên toàn bộ tính năng nâng cao của IAM Role:** Bảo toàn đầy đủ các cấu hình tùy biến gốc của IAM như custom trust policies, role paths, kiểm soát truy cập dựa trên thẻ (ABAC) và IAM role tags phục vụ phân bổ chi phí.
- **Tách bạch quyền chủ động nhưng vẫn giám sát tập trung:** Từng nhóm phát triển vẫn tự do tạo và tinh chỉnh IAM Role phù hợp với nhu cầu riêng của dự án, trong khi đội ngũ quản trị/bảo mật giữ được tầm nhìn và quyền kiểm soát tập trung trên toàn bộ tổ chức AWS.
- **Truy vết đích danh người dùng và truy cập đa kênh:** Sử dụng cơ chế *trusted identity propagation* để gắn ngữ cảnh danh tính người dùng thực vào phiên role, giúp mọi hành động ghi trên **AWS CloudTrail** đều truy vết chính xác tới từng cá nhân thay vì chỉ ghi nhận tên role chung; hỗ trợ đăng nhập qua Account Access Portal, AWS Access Portal hoặc AWS CLI (`aws login`).
- **Hoạt động song song mượt mà với Permission Sets:** Không bắt buộc chuyển đổi toàn bộ hệ thống cùng lúc, cho phép dùng Account Access Manager tại các tài khoản cần tùy biến IAM Role chuyên sâu và tiếp tục dùng Permission Sets ở những nơi khác.
- **Tự động hóa bằng IaC và miễn phí sử dụng:** Hỗ trợ cấu hình và mở rộng qua AWS CloudFormation, AWS CLI, Terraform và Pulumi; cung cấp hoàn toàn **không tính thêm phí** (chỉ trả phí cho các tài nguyên AWS sử dụng bên dưới) tại toàn bộ các AWS Commercial Regions.

Tính năng này đặc biệt hữu ích cho các doanh nghiệp vận hành nhiều tài khoản AWS (multi-account), giúp đội ngũ bảo mật kiểm soát và kiểm toán truy cập tập trung mà vẫn giữ được tốc độ và sự linh hoạt cho các nhóm kỹ thuật khi phân quyền ứng dụng.

**Hình ảnh:**

![AWS Account Access Manager Architecture](/fcj-workshop-template/images/3-Blog/Blog03.png)

**Link:**
- 
