# 🎮 Hướng Dẫn Học Docker Cơ Bản

Chào mừng bạn đến với repo hướng dẫn học Docker! Đây là tài liệu dành cho người mới bắt đầu, giúc bạn hiểu và thực hành các khái niệm cơ bản về Docker một cách có hệ thống.

<img src="https://nimtechnology.com/wp-content/uploads/2021/07/8323.1565281088.png" alt="docker overview" width="600" />

---

## 📚 Mục lục

1. [Docker là gì?](#docker-là-gì)
2. [Cài đặt Docker trên Ubuntu](#cài-đặt-docker-trên-ubuntu)
3. [Các lệnh Docker cơ bản](#các-lệnh-docker-cơ-bản)
4. [Làm việc với Dockerfile](#làm-việc-với-dockerfile)
5. [Docker Compose là gì?](#docker-compose-là-gì)
6. [Thực hành dự án mini](#thực-hành-dự-án-mini)
7. [Tài liệu tham khảo](#tài-liệu-tham-khảo)

---

## Docker là gì?

> Docker là một nền tảng cho phép bạn đóng gói ứng dụng và các phụ thuộc của nó vào một đơn vị có thể chạy độc lập – gọi là **container**.

<img src="https://www.altexsoft.com/static/blog-post/2023/11/50d965c7-b468-4de6-ad45-d8c8cb385a02.jpg" alt="docker container vs vm" width="500" />

### 🔧 Tại sao nên dùng Docker?
- Dễ dàng triển khai trên mọi môi trường
- Nhẹ hơn so với VM
- Tách biệt môi trường
- Dễ backup, version và chia sẻ

---

## Cài đặt Docker trên Ubuntu

```bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install docker-ce -y
```

### Kiểm tra cài đặt:
```bash
docker --version
sudo systemctl status docker
```

### Thêm quyền chạy không cần sudo:
```bash
sudo usermod -aG docker $USER
su - $USER
groups
```

---

## Các lệnh Docker cơ bản

| Lệnh | Mô tả |
|------|-------|
| `docker run hello-world` | Kiểm tra cài đặt Docker |
| `docker pull <image>` | Tải image |
| `docker images` | Liệt kê image |
| `docker ps` | Xem container đang chạy |
| `docker ps -a` | Xem tất cả container |
| `docker ps -l` | Xem container gần nhất |
| `docker stop <id>` | Dừng container |
| `docker stop $(docker ps -q)` | Dừng toàn bộ container đang chạy |
| `docker rm <id>` | Xoá container |
| `docker rm $(docker ps -aq)` | Xoá toàn bộ container (kể cả đã stop) |
| `docker rmi <image>` | Xoá image |
| `docker rmi $(docker images -q)` | Xoá toàn bộ image |
| `docker exec -it <container_id> bash` | Truy cập vào container đang chạy với bash shell |
| `docker logs <container_id>` | Xem log của container |
| `docker inspect <container_id>` | Xem chi tiết config của container |
| `docker network ls` | Liệt kê mạng Docker |
| `docker volume ls` | Liệt kê volumes |
| `docker stats` | Xem tài nguyên đang dùng của container |
| `docker system prune` | Xoá toàn bộ unused containers, networks, volumes và images |


---

## Làm việc với Dockerfile

Tạo file `Dockerfile`:
```Dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "main.py"]
```

Xây dựng image:
```bash
docker build -t my-python-app .
docker run my-python-app
```

---

## Docker Compose là gì?

> Docker Compose giúc bạn định nghĩa và chạy nhiều container cùng lúc thông qua file `docker-compose.yml`

<img src="https://docs.docker.com/compose/images/architecture.svg" alt="docker compose architecture" width="600" />

Ví dụ `docker-compose.yml`:
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: redis
```

Chạy dịch vụ:
```bash
docker compose up
```

---

## Thực hành dự án mini

Gợi ý:
- Tạo Flask API chạy trong Docker
- Kết hợp với Redis (cache)
- Deploy bằng Docker Compose

---

## Tài liệu tham khảo
- [Docker Docs](https://docs.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Play with Docker](https://labs.play-with-docker.com/)
- [DigitalOcean - Cài Docker Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)

---

> 👨‍💻 Hãy clone repo này, thử từng bước và commit lại theo tiến trình học của bạn nhé!
