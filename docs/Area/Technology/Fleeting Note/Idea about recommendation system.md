---
Created: 11:52 07-12-2023
tags:
  - area
  - area/technology
---


*Theo như mình tìm hiểu thì sẽ 3 loại hệ thống gợi ý chính*

![[Pasted image 20231207124229.png]]

# Lý thuyết về các phương pháp gợi ý 

- ## Popular-based : Gợi ý theo mức độ phổ biến 
	- Thuật toán này sẽ đơn giản nhất và lọc theo mức độ quan tâm nhất, nó sẽ phù hợp cho khách hàng mới , hệ thống còn ít tương tác .Phù hợp đặt ở trang chủ hệ thống 
	- Ý tưởng cách thi hành:
		- Có thể sắp xếp và chọn top item theo giá trị rating trung bình 
		- Dùng công thức IMDB weighted `WR = (v ÷ (v+m)) × R + (m ÷ (v+m)) × C` để có thể khiến giúp điều chỉnh số lượng rating tối thiếu để lọt vào bảng xếp hạng tránh trường hợp 1 vote 5 sao làm nó lọt top
			- Trong đó : 
				-  `R` is the average rating for the item.
				- `v` is the number of votes for the item.
				- `m` is the minimum votes required to be listed in the popular items(defined by > percentile 80 of total votes)
				- `C` is the average rating across the whole dataset.
	- Nhược điểm : Tất cả user đều nhận recommend giống nhau 
	 
	![[Pasted image 20231207124427.png]]
- ## Content-based : Gợi ý theo nội dung tương tự
	- Thuật toán này sẽ gợi ý nội dung item liên quan đến sản phẩm dựa vào trường name, tag, description, image,.... Thuật tóan này phù hợp đặt ở trang chi tiết item 
	- Ý tưởng thi hành:
		- User based : Gợi ý theo  
	- Nhược điểm : Việc gợi ý sẽ tiếp tục gợi ý các item giống nhau mà người dùng tương tác mà không đề xuất những cái mới
- ## Collaborative filtering : Gợi ý theo lọc công tác
	- Thuật toán sẽ gợi ý dựa theo sự tương đồng tương tác của các user với nhau . Một user A và B cùng quan tâm đế item1 thì khi user A quan tâm đến item2 thì dẫn đế khả năng user B cũng quan tâm item2 . Thuật toán này phù hợp với hệ thống nhiều tương tác , thích hợp đặt ở trang chi tiết item nó thường bổ sung cho thuật toán content-based giúp gợi ý các sản phẩm mới và mang tính cá nhân hơn
	- Có các biến thể 
		- **Collaborative Filtering — Memory-based — Affinity Matrix:**
				- Sử dụng ma trận tương đồng (affinity matrix) để đo lường sự tương đồng giữa người dùng hoặc sản phẩm. Dựa trên đánh giá hoặc hành vi của người dùng để xác định mối quan hệ giữa họ.
		- **Collaborative Filtering — Memory-based — TruncatedSVD (Sklearn):**
			- Sử dụng phương pháp SVD cắt giảm (Truncated Singular Value Decomposition) để giảm chiều của ma trận tương đồng. Giúp giảm kích thước của ma trận và tăng tốc quá trình tính toán.
		- **Collaborative Filtering — Model-based — Funk MF (Surprise):**
			- Sử dụng mô hình học máy để dự đoán đánh giá của người dùng cho các sản phẩm. Mô hình Funk MF (Matrix Factorization) giảm chiều của ma trận đánh giá thành các ma trận con để học các đặc trưng ẩn.
		- **Collaborative Filtering — Model-based — GMF (Keras):**
			- Sử dụng mô hình học máy sâu (deep learning) với mạng nơ-ron để học các biểu diễn số học (embeddings) cho người dùng và sản phẩm. GMF (Generalized Matrix Factorization) tối ưu hóa các trọng số của mô hình để dự đoán đánh giá.
		- **Collaborative Filtering — Model-based — NCF (Recommender):**
			- Sử dụng mô hình NCF (Neural Collaborative Filtering) cũng dựa trên deep learning. Kết hợp cả mô hình matrix factorization và mạng nơ-ron để học được cả sự tương đồng giữa người dùng và sản phẩm và các đặc trưng ẩn khác.
	- Ý tưởng thi hành : 
		- User based : Dựa trên tương quan giữa các người dùng để đề xuất sản phẩm. Nó xây dựng một ma trận đánh giá dựa trên sự tương quan giữa các người dùng, sau đó gợi ý các sản phẩm mà các người dùng tương quan đã đánh giá và người dùng hiện tại chưa đánh giá.
		- Item based : Gợi ý dựa theo lịch sử tương tác của người dùng đến item , nó sẽ gợi ý các nhóm item tương tự cho người dúng đó , nhưng nó khác ở với content based ở chỗ là không hạn chế ở việc tương quan nội dung mà có thể thêm tương quan về lịch sử đã mua hàng ..
	- Nhược điểm : Không phù hợp với hệ thống data ít tương tác và khá phức tạp 
