---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Tối ưu hóa hiệu năng ứng dụng Spring Boot Serverless trên AWS Lambda với tính năng SnapStart

**Đặt vấn đề**: Ứng dụng Spring Boot truyền thống khi chuyển đổi sang kiến trúc Serverless (AWS Lambda) thường gặp vấn đề "Cold Start" đáng kể do thời gian khởi tạo Application Context và thư viện quá dài, làm giảm trải nghiệm người dùng

**Giải pháp kiến trúc**: Triển khai AWS Lambda tích hợp SnapStart để tối ưu hóa thời gian khởi động thông qua cơ chế khôi phục trạng thái từ snapshot. Hệ thống kết hợp Amazon API Gateway, AWS Secrets Manager để bảo mật thông tin, và Amazon RDS trong Private Subnet để đảm bảo an toàn dữ liệu

**Quy trình thực thi**: Yêu cầu từ người dùng thông qua API Gateway kích hoạt AWS Lambda. SnapStart giúp Lambda khôi phục trạng thái nhanh chóng, bỏ qua quá trình khởi động nặng. Lambda sau đó truy xuất thông tin bảo mật từ Secrets Manager và thực thi truy vấn dữ liệu từ Amazon RDS

**Đánh giá giải pháp**: Giải pháp giải quyết triệt để vấn đề Cold Start cho Java, hỗ trợ khả năng tự động mở rộng linh hoạt và tối ưu chi phí vận hành cho các doanh nghiệp đang hiện đại hóa hệ thống hoặc chuyển đổi sang Microservices

![Sơ đồ kiến trúc AI Diet Tracker](/fcj-workshop-template/images/3-Blogsposted/blog2/blog2.jpg)