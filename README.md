# GAN
**GAN** (Generative Adversarial Networks) - mạng đối nghịch tạo sinh, là mô hình thuộc lớp generative model, được huấn luyện thông qua adversarial training và có mục tiêu tạo ra dữ liệu giống với dữ liệu trong tập huấn luyện

Cấu trúc của GAN gồm 2 mô hình chính là generator và discriminator xung đột lợi ích với nhau, trong đó: 

- **Generator** : giống như mô hình sinh, học cách sinh ra dữ liệu giả giống với dữ liệu trong tập huấn luyện để đánh lừa discriminator
- **Discriminator** : giống như mô hình phân lớp, quan sát dữ liệu và phân biệt dữ liệu thật - giả (từ tập huấn luyện hay do generator sinh ra)

**Xây dựng mô hình**
- Sử dụng tập dữ liệu MNIST
- Discriminstor đơn giản là 1 mạng phân lớp tuyến tính
+ Sử dụng 3 hidden layers + 1 fully-connected layer
+ Mỗi layer có 1 hàm kích hoạt LeakyReLU
- Generator xây dựng tương tự discriminator, tuy nhiên áp dụng hàm tanh cho output

**Tính toán hàm loss**
- Discriminator loss bao gồm loss của ảnh thật + giả
+ Sử dụng BCEWithLogitsLoss-kết hợp hàm sigmoid và BCE loss
- Generator loss gồm loss của ảnh giả

**Huấn luyện**
- Discriminator: tính toán loss trên ảnh thật, dữ liệu huấn luyện và tạo ra ảnh giả, tiếp tục trên ảnh giả, ảnh snh ra và biểu diễn lan truyền ngược + tối ưu
- Generator: tạo ra ảnh giả và tính toán loss
