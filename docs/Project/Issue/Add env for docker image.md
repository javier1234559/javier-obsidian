---
Created: 00:18 27-05-2024
tags:
  - issue
---

TLDR: 

Để build và chạy Docker image, bạn cần sử dụng lệnh `docker build` và `docker run`. Đầu tiên, bạn cần build Docker image từ Dockerfile của bạn. Mở terminal và điều hướng đến thư mục chứa Dockerfile của bạn, sau đó chạy lệnh sau:

```bash
docker build -t your-image-name .
```

Trong đó `your-image-name` là tên bạn muốn đặt cho Docker image của mình. Dấu chấm (`.`) cuối cùng chỉ định context của Docker build là thư mục hiện tại.

Sau khi build thành công, bạn có thể chạy Docker image bằng lệnh sau:

```bash
docker run -p 8080:8080 --env-file ./.env your-image-name
```

Trong đó:

- `-p 8080:8080` map cổng 8080 của máy host với cổng 8080 của Docker container. Bạn có thể thay đổi số cổng này tùy theo ứng dụng của bạn.
- `--env-file ./.env` đặt các biến môi trường từ file `.env`. Bạn cần thay `./.env` bằng đường dẫn tới file `.env` của bạn.
- `your-image-name` là tên của Docker image bạn muốn chạy.

Sau khi chạy lệnh này, Docker container sẽ bắt đầu chạy và bạn có thể truy cập ứng dụng của mình tại `http://localhost:8080` (hoặc cổng khác tùy theo cấu hình của bạn).