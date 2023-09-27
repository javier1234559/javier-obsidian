---
Created: "21:08 27-09-2023"
Link: 
tags:
  - zettelkasten
  - zettelkasten/fleeting
---

# Phân tích yêu cầu 
1. Các trang giao diện bên ngoài
- [ ] Home : Hiển thị danh sách từ vựng
	- [ ] Login : Trang đăng nhập
	- [ ] Form : Ô điền từ mới
	- [ ] Table : danh sách từ mới , sửa và xóa


2. Thiết kế DB

```json
USER
{
_id : string,
username : string,
password : string,
_
}


WORD
{
id : string ,
front : string ,
back : string ,
owners : [ObjectID("fs")]
}
```

- [ ] Tạo database trong mongodb
- [ ] Xem sơ về khái niệm webpack và babel
- [ ] Dựng codebase expressjs cho project










--- 
# References

[NextJSVietnam-NestJS Tutorial - Pet Website - Google Docs](https://docs.google.com/document/d/1_WRHoaIVnI2-8RLRah2P6pP-ZbaBfRHStVvCBF3v5xw/edit)

--- 
# Links to this page


