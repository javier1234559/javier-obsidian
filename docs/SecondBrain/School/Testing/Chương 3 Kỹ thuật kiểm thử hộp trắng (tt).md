---
Created: 08:30 10-10-2023
Link: 
tags:
  - secondbrain
---
# Chương 3 Kỹ thuật kiểm thử hộp trắng (tt)

## 1.Tổng quát về kiểm thử dòng dữ liệu
- Phương pháp kiểm thử dòng dữ liệu sẽ kiểm thử ₫ời sống của từng biến dữ liệu có "tốt lành" trong từng luồng thi hành của chương trình.
- Có thể phát hiện các lỗi
	- Phát biểu gán hay nhập dữ liệu vào biến không ₫úng. 
	- Thiếu ₫ịnh nghĩa biến trước khi dùng
	- Tiên ₫ề sai (do thi hành sai luồng thi hành).
- Mỗi biến nên có chu kỳ sống tốt lành thông qua trình tự 3 bước : ₫ược tạo ra, ₫ược dùng và ₫ược xóa ₫i.
- Thường các ngôn ngữ lập trình cho phép ₫ịnh nghĩa tầm vực cho mỗi biến thuộc 1 trong 3 mức chính yếu : toàn cục, cục bộ trong từng module, cục bộ trong từng hàm chức năng.

## 2. Phân tích đời sống của 1 biến

- Các lệnh truy xuất 1 biến thông qua 1 trong 3 hành ₫ộng sau:
	- d : ₫ịnh nghĩa biến, gán giá trị xác ₫ịnh cho biến (nhập dữ liệu vào biến cũng là hoạt ₫ộng gán trị cho biến).
	-  u : tham khảo trị của biến (thường thông qua biểu thức).
	-  k : hủy (xóa bỏ) biến ₫i.

- Nếu có ý hiệu ~ là miêu tả trạng thái biến đó chưa tồn tại
	-  ~d : biến chưa tồn tại rồi ₫ược ₫ịnh nghĩa với giá trị xác ₫ịnh. 
	-  ~u : biến chưa tồn tại rồi ₫ược dùng ngay (trị nào ?) 
	-  ~k : biến chưa tồn tại rồi bị hủy (lạ lùng).


- 3 hoạt ₫ộng xử lý biến khác nhau kết hợp lại tạo ra 9 cặp ₫ôi hoạt ₫ộng xử lý biến theo thứ tự : 
	- dd : biến ₫ược ₫ịnh nghĩa rồi ₫ịnh nghĩa nữa : hơi lạ, có thể ₫úng và chấp nhận ₫ược, nhưng cũng có thể có lỗi lập trình.
	- du : biến ₫ược ₫ịnh nghĩa rồi ₫ược dùng : trình tự ₫úng và bình thường.
	- dk : biến ₫ược ₫ịnh nghĩa rồi bị xóa bỏ : hơi lạ, có thể ₫úng và chấp nhận ₫ược, nhưng cũng có thể có lỗi lập trình
	- ud : biến ₫ược dùng rồi ₫ịnh nghĩa giá trị mới : hợp lý.
	- uu : biến ₫ược dùng rồi dùng tiếp : hợp lý
	- uk : biến ₫ược dùng rồi bị hủy : hợp lý.
	- kd : biến bị xóa bỏ rồi ₫ược ₫ịnh nghĩa lại : chập nhận ₫ược.
	- ku : biến bị xóa bỏ rồi ₫ược dùng : ₫ây luôn là lỗi.
	- kk : biến bị xóa bỏ rồi bị xóa nữa : có lẽ là lỗi lập trình.

## 3. Đồ thị dòng dữ liệu
##### Độ phức tạp Cyclomatic C



--- 
# References



--- 
# Links to this page

