### E. Triển khai (level test) ứng dụng
1. Chuyển vào trong thư mục ~/myapp
2. Gõ lệnh để docker compose chạy: sẽ run tất cả các service khai báo trong file docker-compose.yml
  > Lợi ích: Chỉ cần docker-compose up -d là toàn bộ hệ thống (Web + Node-RED + Tunnel) tự chạy,
3. Kiểm tra các container đang chạy trong docker, nếu có cái nào bị restart cần tìm lỗi rồi edit lại docker-compose.yml
4. Kiểm tra kiểm thử các service đang chạy độc lập thông qua ip và port của nó: ví dụ mở trình duyệt ip_ubuntu:1880 để check nodered đã chạy chưa
5. Sử dụng nodered: kéo nodered http_in , http_response, function : để tạo api get đơn giản (dùng cho /api proxy_pass của nginx)
6. Sửa file ./myweb/index.html : thêm code html+js để sử dụng được api đã khai báo proxy_pass (thực ra là sử dụng nodered http_in hoặc sử dụng service myapi)

## BÀI LÀM

# 1. Chuyển vào trong thư mục ~/myapp
- Vào thư mục project
  > - cd ~/myapp

# 2. Gõ lệnh để docker compose chạy: sẽ run tất cả các service khai báo trong file docker-compose.yml
  > Lợi ích: Chỉ cần docker-compose up -d là toàn bộ hệ thống (Web + Node-RED + Tunnel) tự chạy.
<img width="1178" height="190" alt="image" src="https://github.com/user-attachments/assets/9b2ff48f-bf25-43de-bcb6-30028e0feeb2" />

# 3. Kiểm tra các container đang chạy trong docker, nếu có cái nào bị restart cần tìm lỗi rồi edit lại docker-compose.yml
- Kiểm tra container có chạy không
 > - docker ps
<img width="1204" height="238" alt="image" src="https://github.com/user-attachments/assets/df4ddd68-02c1-4bbb-9f35-f0206b7672d4" />
- 3 container đang chạy tốt

# 4. Kiểm tra kiểm thử các service đang chạy độc lập thông qua ip và port của nó: ví dụ mở trình duyệt ip_ubuntu:1880 để check nodered đã chạy chưa

# TEST từng service độc lập

- Node-RED : http://IP_UBUNTU:1880
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/00a0f6e3-b34f-4344-ac6b-55ae7a46b882" />

- Flask API (myapi): http://IP_UBUNTU:9630/fun?tien=100
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4729c9e6-c644-458a-bfce-228b01db82db" />

- Nginx web : http://IP_UBUNTU
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/225265d3-d1a8-4095-ae13-a362e5ca63ae" />

- Nginx proxy API: http://IP_UBUNTU/api?tien=100
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/027b34c7-78cc-4c4a-bec1-fe417179211b" />

# 5. Sử dụng nodered: kéo nodered http_in , http_response, function : để tạo api get đơn giản (dùng cho /api proxy_pass của nginx)

- kéo nodered http_in , http_response, function
<img width="908" height="438" alt="image" src="https://github.com/user-attachments/assets/f5c47f07-ba2a-4ed1-8d2a-a2f117a7764d" />
- TEST
<img width="756" height="329" alt="image" src="https://github.com/user-attachments/assets/f2001993-b28d-4399-b7e9-4fe671f9c252" />
