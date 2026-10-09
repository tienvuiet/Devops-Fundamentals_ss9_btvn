# Báo cáo Bài 3: Đóng gói Trang Web HTML Tĩnh bằng Dockerfile

## 1. Cấu trúc thư mục
```text
homework/session_09/ex3/
├── Dockerfile
├── index.html
└── README.md

Bước 1: Build Docker Image
Thực hiện build image my-html-app:v1 từ Dockerfile:

Bash
docker build -t my-html-app:v1 .
Bước 2: Khởi chạy Container
Chạy container html-app ở chế độ background (detached mode) map cổng 8081 trên máy host với cổng 80 của Nginx container:

Bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
3. Kết quả Kiểm tra Minh chứng
Lệnh truy vấn HTTP (curl http://localhost:8081)
Bash
curl http://localhost:8081
Kết quả:

HTML
<h1>Hello Docker Session 09!</h1>
Xác nhận:

Image my-html-app:v1 được build thành công dựa trên base image lightweight nginx:alpine.

Container html-app khởi chạy thành công tại cổng 8081 và trả về đúng nội dung HTML yêu cầu.