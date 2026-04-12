### F. Gỡ lỗi:
1. nếu có lỗi xẩy ra trong quá trình triển khai docker compose up -d
   > Kiểm tra nhanh: **docker compose ps** giúp biết container nào đang chạy
   > xem log, ví dụ:
   >  docker logs mynginx
   >  docker logs myapi
2. Thêm healthcheck cho myapi trong file docker-compose.yml
   >     healthcheck:
   >       test: ["CMD", "curl", "-f", "http://localhost:9630"]
3. giới hạn resource cho một service: (tránh việc 1 service chiếm quá nhiều ram)
   >     deploy:
   >       resources:
   >         limits:
   >           memory: 512M
   sử dụng lệnh: **docker compose stats** để quan sát lượng ram sử dụng bởi mỗi service

   # BÀI LÀM
   # 1. nếu có lỗi xẩy ra trong quá trình triển khai docker compose up -d
   <img width="766" height="691" alt="image" src="https://github.com/user-attachments/assets/cfe48e91-5938-4a3b-801c-7b7b0141be4a" />
   
> Kiểm tra nhanh: **docker compose ps** giúp biết container nào đang chạy
<img width="1289" height="303" alt="image" src="https://github.com/user-attachments/assets/c37eccfe-ae62-4b24-aa82-7fe0f718b043" />

> xem log, ví dụ:
 > -  docker logs mynginx
<img width="1272" height="628" alt="image" src="https://github.com/user-attachments/assets/947fe8d3-69ce-46be-9631-0c7c257bd47e" />
 >  - docker logs myapi
<img width="1251" height="404" alt="image" src="https://github.com/user-attachments/assets/bb10556e-81c6-4e19-ba15-e54b8b699cc5" />

# 2. Thêm healthcheck cho myapi trong file docker-compose.yml
 > -  nano docker-compse.yml
<img width="1239" height="860" alt="image" src="https://github.com/user-attachments/assets/79ed54f6-f48c-4cee-8f27-3c0fedaeab69" />

-  healthcheck:
<img width="1680" height="439" alt="image" src="https://github.com/user-attachments/assets/62f2ff19-9cf0-43f4-8a7f-4805bb29a63c" />

# 3. giới hạn resource cho một service: (tránh việc 1 service chiếm quá nhiều ram)
<img width="1072" height="810" alt="image" src="https://github.com/user-attachments/assets/ec276ca5-0c69-4786-8557-8f58858e7c63" />
- Theo dõi tài nguyên
  > - Sử dụng lệnh: docker compose stats
<img width="1198" height="200" alt="image" src="https://github.com/user-attachments/assets/9b878615-5bef-4bbd-94f6-683d308ba2cf" />


