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
