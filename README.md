## 🎓 Sinh Viên
Họ tên: Đặng Đình Đạt  
MSV: K225480106003  
Lớp: 58KTPM  
Môn: TEE0421 - Phát triển ứng dụng với mã nguồn mở  

# 📋 Pawn Shop Management System

Hệ thống quản lý tiệm cầm đồ được xây dựng bằng **Django**, **MariaDB**, **Docker**, và **Cloudflare Tunnel**.

**Môn học:** Phát triển ứng dụng với mã nguồn mở - TEE0421  
**Lớp:** 58KTPM  
**Deadline:** 23h59 ngày 09 tháng 5 năm 2026

---

## 🎯 Tính Năng Chính

✅ Quản lý khách hàng (Thêm/Sửa/Xóa)  
✅ Quản lý hợp đồng cầm đồ  
✅ Quản lý danh sách nợ đến hạn  
✅ Ghi nhận lịch sử giao dịch  
✅ Admin panel đầy đủ với CRUD operations  
✅ Hiển thị danh sách nợ quá hạn trên trang chủ  
✅ Public qua Cloudflare Tunnel

---

## 🏗️ Kiến Trúc Hệ Thống

### Các Service trong Docker Compose:

1. **MariaDB** (Port 3306)
   - Cơ sở dữ liệu chính
   - User: `pawnshop_user`
   - Password: `pawnshop_pass`

2. **PhpMyAdmin** (Port 8080)
   - Giao diện quản lý database
   - URL: `http://localhost:8080`

3. **Django** (Port 8000)
   - Ứng dụng web chính
   - URL: `http://localhost:8000`

---

Hướng Dẫn Cài Đặt

### Yêu Cầu:
- Docker & Docker Compose
- Ubuntu/Linux hoặc WSL

### Các Bước:

#### 1. Khởi Động Hệ Thống
```bash
docker-compose up -d
```

#### 2. Chạy Migrations
```bash
docker-compose exec django python manage.py migrate
```

#### 3. Tạo Superuser (Admin)
```bash
docker-compose exec django python manage.py createsuperuser
# Username: admin
# Email: admin@pawnshop.com
# Password: admin123
```

#### 4. Truy Cập Ứng Dụng

| Dịch Vụ | URL | Tên Đăng Nhập |
|---------|-----|---------------|
| **Django (Trang Chủ)** | http://localhost:8000 | - |
| **Admin Panel** | http://localhost:8000/admin | admin / admin123 |
| **PhpMyAdmin** | http://localhost:8080 | pawnshop_user / pawnshop_pass |

---

## 📸 Hình Ảnh Minh Họa

###  SỬ DỤNG DOCKER TRÊN UBUNTU
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/37274279-f223-47dc-8b31-bb8a04b552d6" />  

###  Trang Chủ - Danh Sách Nợ Đến Hạn
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fcdf5617-8439-47cf-9523-4845f1200f28" />  
*Hiển thị các hợp đồng nợ quá hạn và sắp đến hạn*

###  Admin Panel - Quản Lý Hợp Đồng
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6f83fe5c-cb27-4eca-96d4-77d211a89381" />  
*Giao diện admin Django với CRUD operations*

###  Cloudflare Connectors
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/00d079af-7700-410f-bb4c-a614d0a7b8b7" />  
*Danh sách các kết nối Cloudflare Tunnel*

###  Cloudflare Tunnel Details
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/91b59515-93ab-47c3-80c3-9599c5498b06" />  
*Chi tiết tunnel pawnshop-new được public*

###  Trang domain  
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/dd8b6809-d958-43c8-8090-5088ef2e881c" />
*Bảng chi tiết các khoản nợ chưa thanh toán*

---

## 🔧 Các Lệnh Quan Trọng

```bash
# Khởi động
docker-compose up -d

# Dừng
docker-compose down

# Xem logs
docker-compose logs -f django

# Vào container Django
docker-compose exec django bash

# Tạo migrations
docker-compose exec django python manage.py makemigrations

# Chạy migrations
docker-compose exec django python manage.py migrate

# Tạo superuser
docker-compose exec django python manage.py createsuperuser

# Truy cập MySQL
docker-compose exec db mysql -u pawnshop_user -p
```

---

## 🌐 Public Qua Cloudflare Tunnel

```bash
# Cài đặt cloudflared
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb

# Đăng nhập
cloudflared tunnel login

# Tạo tunnel
cloudflared tunnel create pawnshop

# Chạy tunnel
cloudflared tunnel run pawnshop --url http://localhost:8000
```

---

## 📄 License
Học tập và không sử dụng thương mại

**Ngày Nộp Bài:** 09/05/2026
