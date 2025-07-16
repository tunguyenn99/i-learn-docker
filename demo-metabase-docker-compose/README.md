# 🐳 Học Docker Compose qua ví dụ Metabase

## 🚀 Giới thiệu Docker Compose

**Docker Compose** là công cụ giúp bạn định nghĩa và khởi chạy **nhiều container Docker cùng lúc** thông qua một file cấu hình duy nhất: `docker-compose.yml`.

### ✅ Lợi ích:
- Tự động hoá việc tạo cấu hình và khởi động nhiều container.
- Dễ dàng chia sẻ cấu hình (team production CI/CD).
- Chuẩn hoá môi trường phát triển.

---

## 📄 Cấu trúc cơ bản của `docker-compose.yml`

```yaml
version: '3.8'
services:
  <service_name>:
    image: <image_name>
    ports:
      - "host:container"
    environment:
      - VAR=value
    volumes:
      - <volume_name>:<path>
volumes:
  <volume_name>:
```

---

## 📌 Bắt buộc và tuỳ chọn

| Thành phần         | Bắt buộc | Ghi chú |
|--------------------|----------|--------|
| `version`          | ✅ | Khuyến nghị là lấy version `3` hoặc `3.x` (file đang dùng là `3.8`) |
| `services`         | ✅        | Bắt buộc để định nghĩa các container cần chạy. |
| `image` hoặc `build` | ✅     | Phải có ít nhất một trong hai để xác định container. |
| `ports`            | ❌        | Dùng khi cần expose cổng cho người dùng truy cập. |
| `environment`      | ❌        | Cần nếu container yêu cầu biến môi trường. |
| `volumes`          | ❌        | Hữu ích để lưu dữ liệu vĩnh viễn nhưng không bắt buộc. |
| `depends_on`       | ❌        | Giúp khởi chạy đúng thứ tự không ảnh hưởng chức năng. |
| `networks`       | ❌        | Giúp tuỳ chỉnh mạng giữa các container |
---

## 🧪 Ví dụ: Triển khai Metabase bằng Docker Compose

```yaml
version: '3'
services:
  metabase:
    image: metabase/metabase:latest
    container_name: metabase
    ports:
      - "3000:3000"
    environment:
      - MB_DB_FILE=/metabase-data/metabase.db
    volumes:
      - metabase-data:/metabase-data

volumes:
  metabase-data:
```

---

## ▶️ Cách chạy

```bash
docker-compose up -d
```


Sau khi chạy lệnh `up` để khởi tạo container, bạn truy cập: http://localhost:3000 để xem giao diện của Metabase. 

Kết quả đạt được:

<img src='images/metabase-ui.png' width=800>

Nếu không cần dùng nữa thì chạy lệnh sau để tắt container.

```bash
docker-compose down
```

---

## 🎁 Mở rộng: Dùng PostgreSQL thay vì SQLite

```yaml
version: '3.8'

services:
  metabase:
    image: metabase/metabase:latest
    ports:
      - "3000:3000"
    environment:
      - MB_DB_TYPE=postgres
      - MB_DB_DBNAME=metabase
      - MB_DB_PORT=5432
      - MB_DB_USER=metabase
      - MB_DB_PASS=metabase
      - MB_DB_HOST=db
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: metabase
      POSTGRES_PASSWORD: metabase
      POSTGRES_DB: metabase
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

---

## 📚 Tài liệu học thêm
- https://docs.docker.com/compose/
- https://hub.docker.com/r/metabase/metabase
- https://compose-spec.io

---

Happy Dockering! 🐳