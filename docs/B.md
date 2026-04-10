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
 1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
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

2. Tìm hiểu các lệnh cơ bản của ubuntu
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


3. Cài đặt docker cho Ubuntu
A. Cài Doker
- BƯỚC 1: Cập nhật hệ thống : sudo apt update
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2fbc6ddb-0a8c-42b8-9147-084d756919b8" />

- BƯỚC 2: Cài Docker : sudo apt install docker.io -y
<img width="1272" height="710" alt="image" src="https://github.com/user-attachments/assets/6335a57e-adbc-4c6d-bb01-675bf7e82726" />

- BƯỚC 3:
  > - Bật Docker : sudo systemctl start docker
  > - Cho Docker tự chạy khi bật máy: sudo systemctl enable docker
<img width="1205" height="695" alt="image" src="https://github.com/user-attachments/assets/129942db-8c07-4f39-9012-99cd41cc8eba" />

  
B. Cài Docker Compose

- BƯỚC 1: Cài Docker Compose : sudo apt install docker-compose -y
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f6e06a7a-093c-47e2-86e6-cf9bb2a8a008" />

4. Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
 Kiểm tra Docker : docker --version
<img width="1263" height="733" alt="image" src="https://github.com/user-attachments/assets/6df883d3-c50f-4ef2-b3cc-5e8bc7096cb7" />

- BƯỚC 5 : Test Docker : sudo docker run hello-world
- <img width="1267" height="792" alt="image" src="https://github.com/user-attachments/assets/69fbc848-d3c1-4784-9cd7-9de4a20aa0db" />
 - => đã cài đặt Docker trên Ubuntu bằng lệnh apt install docker.io, sau đó khởi động dịch vụ Docker và cấu hình để Docker tự động chạy khi khởi động hệ thống. Cuối cùng, kiểm tra bằng lệnh docker run hello-world và nhận được kết quả thành công.

