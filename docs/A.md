### A. Đăng ký tên miền xịn cho cá nhân:
1. Đăng ký domain xịn (có thể dùng của [mắt bão](https://www.matbao.net/ten-mien/dang-ky-ten-mien.html), tên miền *.id.vn đang miễn phí cho mọi công dân việt nam <= 23 tuổi, *.io.vn : giá 30k vnđ/năm)
2. Đăng ký tài khoản [cloudflare](https://dash.cloudflare.com/)
3. Thêm domain đã đăng ký vào trong cloudflare : Nhận 2 dòng namespace
4. Nhập 2 dòng namespace của cloudflare vào trong trang quản lý DNS record của tên miền đăng ký (vd trên mắt bão)
   ## BÀI LÀM
# 1 Đăng ký domain
- Truy cập đường link : https://www.matbao.net/ten-mien/ten-mien-mien-phi.html để vào Mắt Bão
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/92411076-dd7d-43d1-b44a-53be21d3369c" />
- Sau khi vào Mắt bão ta sẽ thực hiện hiện đăng kí domain bằng cách nhập tên miền, sau đó thực hiện các thao tác trang web yêu cầu để đăng kí tên miền
# kết quả sau khi đăng kí thành công
<img width="1179" height="2556" alt="image" src="https://github.com/user-attachments/assets/f9f5912f-9315-4e4a-b017-cec9c1aae426" />
# 2  Đăng ký tài khoản [cloudflare]

- Vào trang chủ của Cloudflare , nhấn sign in để tạo tài khoản và thực hiện nhập các thông tin theo yêu cầu.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f81abfb0-9c34-4e53-9e79-51504b390373" />

# 3. Thêm domain đã đăng kí vào Cloudflare : nhận 2 dòng namespace
- thêm domain vào Cloudflare bằng chức năng "Add a Site" và chọn gói miễn phí. Hệ thống đã cung cấp hai bản ghi Nameserver, em đã lưu lại để sử dụng trong bước cấu hình DNS tiếp theo.
- [ luciana.ns.cloudflare.com ]
- [ patrick.ns.cloudflare.com ]
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bf4e3d6a-7592-40fd-9da8-1a0b6dc5b06a" />

# 4. Nhập 2 dòng namespace của cloudflare vào trong trang quản lý DNS record của tên miền đăng ký (vd trên mắt bão)
- Sau khi ấn đăng nhập vào mắt bão. ấn vào tên miền ( domain)
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/33e7aa3a-d08a-4dc7-a7c8-f13dc01cbe52" />
  
