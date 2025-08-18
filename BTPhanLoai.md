# 📘 Bài tập: Phân loại dữ liệu bằng Cây quyết định

Cho tập dữ liệu sau (10 mẫu), với hai đặc trưng **Tuổi** và **Thu nhập**, cùng nhãn “Mua Laptop” (Có/Không):

| ID | Tuổi | Nhóm tuổi  | Thu nhập | Nhóm thu nhập | Mua Laptop |
| -- | ---- | ---------- | -------- | ------------- | ---------- |
| 1  | 22   | Trẻ        | 35       | Trung bình    | Có         |
| 2  | 25   | Trẻ        | 40       | Cao           | Có         |
| 3  | 28   | Trẻ        | 30       | Trung bình    | Không      |
| 4  | 32   | Trung niên | 45       | Cao           | Có         |
| 5  | 35   | Trung niên | 20       | Thấp          | Không      |
| 6  | 40   | Trung niên | 25       | Thấp          | Không      |
| 7  | 42   | Trung niên | 50       | Cao           | Có         |
| 8  | 48   | Trung niên | 28       | Thấp          | Không      |
| 9  | 50   | Già        | 55       | Cao           | Có         |
| 10 | 55   | Già        | 22       | Thấp          | Không      |

### Quy ước phân loại:

* **Nhóm tuổi**:

  * Trẻ: < 30
  * Trung niên: 30 ≤ tuổi < 50
  * Già: ≥ 50

* **Nhóm thu nhập**:

  * Thấp: < 30
  * Trung bình: 30 ≤ thu nhập < 40
  * Cao: ≥ 40

---

## Yêu cầu:

1. Tính **Entropy gốc** và **Gini gốc** cho toàn bộ tập dữ liệu.
2. Tính **Entropy và Gini** sau khi phân chia theo từng thuộc tính:

   * Thuộc tính “Nhóm tuổi”
   * Thuộc tính “Nhóm thu nhập”
3. Tính **Information Gain** của từng thuộc tính, xác định thuộc tính nào phù hợp nhất để chọn làm nút gốc trong cây quyết định.
4. Vẽ sơ đồ cây quyết định thu được.
5. Kết luận: Với cây này, mô hình phân loại các mẫu dữ liệu sẽ như thế nào?


------------
# BÀI GIẢI CHI TIẾT

## 🔹 Yêu cầu 1: Tính Entropy gốc và Gini gốc

Trong tập dữ liệu:

* Số mẫu: 10
* Nhãn “Có” (Mua laptop): 5
* Nhãn “Không”: 5

👉 **Entropy gốc**:

$$
Entropy(S) = -\frac{5}{10}\log_2\frac{5}{10} - \frac{5}{10}\log_2\frac{5}{10} 
= -0.5 \cdot (-1) - 0.5 \cdot (-1) = 1.000
$$

👉 **Gini gốc**:

$$
Gini(S) = 1 - \left(\frac{5}{10}\right)^2 - \left(\frac{5}{10}\right)^2 
= 1 - 0.25 - 0.25 = 0.5
$$

---

## 🔹 Yêu cầu 2: Tính Entropy & Gini sau khi phân chia

### (a) Thuộc tính **Nhóm tuổi**

* **Trẻ (ID 1–3)**: 3 mẫu (2 Có, 1 Không)

$$
Entropy = -\frac{2}{3}\log_2\frac{2}{3} - \frac{1}{3}\log_2\frac{1}{3} = 0.918
$$

$$
Gini = 1 - \left(\frac{2}{3}\right)^2 - \left(\frac{1}{3}\right)^2 = 0.444
$$

* **Trung niên (ID 4–8)**: 5 mẫu (2 Có, 3 Không)

$$
Entropy = -\frac{2}{5}\log_2\frac{2}{5} - \frac{3}{5}\log_2\frac{3}{5} = 0.971
$$

$$
Gini = 1 - (0.4^2 + 0.6^2) = 0.480
$$

* **Già (ID 9–10)**: 2 mẫu (1 Có, 1 Không)

$$
Entropy = -0.5\log_2 0.5 - 0.5\log_2 0.5 = 1.000
$$

$$
Gini = 1 - (0.5^2 + 0.5^2) = 0.5
$$

👉 **Entropy sau khi chia theo Tuổi**:

$$
Entropy(Tuổi) = \frac{3}{10}\cdot0.918 + \frac{5}{10}\cdot0.971 + \frac{2}{10}\cdot1.000 = 0.959
$$

👉 **Gini sau khi chia theo Tuổi**:

$$
Gini(Tuổi) = \frac{3}{10}\cdot0.444 + \frac{5}{10}\cdot0.480 + \frac{2}{10}\cdot0.5 = 0.474
$$

---

### (b) Thuộc tính **Nhóm thu nhập**

* **Thấp (<30)**: ID 5,6,8,10 → 4 mẫu (0 Có, 4 Không)

$$
Entropy = 0, \quad Gini = 0
$$

* **Trung bình (\[30,40))**: ID 1,3 → 2 mẫu (1 Có, 1 Không)

$$
Entropy = 1, \quad Gini = 0.5
$$

* **Cao (≥40)**: ID 2,4,7,9 → 4 mẫu (4 Có, 0 Không)

$$
Entropy = 0, \quad Gini = 0
$$

👉 **Entropy sau khi chia theo Thu nhập**:

$$
Entropy(Thu nhập) = \frac{4}{10}\cdot0 + \frac{2}{10}\cdot1 + \frac{4}{10}\cdot0 = 0.2
$$

👉 **Gini sau khi chia theo Thu nhập**:

$$
Gini(Thu nhập) = \frac{4}{10}\cdot0 + \frac{2}{10}\cdot0.5 + \frac{4}{10}\cdot0 = 0.1
$$

---

## 🔹 Yêu cầu 3: Information Gain

$$
Gain(Tuổi) = 1 - 0.959 = 0.041
$$

$$
Gain(Thu nhập) = 1 - 0.2 = 0.8
$$

👉 Thu nhập có **Information Gain cao hơn**, là thuộc tính chia tốt nhất.

---

## 🔹 Yêu cầu 4: Vẽ sơ đồ cây quyết định

```
               [Thu nhập?]
              /     |       \
          Thấp     TB       Cao
           |       |         |
         Không   (phân vân) Có
                   / \
                Có   Không
```

* Nếu **Thu nhập = Thấp** → Không mua
* Nếu **Thu nhập = Cao** → Có mua
* Nếu **Thu nhập = Trung bình** → dữ liệu lẫn lộn (1 Có, 1 Không), cần thêm thuộc tính phụ (có thể là Tuổi).

---

## 🔹 Yêu cầu 5: Kết luận

* Mô hình cây quyết định chọn **Thu nhập** làm nút gốc.
* Với dữ liệu này, cây quyết định phân loại gần như **hoàn hảo**, chỉ còn trường hợp **Nhóm thu nhập = Trung bình** cần thêm thông tin để quyết định.
