# 🏸 HƯỚNG DẪN CHẠY AU BADMINTON SYSTEM

## BƯỚC 1 — Mở Terminal trong thư mục backend

```
cd d:\wwweb\backend
```

## BƯỚC 2 — Tạo file cấu hình .env

Tạo file `.env` trong `d:\wwweb\backend\` với nội dung:

```
DB_SERVER=localhost
DB_PORT=1433
DB_NAME=AuDB
DB_USER=sa
DB_PASSWORD=MẬT_KHẨU_SQL_SERVER_CỦA_BẠN

PORT=3000
```

> ⚠️ Thay `MẬT_KHẨU_SQL_SERVER_CỦA_BẠN` bằng password thực của SQL Server

## BƯỚC 3 — Cài đặt thư viện

```bash
npm install
```

Sẽ cài: express, mssql, cors, dotenv, nodemon

## BƯỚC 4 — Chạy server

```bash
npm run dev
```

Hoặc:
```bash
node server.js
```

## BƯỚC 5 — Mở trình duyệt

Truy cập: **http://localhost:3000/index.html**

## Kiểm tra kết nối AuDB

```
http://localhost:3000/api/health
```

Nếu thành công sẽ trả về:
```json
{ "success": true, "status": "OK", "database": "AuDB connected" }
```

## API Endpoints

| Method | URL | Mô tả |
|--------|-----|-------|
| GET | /api/courts | Danh sách sân |
| GET | /api/courts/:id | Chi tiết sân |
| POST | /api/courts | Thêm sân (Admin) |
| PATCH | /api/courts/:id/iot | Điều khiển đèn IoT |
| DELETE | /api/courts/:id | Xóa sân (Admin) |
| GET | /api/bookings | Danh sách đặt sân |
| POST | /api/bookings | **Đặt sân mới** (tự kiểm tra trùng lịch) |
| PATCH | /api/bookings/:id/status | Xác nhận/Hủy |
| GET | /api/bookings/stats/summary | Thống kê Dashboard |
| GET | /api/shop | Pro-Shop items |

## Cấu trúc thư mục

```
d:\wwweb\
├── index.html          ← Trang chủ
├── login.html          ← Đăng nhập
├── courts.html         ← Danh sách sân
├── court-detail.html   ← Chi tiết + đặt sân
├── booking-history.html← Lịch sử đặt
├── admin/
│   ├── dashboard.html
│   ├── courts.html
│   └── bookings.html
├── assets/css/style.css
└── backend/            ← Node.js Express API
    ├── server.js
    ├── db.js           ← Kết nối AuDB SQL Server
    ├── .env            ← Cấu hình (tạo tay)
    ├── package.json
    └── routes/
        ├── courts.js
        ├── bookings.js
        └── shop.js
```
