---
Created: 08:06 10-10-2023
Link: 
tags:
  - secondbrain
---

# Chương 3 Kỹ thuật kiểm thử hộp trắng

## 1. Tổng quát về kiểm thử hộp trắng
Kiểm thử hộp trắng là kiểm thử một thành phần mềm (hàm chức năng, module chức năng ,phân hệ chức năng , .. )
Có 2 hoạt ₫ộng kiểm thử hộp trắng : 
- Kiểm thử luồng điều khiển : tập trung kiểm thử thuật giải chức năng. 
- Kiểm thử dòng dữ liệu : tập trung kiểm thử ₫ời sống của từng biến dữ liệu ₫ược dùng trong thuật giải.
## 2. Một số thuật ngữ về kiểm thử luồng điều khiển
- Đường thi hành (Execution path) : là 1 kịch bản thi hành đơn vị phần mềm tương ứng, cụ thể nó là danh sách có thứ tự các lệnh ₫ược thi hành ứng với 1 lần chạy cụ thể của ₫ơn vị phần mềm, bắt đầu từ ₫iểm nhập của đơn vị phần mềm đến điểm kết thúc của đơn vị phần mềm.
## 3.Các cấp phủ kiểm thử (Coverage)
Phủ cấp 1
Phủ cấp 2
Phủ cấp 3
Phủ cấp 4
## 4. Đồ thị dòng điều khiển
Gồm 2 loại thành phần : các nút và các cung nối kết giữa chúng. Các loại nút trong ₫ồ thị dòng ₫iều khiển :

![[Pasted image 20231010081835.png]]
Miêu tả các cấu trúc ₫iều khiển phổ dụng :
![[Pasted image 20231010081906.png]]

##### Độ phức tạp Cyclomatic C
Độ phức tạp Cyclomatic C = V(G) của ₫ồ thị dòng ₫iều khiển ₫ược tính bởi 1 trong các công thức sau : 
- `V(G) = E - N + 2`, trong ₫ó E là số cung, N là số nút của ₫ồ thị. 
- `V(G) = P + 1`, nếu là đồ thị dòng ₫iều khiển nhị phân (chỉ chứa các nút quyết ₫ịnh luận lý - chỉ có 2 cung xuất True/False) và P số nút quyết ₫ịnh. Độ phức tạp Cyclomatic C chính là số ₫ường thi hành tuyến tính ₫ộc lập của TPPM cần kiểm thử.

## 5. Đồ thị dòng ₫iều khiển cơ bản

## 6. Qui trình kiểm thử hộp trắng
1. Từ TPPM cần kiểm thử, xây dựng ₫ồ thị dòng ₫iều khiển tương ứng, rồi chuyển thành ₫ồ thị dòng ₫iều khiển nhị phân, rồi chuyển thành ₫ồ thị dòng ₫iều khiển cơ bản.
2.  Tính ₫ộ phức tạp Cyclomatic của ₫ồ thị (C = P +1). 
3.  Xác ₫ịnh C ₫ường thi hành tuyến tính ₫ộc lập cơ bản cần kiểm thử (theo thuật giải chi tiết ở slide kế).
4. Tạo từng test case cho từng ₫ường thi hành tuyến tính ₫ộc lập cơ bản. 
5.  Thực hiện kiểm thử trên từng test case. 6. So sánh kết quả có ₫ược với kết quả ₫ược kỳ vọng. 7. Lập báo cáo kết quả ₫ể phản hồi cho những người có liên qu

Qui trình xác ₫ịnh các ₫ường tuyến tính ₫ộc lập
Thiết kế các test case
Kiểm thử vòng lặp



--- 
# References
https://fhqx.hcmute.edu.vn/pluginfile.php/2880151/mod_resource/content/1/Chuong03.pdf


--- 
# Links to this page