- ## Other states of the art algorithms
	- Mỗi thuật toán đề có ưu nhược khác nhau  và hybrid tận dụng cùng luc chúng cũng là một cách để tạo nên hệ thống gợi ý hiệu quả
	- Ngoài ra còn rất nhiều biến thể và thư viện gợi ý gồm các tài liệu chúng ta có thể tìm hiểu thêm như 
		- [Bilateral Variational Autoencoder (BiVAE)](https://archive.ph/o/SEmw5/https://github.com/microsoft/recommenders/blob/main/examples/02_model_collaborative_filtering/cornac_bivae_deep_dive.ipynb)
		- [Bayesian Personalized Ranking (BPR)](https://archive.ph/o/SEmw5/https://github.com/microsoft/recommenders/blob/main/examples/02_model_collaborative_filtering/cornac_bpr_deep_dive.ipynb)
		- [Light Graph Convolutional Network (LigthGCN)](https://archive.ph/o/SEmw5/https://github.com/microsoft/recommenders/blob/main/examples/02_model_collaborative_filtering/lightgcn_deep_dive.ipynb)
		- [Transformaer4Rec provided by Nvidia-Merlin](https://archive.ph/o/SEmw5/https://github.com/NVIDIA-Merlin/Transformers4Rec)
		- [grahamjenson/list_of_recommender_systems: A List of Recommender Systems and Resources (github.com)](https://github.com/grahamjenson/list_of_recommender_systems)


# Ý tưởng vận dụng vào website
Với mong muốn tích hợp vào website thì các bước mà mình nghĩ cần thực hiện là
- Chọn phương pháp in memory hay model based. 
	- Trong đó in memory nghĩa là chúng ta sẽ không lưu lại kết quả mà mỗi lần chúng ta sẽ tính lại một recommend mới .
		- Uư điểm:  Phương pháp này đơn giản cho các web nhỏ và cũng như luôn đảm bảo kết quả gợi ý luôn sát với data thật nhất 
		- Nhược điểm: Sẽ rất tốn tài nguyên , đối với data lớn thì sẽ rất mất thời gian phản hồi
	- Chọn model based thì chúng ta sẽ train thành một model đánh giá ,lưu lại và sử dụng cho những lần sau
		- Ưu điểm : Tiết kiệm tài nguyên, lưu lại các model đã tính toán. Phù hợp với dữ liệu lớn.
		- Nhược điểm : Cần có dữ liệu đủ lớn và đại diện để huấn luyện mô hình. Dữ liệu mới cần được cập nhật đều đặn.
- Nên chọn phương pháp gì , theo ý tưởng của mình thì sẽ chọn thuật toán content based và dặt các items được gợi ý ở trang detail item . Vì nó phù hợp với trang web ít tương tác người dùng và đủ đơn giản để mình làm quen 



# References
[A Complete Guide To Recommender System — Tutorial with Sklearn, Surprise, Keras, Recommender | by Pathairush Seeda | in Towards Data Science - Freedium](https://freedium.cfd/https://towardsdatascience.com/a-complete-guide-to-recommender-system-tutorial-with-sklearn-surprise-keras-recommender-5e52e8ceace1)