---
Created: 09:29 28-06-2024
tags:
  - area
  - area/technology
---

# SSH key and SSH key agent
SSH Key
- **Mô tả**: Một cặp khóa mã hóa bao gồm khóa riêng tư (private key) và khóa công khai (public key). Sử dụng để xác thực và bảo mật kết nối SSH.
- **Cách tạo**: Sử dụng lệnh `ssh-keygen` với tùy chọn `-t` để chọn thuật toán (như RSA, ED25519). Bạn có thể thêm tùy chọn `-C` để gắn email hoặc tên người dùng.
- **Thuật toán**: Thuật toán phổ biến bao gồm RSA và ED25519. RSA được sử dụng rộng rãi nhưng chậm hơn so với ED25519, một thuật toán dựa trên số học elliptic nhanh hơn và an toàn hơn.
- Tạo SSH key 
- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
	- `-t`: Thuật toán (RSA, ED25519)
	- `-b`: Độ dài bit của khóa (4096 bits là khuyến nghị)
	- `-C`: Gắn email hoặc tên người dùng
### SSH-Agent
- **Mô tả**: Dịch vụ chạy trong nền, quản lý các khóa SSH của bạn. Lưu trữ khóa riêng tư và tự động cung cấp chúng cho các yêu cầu SSH.
- **Sử dụng**: Khởi động bằng `eval "$(ssh-agent -s)"` và thêm khóa vào bằng `ssh-add ~/.ssh/id_rsa` (hoặc tên file khóa khác).
### Vòng đời xử lý kết nối SSH trên GitHub
1. **Tạo SSH Key**: Sử dụng `ssh-keygen` để tạo cặp khóa.
2. **Thêm khóa công khai vào GitHub**: Chia sẻ khóa công khai với GitHub để xác thực.
3. **Clone Project**: Khi clone một dự án từ GitHub, GitHub sẽ sử dụng khóa công khai của bạn để xác minh yêu cầu.
### Passphrase
- **Mô tả**: Mật khẩu bổ sung cho khóa SSH, tăng cường bảo mật bằng cách yêu cầu nhập passphrase mỗi khi sử dụng khóa.
- **Ví dụ bảo mật**: Một passphrase nên chứa ít nhất 8 ký tự, bao gồm chữ hoa, chữ thường, số, và ký tự đặc biệt. Ví dụ: `P@ssw0rd`.



## How to to add SSH key to Github account 
- https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
- TLDR:
	- `cat ~/.ssh/id_ed25519.pub` in Linux
	- `clip < ~/.ssh/id_ed25519.pub` in Window
	- `pbcopy < ~/.ssh/id_ed25519.pub` in MacOS

--- 
# References

--- 
# Links to this page


[[Linux]]
