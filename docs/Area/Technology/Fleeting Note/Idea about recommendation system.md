---
Created: 11:52 07-12-2023
tags:
  - area
  - area/technology
---


Theo như mình tìm hiểu thì sẽ 3 loại hệ thống gợi ý chính 

- ## Popular-based : Gợi ý theo mức độ phổ biến 
	- Thuật toán này sẽ đơn giản nhất và lọc theo mức độ quan tâm nhất, nó sẽ phù hợp cho khách hàng mới , hệ thống còn ít tương tác
	- Cách thi hành:
		- Có thể sắp xếp và chọn top item theo giá trị rating trung bình 
		- Dùng công thức IMDB weighted `WR = (v ÷ (v+m)) × R + (m ÷ (v+m)) × C` để có thể khiến giúp điều chỉnh số lượng rating tối thiếu để lọt vào bảng xếp hạng tránh trường hợp 1 vote 5 sao làm nó lọt top
			- Trong đó : 
				-  `R` is the average rating for the item.
				- `v` is the number of votes for the item.
				- `m` is the minimum votes required to be listed in the popular items(defined by > percentile 80 of total votes)
				- `C` is the average rating across the whole dataset.
	- Nhược điểm : Tất cả user đều nhận recommend giống nhau
- ## Content-based : Gợi ý theo nội dung tương tự
	- Thuật toán này sẽ gợi ý nội dung item liên quan đến sản phẩm dựa vào trường name, tag, description, ảnh,.. Nó sẽ phù hợp cho việc 
	- Cách thi hành:
	- Nhược điểm : Việc gợi ý sẽ tiếp tục gợi ý các item giống nhau mà người dùng tương tác mà không đề xuất những cái mới
- ## Collaborative filtering : Gợi ý theo lọc công tác
	- Có các biến thể 
		- Collaborative filtering — Memory-based — Affinity matrix
		- Collaborative filtering — Memory-based — TruncatedSVD (Sklearn)
		- Collaborative filtering — Model-based — Funk MF (Surprise)
		- Collaborative filtering — Model-based — GMF (Keras)
		- Collaborative filtering — Model-based — NCF (Recommender)
- Other states of the art algorithms

