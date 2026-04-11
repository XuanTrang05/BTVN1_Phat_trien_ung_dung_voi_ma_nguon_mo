### C. Cấu hình docker compose:
1. Tạo thư mục: ~/myapp
2. Chuyển vào trong thư mục ~/myapp
3. Tạo thư mục: ./myweb
4. Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)
5. Tạo file **docker-compose.yml** để nó sẽ có các dịch vụ sau:
   > - Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered
   > - Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf
   > - Mount thư mục ./myweb thành thư mục /myweb trong nginx
   > - Mount file **./nginx/nginx.conf** vào file **/etc/nginx/nginx.conf** trong nginx
6. Edit file **./nginx/nginx.conf** để: 
   > - Cấu hình web server cổng 80
   > - server_name là sub-domain (sub-domain tuỳ ý của em)
   > - location / trỏ tới root là thư mục /myweb
   > - location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered
7. Edit file **./nodered/settings.js** để nodered bắt buộc đăng nhập
   > Chạy docker-compose lần đầu để Node-RED tự sinh file cấu hình trong thư mục ./nodered, sau đó mới tiến hành sửa settings.js và restart lại container

### BÀI LÀM

# 1. Tạo thư mục: ~/myapp
- mkdir ~/myapp
<img width="1045" height="99" alt="image" src="https://github.com/user-attachments/assets/71cd5fc1-b20c-4cee-bb82-5fa398195fb2" />

# 2. Chuyển vào trong thư mục ~/myapp
- cd ~/myapp
<img width="609" height="49" alt="image" src="https://github.com/user-attachments/assets/8d7bffe9-beec-4f00-b315-f3f7a6838b9b" />

# 3. Tạo thư mục: ./myweb
- mkdir myweb
<img width="667" height="93" alt="image" src="https://github.com/user-attachments/assets/70fb5360-415b-4b4e-af50-aa7ef0ef13c6" />

# 4. Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)
- nano myweb/index.html
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b1ef65d9-3823-4d2e-a9ca-0ebfba04c168" />

# 5. Tạo file **docker-compose.yml** để nó sẽ có các dịch vụ sau:
- tạo file  **docker-compose.yml**
- gõ: nano docker-compose.yml  để tạo file

<img width="1289" height="822" alt="image" src="https://github.com/user-attachments/assets/7b809414-07d4-496e-a66b-a052558a56d8" />

- tạo thư mục Nginx và nodered ( vì máy chưa có)
   > - mkdir nginx
   > - mkdir nodered
<img width="693" height="112" alt="image" src="https://github.com/user-attachments/assets/733dbd4f-4633-42c3-9cb6-a1565d754b94" />

- Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered

- Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf
  - nano nginx/nginx.conf
<img width="1063" height="818" alt="image" src="https://github.com/user-attachments/assets/494db18a-c99c-4f36-9db1-f8f5dd36b779" />
<img width="679" height="97" alt="image" src="https://github.com/user-attachments/assets/166d6996-2af1-4638-b032-ed1a74553ca7" />
<img width="1087" height="172" alt="image" src="https://github.com/user-attachments/assets/bb9876e9-6102-4f80-ac4c-f903dd61e14a" />

-  Mount thư mục ./myweb thành thư mục /myweb trong nginx
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a23e4ae6-fd63-4358-b362-b7df57342b9f" />

-  Mount file **./nginx/nginx.conf** vào file **/etc/nginx/nginx.conf** trong nginx
<img width="1257" height="669" alt="image" src="https://github.com/user-attachments/assets/b0a35022-edfc-411d-9a11-b90f3b4a8e5a" />

# 6. Edit file **./nginx/nginx.conf** để: 
- Cấu hình web server cổng 80
  > - Mở file cấu hình
   nano nginx/nginx.conf
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d519bf9d-87c6-43ef-b7ed-fa0c1eddce93" />

- location / trỏ tới root là thư mục /myweb
  > - Mở file cấu hình
   nano nginx/nginx.conf
<img width="1263" height="838" alt="image" src="https://github.com/user-attachments/assets/3f9ad671-5947-4b5e-b65b-79be2c9d110e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d1fbdf53-ba91-4a38-b36b-9fb9883ee894" />

 - location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered
   > - Tạo api trong node-Red
<img width="1294" height="912" alt="image" src="https://github.com/user-attachments/assets/b4976fd7-e8ee-42ac-885c-f39ba24b16ea" />
<img width="825" height="419" alt="image" src="https://github.com/user-attachments/assets/118aeca0-8813-461b-b211-115a0901568b" />
- Test qua nginx (proxy)
<img width="626" height="272" alt="image" src="https://github.com/user-attachments/assets/d27c5685-e749-4bce-90df-b79baa635cf8" />

7. Edit file **./nodered/settings.js** để nodered bắt buộc đăng nhập
- Chạy docker-compose lần đầu để Node-RED tự sinh file cấu hình trong thư mục ./nodered, sau đó mới tiến hành sửa settings.js và restart lại container
> - BƯỚC 1: Đảm bảo đã có file settings.js
    - ls nodered
> - BƯỚC 2: Tạo mật khẩu
   - docker exec -it mynodered node-red admin hash-pw [nhập password (ví dụ: 123456)] [ thì sẽ ra dang: $2b$08$xxxxxxxxxxxxxxxxxxxxxxxxxxxxx]
> - BƯỚC 2: Mở file
     - nano nodered/settings.js
> - BƯỚC 4: Sửa settings.js
   - tiến hành sửa mật khẩu và lưu file
> - BƯỚC 5: Restart Node-RED
> - BƯỚC 6: TEST
- Mở: http://IP_UBUNTU:1880
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1f7dff21-5115-43a6-b4aa-b9313567dfcb" />

