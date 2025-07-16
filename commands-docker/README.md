# 🚀 Docker Commands Cheat Sheet

## 📄 Giới thiệu

Docker là nền tảng container hoá cho phép package và deploy ứng dụng cùng các phụ thuộc cần thiết. Dưới đây là danh sách tổng hợp các lệnh Docker hay dùng nhất.

---

## 🚧 Docker Engine Commands

| Lệnh             | Mô tả                                                      |
| ---------------- | ---------------------------------------------------------- |
| `docker version` | Xem phiên bản Docker Engine.                               |
| `docker info`    | Xem thông tin chung về Docker Engine, image, container,... |
| `docker help`    | Hiển thị danh sách lệnh hỗ trợ.                            |

---

## 📂 Image Commands

| Lệnh                             | Mô tả                          |
| -------------------------------- | ------------------------------ |
| `docker build -t <name>:<tag> .` | Build image từ Dockerfile.     |
| `docker pull <image>:<tag>`      | Kéo image từ Docker Hub về.    |
| `docker push <image>:<tag>`      | Push image lên Docker Hub.     |
| `docker images`                  | Liệt kê danh sách image local. |
| `docker rmi <image>`             | Xóa image.                     |

---

## 🛋️ Container Commands

| Lệnh                               | Mô tả                                   |
| ---------------------------------- | --------------------------------------- |
| `docker run -it <image>`           | Tạo và chạy container tương tác.        |
| `docker run -d <image>`            | Chạy container ở chế detached.          |
| `docker start <container>`         | Khởi động container đã dừng.            |
| `docker stop <container>`          | Dừng container.                         |
| `docker restart <container>`       | Khởi động lại container.                |
| `docker rm <container>`            | Xóa container.                          |
| `docker ps`                        | Xem danh sách container đang chạy.      |
| `docker ps -a`                     | Xem tất cả container (bao gồm đã dừng). |
| `docker exec -it <container> bash` | Truy cập terminal bên trong container.  |

---

## 🛋️ Volume & Network

| Lệnh                           | Mô tả                  |
| ------------------------------ | ---------------------- |
| `docker volume create <name>`  | Tạo volume mới.        |
| `docker volume ls`             | Danh sách các volume.  |
| `docker volume rm <name>`      | Xóa volume.            |
| `docker network ls`            | Danh sách các network. |
| `docker network create <name>` | Tạo network mới.       |
| `docker network rm <name>`     | Xóa network.           |

---

## 🔧 Khác

* `docker system prune` – Xóa tất cả container, image, volume không dùng.
* `docker stats` – Theo dõi tài nguyên của container.
* `docker inspect <container|image>` – In ra cấu hình chi tiết JSON.

---

## 📃 Tài liệu tham khảo

* [Docker CLI Docs](https://docs.docker.com/engine/reference/commandline/docker/)
* [Docker Cheat Sheet PDF](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
* [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)

---
