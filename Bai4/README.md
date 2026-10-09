# Báo cáo Bài 4: Lưu trữ dữ liệu đơn giản với Docker Volume

## 1. Cấu trúc thư mục
```text
homework/session_09/ex4/
└── README.md

2. Các bước Thực thi
Bước 1: Tạo Named Volume mới
Thực hiện tạo volume có tên easy-volume:

Bash
docker volume create easy-volume
Kiểm tra danh sách volume:

Bash
docker volume ls
Kết quả: Volume easy-volume xuất hiện trong danh sách local volume.

Bước 2: Ghi dữ liệu vào Volume bằng Container Alpine thứ nhất
Khởi chạy container Alpine tạm thời (--rm), mount volume easy-volume vào thư mục /data và ghi nội dung vào tệp /data/test.txt:

Bash
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
Ghi chú: Sau khi thực thi xong câu lệnh, container Alpine này sẽ tự động xóa, nhưng dữ liệu trong easy-volume vẫn được lưu trữ bền vững trên host.

3. Kết quả Kiểm tra Minh chứng
Bước 3: Đọc dữ liệu từ Volume bằng Container Alpine thứ hai
Khởi chạy container Alpine thứ hai để kiểm tra tính bền vững của dữ liệu sau khi container trước đã bị xóa:

Bash
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
Kết quả hiển thị trên Terminal:

Plaintext
Luu tru du lieu Docker
Xác nhận:

Volume easy-volume được tạo và quản lý thành công bởi Docker Engine.

Dữ liệu test.txt ghi bởi container thứ nhất vẫn tồn tại và được đọc chính xác bởi container thứ hai, chứng minh tính bền vững (persistence) của Docker Named Volume.