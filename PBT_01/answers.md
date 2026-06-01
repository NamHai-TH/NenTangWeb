Câu A1 — HTTP & Browser
1. Các bước khi gõ URL và nhấn Enter:
- Bước 1 (DNS Lookup): Trình duyệt tìm kiếm địa chỉ IP của tên miền shopee.vn thông qua hệ thống phân giải tên miền (DNS).
- Bước 2 (TCP Connection): Trình duyệt thiết lập kết nối TCP với máy chủ bằng quá trình bắt tay 3 bước (3-way handshake).
- Bước 3 (TLS Handshake): Vì dùng https, quá trình thiết lập bảo mật TLS diễn ra để mã hóa dữ liệu.
- Bước 4 (HTTP Request): Trình duyệt gửi một HTTP GET Request tới máy chủ yêu cầu tải trang web.
- Bước 5 (HTTP Response): Máy chủ xử lý và trả về phản hồi chứa mã trạng thái (VD: 200 OK) kèm theo nội dung HTML của trang.
- Bước 6 (Rendering): Trình duyệt phân tích cú pháp HTML, tải thêm CSS/JS/Hình ảnh và render giao diện ra màn hình.

2. 

![A1.2]