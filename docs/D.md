### D. (Bonus - không bắt buộc)
1. tạo thư mục ./myapi
2. tạo file ./myapi/app.py sử dụng Python + Flask để làm gì đó funny
3. tạo file ./myapi/requirements.txt chứa các thư viện mà app.py sử dụng (theo như app.py ví dụ thì requirements.txt chỉ cần có nội dung: **flask**)
4. tạo file ./myapi/Dockerfile để khai báo sử dụng Python 3.9 slim
   ```
	# Sử dụng phiên bản Python nhẹ (alpine) để giảm dung lượng image
	FROM python:3.9-slim

	# Thiết lập thư mục làm việc bên trong container
	WORKDIR /app

	# Sao chép file requirements vào và cài đặt thư viện
	COPY requirements.txt .
	RUN pip install --no-cache-dir -r requirements.txt

	# Sao chép toàn bộ mã nguồn vào container
	COPY . .

	# Thông báo container sẽ chạy ở cổng 9630
	EXPOSE 9630

	# Lệnh khởi chạy ứng dụng
	CMD ["python", "app.py"]
5. Sửa đổi docker-compose để sử dụng myapp (xem phần tham khảo ở dưới)
6. Sửa đổi nginx/nginx.conf để /api trỏ tới service myapp cổng 9630

## BÀI LÀM
# 1.  tạo thư mục ~/myapi
   - mkdir myapi
<img width="695" height="124" alt="image" src="https://github.com/user-attachments/assets/8adb2517-2e03-4daa-8449-efc630d6b907" />

# 2. tạo file ./myapi/app.py sử dụng Python + Flask để làm gì đó funny
- Tạo file app.py
  > - nano myapi/app.py
<img width="1191" height="792" alt="image" src="https://github.com/user-attachments/assets/7bbf8b34-2c27-4f9e-bb3e-d6105d69abf5" />

# 3. tạo file ./myapi/requirements.txt chứa các thư viện mà app.py sử dụng (theo như app.py ví dụ thì requirements.txt chỉ cần có nội dung: **flask**)
- Tạo requirements.txt
> - nano myapi/requirements.txt
<img width="1187" height="782" alt="image" src="https://github.com/user-attachments/assets/9723d457-3dd8-408d-9327-e37a89408cf9" />

# 4. tạo file ./myapi/Dockerfile để khai báo sử dụng Python 3.9 slim
TẠO FILE ./myapi/Dockerfile
> - nano myapi/Dockerfile
<img width="1201" height="822" alt="image" src="https://github.com/user-attachments/assets/cc439493-9462-4a70-89a0-8eebf2e6708f" />
- KIỂM TRA NHANH
  > - ls myapi
<img width="759" height="103" alt="image" src="https://github.com/user-attachments/assets/48d8b000-42b7-48ca-8171-d4d1285d2eee" />

# 5. Sửa đổi docker-compose để sử dụng myapp (xem phần tham khảo ở dưới)
SỬA docker-compose.yml (THÊM myapi)
- Mở file:
> - nano docker-compose.yml
- THÊM SERVICE myapi
<img width="1192" height="784" alt="image" src="https://github.com/user-attachments/assets/228d7fb7-c7e1-4134-9117-ba3242297f66" />

# 6. Sửa đổi nginx/nginx.conf để /api trỏ tới service myapp cổng 9630
 - SỬA nginx/nginx.conf
	> - mở file:
		- nano nginx/nginx.conf
- THÊM / SỬA BLOCK /api
  <img width="1234" height="809" alt="image" src="https://github.com/user-attachments/assets/b2f3eb67-de36-47bf-ada6-96becbeb9280" />
  - CHẠY LẠI TOÀN BỘ CONTAINER
 > - Sau khi sửa nginx.conf:
		- docker compose down
		- docker compose up -d --build
- TEST : http://192.168.18.128:9630/fun?tien=100
<img width="1240" height="881" alt="image" src="https://github.com/user-attachments/assets/8c827c0f-0eea-458d-a9fb-4ecfd15ede1d" />



