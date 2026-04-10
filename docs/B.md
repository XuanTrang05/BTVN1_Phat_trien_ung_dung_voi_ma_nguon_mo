### B. Cài đặt Ubuntu + Docker 
1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
   - Sử dụng một trong các công cụ để giả lập: HyperV (có sẵn của windows), VirutualBox (Miễn phí), VM_Ware (bản quyền)
   - Download file [iso](https://releases.ubuntu.com/24.04.4/ubuntu-24.04.4-live-server-amd64.iso) để cài đặt.
   - Cấu hình mạng trong Ubuntu (và công cụ giả lập) để cho phép truy cập SSH vào Ubuntu từ cmd của windows   
   >    **Ví dụ:**
   >
   >    - để ssh tới ubuntu ở ip 192.168.100.123, user là admin thì mở CMD trên windows, 
   >    - gõ lệnh: **ssh admin@192.168.100.123** 
   >    - hệ thống sẽ yêu cầu nhập password (chú ý : password sẽ không hiện ra)
   >    - sau khi login thành công sẽ thấy màn hình chào hỏi của ubuntu
2. Tìm hiểu các lệnh cơ bản của ubuntu
   > *Các lệnh cần tìm hiểu:*
   > 
   >    - Liệt kê các file trong thư mục: ls
   >    - Tạo thư mục: mkdir nameFolder
   >    - Chuyển thư mục làm việc: cd path
   >    - Copy file: cp file_nguồn path/file_đích
   >    - Thay đổi quyền thao tác file: sudo chmod  xxx filename
   >    - Edit file: sudo nano tenfile
   >       + CTRL+o : lưu nội dung sau khi edit
   >       + CTRL+x : thoát edit file
   >    - Xem ip của máy ubuntu: ip -4 addr
   > 
3. Cài đặt docker cho Ubuntu
4. Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
5. Cấu hình để docker chạy mà không cần tiền tố sudo
6. Tìm hiểu tập lệnh của docker và docker compose
7. Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
 # BÀI LÀM 
# 1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
 -  Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
 -  Sử dụng một trong các công cụ để giả lập:  VM_Ware
 -  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/049e7fd6-f043-4cff-9be2-2b4f0da74132" />

- Cài SSH trong Ubuntu
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bb46ea9f-e99b-4ca7-8ff7-05b66690b3a0" />
- khởi động dịch vụ SSH và cấu hình để SSH tự động chạy khi khởi động hệ thống. Sau đó, kiểm tra trạng thái dịch vụ và đảm bảo SSH hoạt động bình thường.
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/29670b09-b073-4edd-a857-8064a32709a8" />
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f4d5b9ab-496a-4cbe-8930-218d794b8589" />

- truy cập SSH vào Ubuntu từ cmd của windows
   - BƯỚC 1: Lấy IP của Ubuntu
Trong Ubuntu, gõ: ip -4 addr để xem ip của máy ubuntu
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b2f3fd3c-2dcd-41a3-8d91-63b0bef835c8" />

   - BƯỚC 2: Mở CMD trên Windows
- gõ lệnh : ssh xuantrang@192.168.18.128
- sau đó máy sẽ hỏi : Are you sure you want to continue connecting (yes/no/[fingerprint])?. chọn yes và sau đó nhập mật khẩu của ubuntu.
- cấu hình SSH trên Ubuntu và sử dụng lệnh ssh từ máy Windows để kết nối đến máy Ubuntu thông qua địa chỉ IP. Sau khi nhập đúng thông tin đăng nhập, hệ thống hiển thị màn hình chào của Ubuntu, chứng tỏ kết nối SSH thành công.
   - <img width="1022" height="827" alt="image" src="https://github.com/user-attachments/assets/28ab4b05-0056-4904-832f-7f17ed051210" />

# 2. Tìm hiểu các lệnh cơ bản của ubuntu
   >    - Liệt kê các file trong thư mục: ls
   >    - Tạo thư mục: mkdir nameFolder
   >    - Chuyển thư mục làm việc: cd path
   >    - Copy file: cp file_nguồn path/file_đích
   - <img width="806" height="139" alt="image" src="https://github.com/user-attachments/assets/bec52b45-6441-4d88-82f7-82a55c955420" />
   >    - Edit file: sudo nano tenfile
   >       + CTRL+o : lưu nội dung sau khi edit
   >       + CTRL+x : thoát edit file
   >      <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1f57a413-12ee-4070-900f-c51262337ed4" />
   >    - Thay đổi quyền thao tác file: sudo chmod  xxx filename
   - <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1f2e1ec2-0081-4b68-8583-7bb7261b1e33" />
   - Lệnh chmod 777 được sử dụng để cấp toàn quyền (đọc, ghi, thực thi) cho tất cả người dùng đối với file.


# 3. Cài đặt docker cho Ubuntu
# A. Cài Doker
- BƯỚC 1: Cập nhật hệ thống : sudo apt update
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2fbc6ddb-0a8c-42b8-9147-084d756919b8" />

- BƯỚC 2: Cài Docker : sudo apt install docker.io -y
<img width="1272" height="710" alt="image" src="https://github.com/user-attachments/assets/6335a57e-adbc-4c6d-bb01-675bf7e82726" />

- BƯỚC 3:
  > - Bật Docker : sudo systemctl start docker
  > - Cho Docker tự chạy khi bật máy: sudo systemctl enable docker
<img width="1205" height="695" alt="image" src="https://github.com/user-attachments/assets/129942db-8c07-4f39-9012-99cd41cc8eba" />

- BƯỚC 4 : Test Docker : sudo docker run hello-world
- <img width="1267" height="792" alt="image" src="https://github.com/user-attachments/assets/69fbc848-d3c1-4784-9cd7-9de4a20aa0db" />
- => đã cài đặt Docker trên Ubuntu bằng lệnh apt install docker.io, sau đó khởi động dịch vụ Docker và cấu hình để Docker tự động chạy khi khởi động hệ thống. Cuối cùng, kiểm tra bằng lệnh docker run hello-world và nhận được kết quả thành công.

# B. Cài Docker Compose
 Cài Docker Compose : sudo apt update
sudo apt install docker-compose-v2 -y
<img width="1205" height="672" alt="image" src="https://github.com/user-attachments/assets/9c8e067d-9306-4b10-ba5d-87d2f7909174" />

# 4. Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
 Kiểm tra Docker : docker --version
<img width="1263" height="733" alt="image" src="https://github.com/user-attachments/assets/6df883d3-c50f-4ef2-b3cc-5e8bc7096cb7" />
 Kiểm tra phiên bản Docker compose :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/08e29431-b80d-45fd-8322-68182b7437bd" />

# 5. Cấu hình để docker chạy mà không cần tiền tố sudo

- BƯỚC 1: Thêm user vào nhóm docker 
> - sudo usermod -aG docker $USER
- BƯỚC 2: Áp dụng thay đổi
> - newgrp docker
- BƯỚC 3: TEST
> - docker run hello-world
- KẾT QUẢ:
> - đã cấu hình để Docker có thể chạy mà không cần sử dụng sudo bằng cách thêm user vào nhóm docker và áp dụng thay đổi. Sau đó, kiểm tra và chạy container thành công mà không cần sudo.
<img width="1204" height="808" alt="image" src="https://github.com/user-attachments/assets/416b1de7-23f1-46ae-ab3e-d9e4586e4e53" />

# 6. Tìm hiểu tập lệnh của docker và docker compose
# A. Docker
1. Xem container đang chạy
- docker ps
<img width="759" height="46" alt="image" src="https://github.com/user-attachments/assets/c4bdc9d1-579a-4e42-accc-8826795bdd12" />

2. Xem tất cả container
- docker ps -a
<img width="1141" height="92" alt="image" src="https://github.com/user-attachments/assets/39fda01f-4b1e-470b-a97c-af866acbf103" />

3. Chạy container
- docker run hello-world
<img width="1193" height="779" alt="image" src="https://github.com/user-attachments/assets/620f709a-f6b8-4601-94a7-87117f14b94b" />

4. Xóa container
- docker rm ID_container
<img width="1232" height="138" alt="image" src="https://github.com/user-attachments/assets/2a50a2f8-f069-47d9-85d8-dcd8e7e43c57" />

5. Xem image
- docker images
<img width="1173" height="116" alt="image" src="https://github.com/user-attachments/assets/67133603-7e4e-4d72-b606-75be51d15654" />

6.Xóa image
- docker rmi ID_image

# B. Docker compose
1. Chạy hệ thống
- docker compose up -d
2. Dừng hệ thống
- docker compose down
3. Xem container
- docker compose ps
<img width="786" height="155" alt="image" src="https://github.com/user-attachments/assets/7119d12a-02cd-4a5c-b1ac-d93794def65d" />

# 7. Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
- Mở port 80
> - sudo ufw allow 80
<img width="662" height="94" alt="image" src="https://github.com/user-attachments/assets/a2d9729a-5134-40cf-9c62-f1a24d8d7ec1" />

- Mở port 1880
> - sudo ufw allow 1880
<img width="676" height="68" alt="image" src="https://github.com/user-attachments/assets/c845f4bd-55b8-4a6b-8f46-772673b8ee7c" />

- Mở port 9630
> - sudo ufw allow 9630
<img width="667" height="71" alt="image" src="https://github.com/user-attachments/assets/f26c9d35-4a6d-47f2-b472-d92ace3877ee" />

- Bật firewall
> - sudo ufw enable
> - Nếu có hỏi: Proceed with operation (y/n)? . gõ y
<img width="654" height="71" alt="image" src="https://github.com/user-attachments/assets/5dd6c4d2-f93b-4099-b2a4-1d2a107df51c" />

- Kiểm tra lại
> - sudo ufw status
<img width="670" height="294" alt="image" src="https://github.com/user-attachments/assets/9496f471-ebdf-49a4-aa2d-dd759813eab9" />
