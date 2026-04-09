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
 -  Cài đặt hệ điều hành Ubuntu 24.04.4 LTS


 -  <img width="789" height="70" alt="image" src="https://github.com/user-attachments/assets/b34d44bf-275d-45e4-91e9-b563aefbdc9f" />


 -  Sử dụng một trong các công cụ để giả lập:  VM_Ware
