---
title: "Blog 2"
date: 2026-10-12
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# AWS LAMBDA WEB FUNCTIONS: CHẠY TRỰC TIẾP ỨNG DỤNG WEB HTTP KHÔNG MÁY CHỦ

AWS vừa chính thức ra mắt **AWS Lambda Web Functions**, một mô hình tính toán không máy chủ mới cho phép chạy các ứng dụng web HTTP và API backend chuẩn trực tiếp trên AWS Lambda mà không cần viết lại mã nguồn theo dạng event handler truyền thống hay dùng lớp chuyển đổi (adapter). Song song đó, các hàm Lambda kiểu cũ được đổi tên thành **Lambda Event Functions** (chỉ thay đổi tên gọi, không yêu cầu chỉnh sửa bất kỳ workload hiện có nào), giúp lập trình viên giữ nguyên trải nghiệm xây dựng web server quen thuộc trên nền tảng serverless.

Các điểm chính cần nắm:

- **Hỗ trợ nguyên bản các web framework phổ biến:** Mã nguồn hoạt động như một web server lắng nghe trực tiếp trên cổng HTTP (ra mắt với runtime Node.js 24 trên kiến trúc Arm64), cho phép dùng ngay Express, Hono, Fastify, Next.js hoặc React Router mà không cần wrapper hay cấu hình chuyển đổi phức tạp.
- **Xử lý nhiều request đồng thời và giảm Cold Start:** Khác với mô hình event xử lý tuần tự từng sự kiện, một môi trường thực thi đang warm của Web Function (được cấp sẵn 2 vCPU và 2 GB bộ nhớ khi ra mắt) có thể xử lý nhiều HTTP request cùng lúc, giúp giảm đáng kể tình trạng cold start.
- **Tối ưu chi phí với cơ chế Active Compute:** Thay vì trả tiền cho cả khoảng thời gian chờ I/O (như chờ truy vấn database hoặc gọi API bên ngoài), bạn chỉ trả phí theo thời gian CPU thực sự xử lý (active CPU time), tách riêng với chi phí bộ nhớ và số lượng request.
- **Hỗ trợ native HTTP Streaming:** Cho phép truyền dữ liệu phản hồi theo từng phần (streaming) ngay khi sẵn sàng về phía client thay vì phải chờ gom toàn bộ dữ liệu, phù hợp cho ứng dụng thời gian thực hoặc AI tạo sinh.
- **Cấu trúc tài nguyên gồm 3 thành phần rõ ràng:** Bao gồm **Web Function** (tài nguyên gốc chứa tên và cấu hình), **Revision** (bản chụp bất biến của code và cấu hình giúp rollback nhanh về phiên bản cũ) và **Endpoint** (điểm truy cập mạng cung cấp tên miền HTTPS công khai duy nhất, cấu hình xác thực và quy tắc điều hướng traffic).
- **Định tuyến đa vùng và tích hợp Amazon VPC:** Hỗ trợ triển khai một lần qua nhiều AWS Region để tự động điều hướng request tới Region gần người dùng nhất nhằm giảm độ trễ, đồng thời kết nối đầy đủ vào Amazon VPC để giao tiếp an toàn với database và tài nguyên nội bộ.

Tính năng này đặc biệt hữu ích cho các nhóm phát triển ứng dụng web hiện đại và API backend muốn tận dụng sự đơn giản của web framework thông thường nhưng vẫn hưởng lợi từ khả năng tự mở rộng, vận hành không máy chủ và mô hình tính phí tối ưu của AWS Lambda.

**Hình ảnh:**

![AWS Lambda Web Functions Architecture](/fcj-workshop-template/images/3-Blog/Blog02.png)

**Link**
- 
