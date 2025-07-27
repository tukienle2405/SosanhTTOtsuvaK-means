# SosanhTTOtsuvaK-means
# So sách thuật toán Otsu va thuật toán K-means
## Nhóm thực hiện: 09_NMXLA_HK242
## Giảng viên: Đỗ Hữu Quân

# Giới thiệu
Đồ án này nhằm mục đích áp dụng thuật toán Otsu và thuật toán K-Means để thực hiện phân đoạn ảnh là một trong những bước cơ bản và quan trọng trong xử lý ảnh số. <br>
Thuật toán Otsu được sử dụng để tự động tìm ngưỡng tối ưu, phân tách đối tượng và nền trong ảnh xám, giúp làm nổi bật các chi tiết chính. <br>
Thuật toán K-Means được áp dụng để phân nhóm các điểm ảnh (pixel) của ảnh màu thành k cụm dựa trên sự tương đồng màu sắc, giúp đơn giản hóa ảnh hoặc tách các vùng màu đặc trưng. <br>
Mục tiêu chính của hai đoạn code: <br>
Làm rõ sự khác biệt giữa phương pháp phân ngưỡng đơn giản (Otsu) và phân đoạn dựa trên phân cụm (K-Means). <br>
Giúp sinh viên nắm vững các thao tác tiền xử lý, tách nền, và nhận diện vùng quan trọng trong ảnh.<br>

# Công nghệ sử dụng <br>
Hai đoạn code trên sử dụng các công nghệ và thư viện sau: <br>
Python: Ngôn ngữ lập trình chính.<br>
Pillow (PIL): Dùng để đọc ảnh (Image.open) và chuyển đổi ảnh sang thang xám (convert('L')). <br>
NumPy: Dùng để chuyển ảnh thành mảng số học (np.asarray) và thực hiện các phép tính logic, xử lý dữ liệu ảnh. <br>
Scikit-Image (skimage.filters.threshold_otsu): Dùng để tính ngưỡng Otsu tự động. <br>
Matplotlib (pyplot): Dùng để hiển thị ảnh gốc và ảnh đã phân ngưỡng trực quan trên Python. <br>

# Chi tiết các phép biến đổi & công thức
1. Thuật toán Otsu (Otsu Thresholding)
Mục đích:
Tự động tìm ngưỡng t để phân tách đối tượng (foreground) và nền (background) trong ảnh xám.
Tăng khả năng nhận diện chi tiết và tách rõ ràng vùng ảnh cần quan tâm.
Công thức toán học:
Otsu tìm ngưỡng t sao cho phương sai giữa các lớp được tối đa hóa:
<img width="417" height="66" alt="Image" src="https://github.com/user-attachments/assets/0b4f2c81-0ef3-4d58-a566-c0b830e41ad7" /> <br>
Ví dụ:
Giả sử ngưỡng Otsu tính được t=120, pixel có giá trị r=150 sẽ được gán thành 1 (trắng), còn r=90 sẽ thành 0 (đen).
Code chính:
<img width="776" height="144" alt="Image" src="https://github.com/user-attachments/assets/10f080b8-3ae1-44c4-bdd4-8be28dd278df" /> <br>
ω 1,ω 2: Xác suất của 2 lớp (pixel < t và pixel ≥ t). <br>
μ 1,μ 2: Giá trị trung bình của 2 lớp.<br>
2. Thuật toán K-Means (K-Means Clustering)<br>
Mục đích: <br>
Phân đoạn ảnh màu thành k cụm dựa trên sự tương đồng về màu (RGB).<br>
Giảm độ phức tạp của ảnh, làm rõ các vùng có màu sắc đặc trưng.<br>
Công thức toán học:<br>
Tối ưu hàm mất mát:<br>
<img width="257" height="88" alt="Image" src="https://github.com/user-attachments/assets/7be4b115-dbc1-47aa-a616-f75ba31e0eff" /> <br>
x: Pixel trong không gian màu (R, G, B).<br>
i: Tâm của cụm thứ <br>
k: Số cụm màu.<br>
Ví dụ:<br>
Với k=5, ảnh sẽ được gom thành 5 màu chính đại diện cho các cụm.<br>
Code chính:<br>
<img width="688" height="50" alt="Image" src="https://github.com/user-attachments/assets/46c1c6b6-9292-479d-baf9-d7a850b4493b" /> <br>
<img width="870" height="69" alt="Image" src="https://github.com/user-attachments/assets/17b9e3bc-0bb7-4d09-ab5d-540c1bfebcaa" /> <br>
<img width="778" height="37" alt="Image" src="https://github.com/user-attachments/assets/c45bb66e-b39d-4231-a9bb-7babc1542786" /> <br>
# So sách: <br>
1. Nguyên lý hoạt động<br>
Otsu: <br>
Dùng histogram của ảnh xám để tìm một ngưỡng duy nhất <br>
t tách ảnh thành 2 lớp: nền (background) và đối tượng (foreground).<br>
Thường áp dụng cho ảnh grayscale.<br>
K-Means:<br>
Gom pixel của ảnh màu vào k cụm dựa trên sự tương đồng về màu sắc (RGB).<br>
Phân đoạn ảnh thành nhiều vùng màu, không chỉ 2 lớp.<br>
2. Đầu vào và đầu ra<br>
Otsu:<br>
Đầu vào: Ảnh xám (grayscale).<br>
Đầu ra: Ảnh nhị phân (2 màu: trắng và đen).<br>
K-Means:<br>
Đầu vào: Ảnh màu (RGB).<br>
Đầu ra: Ảnh phân đoạn với k màu đại diện cho các cụm.<br>
3. Ưu điểm<br>
Otsu:<br>
Nhanh, đơn giản, không cần chọn tham số nhiều.<br>
Hiệu quả với ảnh có histogram 2 đỉnh rõ rệt.<br>
K-Means:<br>
Áp dụng được cho ảnh màu, cho phép phân đoạn nhiều vùng (không giới hạn 2 lớp).<br>
Cho kết quả phân cụm màu chi tiết hơn.<br>
4. Nhược điểm<br>
Otsu:<br>
Chỉ phân tách được 2 lớp (foreground và background).<br>
Không hoạt động tốt với ảnh màu hoặc ảnh có nhiều mức xám phức tạp.<br>
K-Means:<br>
Chậm hơn do phải lặp nhiều lần để hội tụ.<br>
Phải chọn trước số cụm k (nếu chọn sai, kết quả không tốt).<br>


