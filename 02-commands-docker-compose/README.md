# 🐳 Docker Compose Commands & Flags

## 📌 Giới thiệu

Docker Compose là công cụ dùng để định nghĩa và chạy các ứng dụng multi-container Docker. Với một file `docker-compose.yml`, bạn có thể cấu hình tất cả các dịch vụ, volume, network,... và chạy chỉ bằng một dòng lệnh.

---

## 🚀 Các lệnh cơ bản

| Lệnh                                      | Mô tả                                                  |
| ----------------------------------------- | ------------------------------------------------------ |
| `docker compose up`                       | Tạo và chạy toàn bộ dịch vụ được khai báo.             |
| `docker compose down`                     | Dừng và xóa toàn bộ container, network, volume đã tạo. |
| `docker compose build`                    | Build lại image cho các service.                       |
| `docker compose start`                    | Khởi động lại các container đã dừng.                   |
| `docker compose stop`                     | Dừng các container đang chạy.                          |
| `docker compose restart`                  | Restart toàn bộ dịch vụ.                               |
| `docker compose ps`                       | Hiển thị danh sách container đang được quản lý.        |
| `docker compose logs`                     | Xem log của các dịch vụ.                               |
| `docker compose exec <service> <command>` | Chạy lệnh bên trong container đang chạy.               |
| `docker compose run <service> <command>`  | Tạo và chạy container tạm thời từ một service.         |

---

## ⚙️ Các flag thường dùng

### Với `docker compose up`:

* `-d` – Chạy ở chế độ nền (detached).
* `--build` – Build lại image trước khi chạy.
* `--force-recreate` – Buộc recreate container, kể cả khi không có thay đổi.
* `--remove-orphans` – Xóa các container không còn được định nghĩa trong compose file.

### Với `docker compose down`:

* `--volumes` – Xóa cả volume khi dừng.
* `--remove-orphans` – Xóa các container không được định nghĩa trong file `docker-compose.yml`.

### Với `docker compose logs`:

* `-f` – Theo dõi log realtime (giống `tail -f`).
* `--tail <number>` – Chỉ lấy số dòng log cuối cùng (ví dụ: `--tail 100`).

---

## 🧪 Ví dụ thực tế

```bash
# Khởi chạy project ở chế độ nền
docker compose up -d

# Build lại image và chạy
docker compose up --build

# Dừng và xóa toàn bộ container + volume
docker compose down --volumes

# Xem log realtime
docker compose logs -f

# Truy cập vào container app
docker compose exec app bash
```

---

## 📚 Tài liệu tham khảo

* [Docker Compose CLI Docs](https://docs.docker.com/compose/reference/)
* [Compose Spec](https://compose-spec.io)

---
