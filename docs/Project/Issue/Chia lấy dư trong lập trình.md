---
Created: 12:07 05-11-2023
tags:
  - issue
---

# Chia lấy dư trong lập trình
- **Quản lý vòng lặp vô hạn:** Sử dụng phép chia lấy dư để quản lý index trong mảng và đảm bảo vòng lặp vô hạn. Ví dụ:
```python
index = 0
while True:
    element = array[index]
    # Xử lý phần tử
    index = (index + 1) % len(array)  # Lấy index tiếp theo

```

- **Lặp qua mảng trong chu kỳ cố định:** Sử dụng phép chia lấy dư để xác định khi nên thực hiện hành động sau mỗi chu kỳ. Ví dụ:```
```python
n = len(array)  # Độ dài của mảng
k = 3  # Chu kỳ cố định
for i in range(n):
    element = array[i]
    # Xử lý phần tử
    if (i + 1) % k == 0:
        # Thực hiện hành động sau mỗi chu kỳ
```

**Phép Chia Lấy Dư và Phân Loại**:
- Phép chia lấy dư có thể được sử dụng để phân loại dữ liệu thành các nhóm dựa trên các tiêu chí nhất định.
- Ví dụ: Dựa vào kết quả của `số % 2`, bạn có thể phân chia các số thành hai nhóm: số chẵn và số lẻ.
```python
# Phân loại các số từ 1 đến 10 thành số chẵn và số lẻ
numbers = list(range(1, 11))
even_numbers = []
odd_numbers = []

for num in numbers:
    if num % 2 == 0:
        even_numbers.append(num)
    else:
        odd_numbers.append(num)

print("Số chẵn:", even_numbers)
print("Số lẻ:", odd_numbers)

```
**Phép Chia Lấy Dư và Phân Trang**:
- Trong ứng dụng phân trang, phép chia lấy dư thường được sử dụng để xác định trang hiện tại và hiển thị dữ liệu tương ứng trên trang đó.
- Ví dụ: Dựa vào index và số phần tử trên mỗi trang, phép chia lấy dư được sử dụng để tính index bắt đầu và kết thúc cho trang hiện tại, giúp hiển thị dữ liệu trên từng trang phân trang.
  ```python
  # Phân trang dữ liệu
data = list(range(1, 21))
items_per_page = 5
current_page = 3
start_index = (current_page - 1) * items_per_page
page_data = data[start_index:start_index + items_per_page]

print("Dữ liệu trang", current_page, ":", page_data)
```



--- 
# References
[Understanding Your UI as a Tree – React](https://react.dev/learn/understanding-your-ui-as-a-tree)


--- 
# Links to this page

