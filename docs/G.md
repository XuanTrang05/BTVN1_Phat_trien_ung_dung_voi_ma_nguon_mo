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
# BÀI LÀM
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
