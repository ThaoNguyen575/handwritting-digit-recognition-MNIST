#  Nhận dạng chữ số viết tay từ tập dữ liệu MNIST

## 1. Giới thiệu
Dự án này sử dụng **Deep Learning** để nhận dạng chữ số viết tay (0–9) từ tập dữ liệu **MNIST** nổi tiếng.  
MNIST bao gồm **60,000 ảnh huấn luyện** và **10,000 ảnh kiểm thử**, mỗi ảnh là ảnh xám 28x28 pixel.  

---

## 2. Dataset
- **Nguồn:** [Yann LeCun’s MNIST Database](http://yann.lecun.com/exdb/mnist/)
- **Kích thước ảnh:** 28 x 28 pixel (ảnh xám)
- **Số lớp (labels):** 10 (chữ số từ 0 đến 9)
- **Số mẫu:**
  - Train: 60,000 ảnh
  - Test: 10,000 ảnh

---

## 3. Mô hình
- **Thuật toán:** Convolutional Neural Network (CNN)  
- **Thư viện:** TensorFlow / Keras
## Kiến trúc mô hình
- 3 lớp tích chập (`Conv2D`) với 64 bộ lọc kích thước 3x3, mỗi lớp theo sau là hàm kích hoạt ReLU và lớp MaxPooling (2x2).
- Lớp Flatten để chuyển đổi bản đồ đặc trưng 2 chiều thành vector 1 chiều.
- Hai lớp fully connected (`Dense`) với hàm kích hoạt ReLU, gồm 64 và 32 đơn vị.
- Lớp đầu ra gồm 10 đơn vị với hàm kích hoạt softmax để phân loại đa lớp.

## Huấn luyện
- Hàm mất mát: Sparse Categorical Crossentropy.
- Bộ tối ưu: Adam.
- Số epoch: 5.
- Tỷ lệ dữ liệu dùng để kiểm tra chéo (validation): 30% dữ liệu huấn luyện.


---

## 4. Kết quả
- **Độ chính xác (Accuracy) trên tập kiểm thử:** ~97%
- **Loss:** ~0.07
- **Mô hình dự đoán đúng gần như toàn bộ chữ số viết tay trong tập test.**

---

## 5. Cách chạy dự án
### 5.1. Cài đặt môi trường ảo
```bash
python -m venv mnist_env
mnist_env\Scripts\activate
pip install -r requirements.txt
```
---

## 6.Hướng phát triển
- **Triển khai web app**:  
  - Dùng Streamlit / Flask / FastAPI kết hợp Canvas để người dùng viết trực tiếp trên màn hình.  
  - Dự đoán kết quả ngay lập tức sau khi người dùng hoàn thành nét vẽ (real-time detection).  

- **Mở rộng dữ liệu**:  
  - Bổ sung dataset chứa ký tự phép toán (+, -, ×, ÷) và dấu bằng (=).  
  - Kết hợp nhận dạng chữ số và ký hiệu để đọc toàn bộ phép toán viết tay.

- **Ứng dụng giải toán tự động**:  
  - Nhận diện phương trình viết tay.  
  - Phân tích, giải phương trình và trả kết quả.  
  - Gợi ý các bước giải để hỗ trợ học tập.

- **Cải thiện mô hình**:  
  - Dùng kiến trúc CNN nâng cao (ResNet, EfficientNet) để tăng độ chính xác.  
  - Tối ưu tốc độ dự đoán để đảm bảo trải nghiệm người dùng trên web.
