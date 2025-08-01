## **BÀI THỰC HÀNH: LÀM QUEN VỚI PYTHON**

### **1. Chuẩn bị môi trường**

**Tuỳ chọn (chọn 1):**

* Cài Python + IDLE hoặc VS Code trên máy cá nhân.
  ([https://www.python.org/downloads/](https://www.python.org/downloads/))
* Dùng **Google Colab**: truy cập [https://colab.research.google.com](https://colab.research.google.com)

---

### **2. Làm quen cú pháp cơ bản**

#### **Bài 1.1: In ra dòng chữ "Hello Python"**

```python
print("Hello Python")
```

> ✅ **Yêu cầu**: Chạy chương trình, sửa `"Hello Python"` thành tên bạn, ví dụ `"Hello, I'm An"`.

---

#### **Bài 1.2: Các phép toán số học cơ bản**

```python
a = 10
b = 3
print("a + b =", a + b)
print("a - b =", a - b)
print("a * b =", a * b)
print("a / b =", a / b)
print("a // b =", a // b)   # chia lấy nguyên
print("a % b =", a % b)     # chia lấy dư
print("a ** b =", a ** b)   # lũy thừa
```

> **Yêu cầu**: Tự thay đổi giá trị `a`, `b` và quan sát kết quả.

---

### **3. Tương tác với người dùng**

#### **Bài 1.3: Nhập từ bàn phím và tính toán**

```python
name = input("Bạn tên gì? ")
print("Chào bạn", name)

x = int(input("Nhập số nguyên x: "))
y = int(input("Nhập số nguyên y: "))
print("Tổng x + y =", x + y)
```

> **Yêu cầu**: Thêm các phép toán trừ, nhân, chia.

---

### **4. Bài tập ứng dụng tổng hợp**

#### **Bài 1.4: Tính diện tích hình chữ nhật**

```python
chieu_dai = float(input("Nhập chiều dài: "))
chieu_rong = float(input("Nhập chiều rộng: "))
dien_tich = chieu_dai * chieu_rong
print("Diện tích hình chữ nhật là:", dien_tich)
```

> ✅ **Mở rộng**: Tính chu vi hình chữ nhật.

---

#### **Bài 1.5: Tính tổng ba chữ số của một số nguyên có 3 chữ số**

```python
so = int(input("Nhập số nguyên có 3 chữ số: "))
a = so // 100         # chữ số hàng trăm
b = (so // 10) % 10   # chữ số hàng chục
c = so % 10           # chữ số hàng đơn vị
tong = a + b + c
print("Tổng 3 chữ số là:", tong)
```
---
## **BÀI THỰC HÀNH: Vòng lặp và cấu trúc dữ liệu cơ bản trong Python**

## **1. Vòng lặp `for`**

### **Bài 2.1: In các số từ 1 đến 10**

```python
for i in range(1, 11):
    print(i)
```

> ✅ `range(start, end)` tạo dãy từ `start` đến `end-1`

---

### **Bài 2.2: Tính tổng 1 + 2 + ... + n**

```python
n = int(input("Nhập n: "))
tong = 0
for i in range(1, n+1):
    tong += i
print("Tổng từ 1 đến", n, "là:", tong)
```

---

### **Bài 2.3: In bảng cửu chương**

```python
for i in range(1, 10):
    for j in range(1, 10):
        print(f"{i} x {j} = {i*j}")
    print("-" * 20)
```

---

## **2. Vòng lặp `while`**

### **Bài 2.4: Nhập số cho đến khi đúng**

```python
x = 0
while x != 5:
    x = int(input("Nhập số 5 để thoát: "))
print("Bạn đã nhập đúng!")
```

---

### **Bài 2.5: Kiểm tra số nguyên tố**

```python
n = int(input("Nhập số nguyên: "))
is_prime = True
if n < 2:
    is_prime = False
else:
    i = 2
    while i*i <= n:
        if n % i == 0:
            is_prime = False
            break
        i += 1

if is_prime:
    print(n, "là số nguyên tố")
else:
    print(n, "không phải số nguyên tố")
```

---

## **3. Danh sách (List)**

### **Bài 2.6: Khai báo và truy xuất**

```python
ds = [5, 10, 15, 20]
print("Phần tử đầu:", ds[0])
print("Tổng phần tử:", sum(ds))
```

---

### **Bài 2.7: Nhập danh sách số nguyên từ người dùng**

```python
n = int(input("Nhập số phần tử: "))
lst = []
for i in range(n):
    x = int(input(f"Phần tử thứ {i+1}: "))
    lst.append(x)

print("Danh sách vừa nhập:", lst)
print("Giá trị lớn nhất:", max(lst))
print("Trung bình:", sum(lst) / len(lst))
```

---

## **4. Từ điển (Dictionary)**

### **Bài 2.8: Tạo từ điển và truy cập**

```python
sv = {
    "name": "Nguyễn Văn A",
    "mssv": "123456",
    "lop": "CTK43"
}
print("Tên:", sv["name"])
print("MSSV:", sv["mssv"])
```

---

### **Bài 2.9: Duyệt từ điển**

```python
for key in sv:
    print(key, ":", sv[key])
```

---

### **Bài 2.10: Từ điển đếm số lần xuất hiện**

```python
s = input("Nhập chuỗi: ")
freq = {}

for ch in s:
    if ch in freq:
        freq[ch] += 1
    else:
        freq[ch] = 1

print("Tần số xuất hiện:", freq)
```

### 📌 **Tài liệu tham khảo**

* Python Documentation: [https://docs.python.org/3/](https://docs.python.org/3/)
* W3Schools Python Tutorial: [https://www.w3schools.com/python/](https://www.w3schools.com/python/)
* Google Colab Help: [https://colab.research.google.com/notebooks/intro.ipynb](https://colab.research.google.com/notebooks/intro.ipynb)
