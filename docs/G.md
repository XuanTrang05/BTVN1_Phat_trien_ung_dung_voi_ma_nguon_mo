### G. Triển khai ứng dụng đến End-user
1. Trong Cloudflare: Tạo tunnel (đường hầm), chọn loại triển khai cho docker
2. Convert lệnh docker run ... sang dạng docker compose
3. Khai báo kết quả convert vào trong file docker-compose.yml
4. Chạy lại docker compose
5. Public ứng dụng bằng cách thêm 1 router trỏ tới container đang chạy trong docker, dữ liệu sẽ đi qua tunnel, url dạng sub-domain
6. Kiểm tra url sub-domain đã hoạt động public cho mọi end-user

#### Cấu trúc thư mục:
```
myapp/
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
├── myweb/
│   └── index.html
└── nodered/ (sẽ tự sinh dữ liệu)
│   └── (có nhiều file tự sinh)
│   └── settings.js (file này cần edit để bắt nodered login)
```

#### Sơ đồ theo góc nhìn của dev:
```mermaid
graph LR
A(Ubuntu) -- Command basic --> B((Docker compose))
B -- Khai báo --> C((Nodered))
C -- Cấu hình --> E(Yêu cầu đăng nhập) --> Z[end-user]
B -- Khai báo --> D((nginx))
D -- Cấu hình --> F(web+domain) --> Z
B -- Khai báo --> G(myapi)
D -- Cấu hình --> H((API)) --> F
H -- proxy --> G

```

#### Sơ đồ theo góc nhìn ngược lại:
```mermaid
graph LR
A[End-user] --> B((Cloudflare Tunnel)) --> C((Nginx))
C -- Cấu hình --> D(Nodered login)
C -- Cấu hình --> E((web+domain))
C -- Cấu hình --> G(myapi as api) --> E
D --> E
```
### G. Câu hỏi về bài làm?
1. Tại sao phải dùng Nginx làm Reverse Proxy mà không trỏ thẳng Tunnel vào Node-RED?
2. Sự khác biệt giữa việc Mount file và Mount thư mục trong Docker là gì?
3. Nếu thay đổi file index.html ở máy Ubuntu, nội dung trên web có thay đổi ngay không? Tại sao?
4. docker-compose.yml khai báo các services có phần **restart: always** hoặc **restart: unless-stopped** : chúng để làm gì?
5. Cách khai báo để tất cả các services đều dùng chung 1 network? lợi ích của việc khai báo này là gì? Sửa đổi file docker-compose để tất cả các service đều dùng chung 1 network.
6. Tìm cách đưa Cloudflare **Token** vào trong file .env rồi sau đó thêm .env vào file .gitignore trước khi push code lên github. Tại sao nói đây là điều quan trọng về bảo mật mã nguồn?
7. Tại sao chúng ta nên thêm hậu tố :ro khi mount file cấu hình Nginx?
8. Khi dùng Cloudflare Tunnel: có cần thiết phải mở cổng cho các service nữa không?
# BÀI LÀM
### G. Triển khai ứng dụng đến End-user
1. Trong Cloudflare: Tạo tunnel (đường hầm), chọn loại triển khai cho docker
- Bước 1: vào Cloudflare
- Bước 2:mở Zero Trust
  > - Zero Trust → Networks → Tunnels
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b0dccb2e-6360-4f99-b567-0df8015212e0" />
  - ấn Add a tunnel -> chọn cloudflared -> đặt tên cho tunnel -> Chọn môi trường chạy ( docker) -> lấy token và thêm vào docker-compose.yml 
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/97c6688b-4c48-470e-9a59-2b67de68d78a" />
- chạy lại docker
<img width="1173" height="644" alt="image" src="https://github.com/user-attachments/assets/572e44c2-8996-4414-a359-cc7d99c21c4d" />
- <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/193b5305-e420-43fe-b1e2-c1ea1cfbc371" />

-  Cấu hình router
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9b762947-a43f-4beb-ad05-040f68398b7a" />


# 2. Convert lệnh docker run ... sang dạng docker compose
- Sau khi convert, toàn bộ hệ thống có thể được khởi chạy chỉ bằng một lệnh duy nhất:
  > - docker compose up -d
<img width="1100" height="203" alt="image" src="https://github.com/user-attachments/assets/fcbfb923-38dd-44d1-b41e-c81c2046e51f" />

# 3. Khai báo kết quả convert vào trong file docker-compose.yml
- Bước 1: Kiểm tra các container đang chạy
   > - docker ps
- Bước 2: Xác định lệnh docker run ban đầu
- Bước 3: Tạo file docker-compose.yml
- Bước 4: Chuyển đổi cấu hình vào docker-compose
- Bước 5: Khởi chạy hệ thống bằng Docker Compose
   > - docker compose up -d
<img width="1106" height="206" alt="image" src="https://github.com/user-attachments/assets/1a5e388d-2e7b-49bd-a5b6-4b44b2b266fd" />

#  4. Chạy lại docker compose
- docker compose up -d
 > - Ý nghĩa của lệnh
docker compose up: khởi động toàn bộ các service đã khai báo trong file docker-compose.yml
  -d: chạy ở chế độ nền (background), không chiếm terminal
Kiểm tra kết quả
Có thể kiểm tra trạng thái các container bằng: docker ps
<img width="1106" height="272" alt="image" src="https://github.com/user-attachments/assets/0f2d93f5-31f3-473d-be28-1663a353f4af" />

# 5. Public ứng dụng bằng cách thêm 1 router trỏ tới container đang chạy trong docker, dữ liệu sẽ đi qua tunnel, url dạng sub-domain
<img width="927" height="783" alt="image" src="https://github.com/user-attachments/assets/4fe72f0c-0c21-4977-8d01-ebfe1e120bbb" />
- nginx reverse proxy (bên trong container)
web domain → nginx → /api → Flask API : routing nội bộ trong hệ thống

# 6. Kiểm tra url sub-domain đã hoạt động public cho mọi end-user
- [https://web.hoangthixuantrang.id.vn/]
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/355f43e7-780a-4de9-be87-5b796478d98f" />


- [ https://nodered.hoangthixuantrang.id.vn/]
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/acce151b-351b-4a0c-8555-bf527790337e" />

[ api.hoangthixuantrang.id.vn/]
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/502576d5-0417-4eab-88e3-9969204be2bc" />

### G. Câu hỏi về bài làm

# 1. Tại sao phải dùng Nginx làm Reverse Proxy mà không trỏ thẳng Tunnel vào Node-RED?
- Nginx giúp đóng vai trò reverse proxy để điều hướng nhiều dịch vụ trên cùng một domain. Nếu trỏ Cloudflare Tunnel trực tiếp vào Node-RED thì chỉ sử dụng được một service duy nhất, khó mở rộng.
- Ngoài ra, Nginx giúp:
  > - Quản lý nhiều service (web, API, Node-RED) trên cùng một domain
  > - Tăng bảo mật bằng cách che giấu service nội bộ
  > - Dễ dàng cấu hình routing (/api, /web,...)

# 2. Sự khác biệt giữa việc Mount file và Mount thư mục trong Docker là gì?
- Sự khác biệt giữa Mount file và Mount thư mục trong Docker
  > - Mount file: chỉ ánh xạ một file cụ thể từ máy host vào container (ví dụ nginx.conf)
  > -Mount thư mục: ánh xạ toàn bộ thư mục từ host vào container

- Khác nhau:
  > - File mount: thay đổi 1 file → container dùng file đó
  > - Folder mount: thay đổi nhiều file → container cập nhật toàn bộ thư mục

# 3. Nếu thay đổi file index.html ở máy Ubuntu, nội dung trên web có thay đổi ngay không? Tại sao?
- Có, sẽ thay đổi ngay nếu file được mount vào container.
- Vì Docker sử dụng volume mapping:
  > - File trên host được ánh xạ trực tiếp vào container
  > - Khi host thay đổi → container đọc dữ liệu mới ngay lập tức

# 4. docker-compose.yml khai báo các services có phần **restart: always** hoặc **restart: unless-stopped** : chúng để làm gì?
- restart: always: container luôn tự khởi động lại khi bị crash hoặc khi Docker restart
- restart: unless-stopped: tự restart trừ khi người dùng chủ động dừng container
  => Giúp đảm bảo hệ thống luôn hoạt động ổn định

# 5. Cách khai báo để tất cả các services đều dùng chung 1 network? lợi ích của việc khai báo này là gì? Sửa đổi file docker-compose để tất cả các service đều dùng chung 1 network.
   - Khai báo:
     networks:
  mynetwork:

services:
  nginx:
    networks:
      - mynetwork

  myapi:
    networks:
      - mynetwork

  nodered:
    networks:
      - mynetwork
  - Lợi ích:
    > - Các container có thể giao tiếp bằng tên service
    > - Không cần expose port ra ngoài không cần thiết
    > - Tăng tính bảo mật và quản lý hệ thống tốt hơn
# 6. Tìm cách đưa Cloudflare **Token** vào trong file .env rồi sau đó thêm .env vào file .gitignore trước khi push code lên github. Tại sao nói đây là điều quan trọng về bảo mật mã nguồn?
- Token Cloudflare chứa quyền truy cập hệ thống.
- Nếu push lên GitHub:
  > - Người khác có thể chiếm quyền tunnel
  > - Dễ bị tấn công hoặc phá hệ thống

- Vì vậy:
  > - Đưa token vào .env
  > - Thêm .env vào .gitignore
→ đảm bảo bảo mật thông tin nhạy cảm

# 7. Tại sao chúng ta nên thêm hậu tố :ro khi mount file cấu hình Nginx?
- :ro = read-only (chỉ đọc)

 - Lợi ích:
  > - Container không thể sửa file cấu hình
  > - Tăng bảo mật
  > - Tránh lỗi do service ghi đè file config

# 8. Khi dùng Cloudflare Tunnel: có cần thiết phải mở cổng cho các service nữa không?
- Không cần thiết phải mở cổng public cho các service.
- Vì:
    > - Tunnel tạo kết nối outbound từ server → Cloudflare
    > - Cloudflare xử lý truy cập từ bên ngoài
- Lợi ích:
    > - Không cần mở firewall
    > - Tăng bảo mật hệ thống
    > - Giảm rủi ro bị scan port
