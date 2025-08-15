# Mô tả các tham số trong đầu ra Association Rules

Khi khai phá luật kết hợp (Association Rules Mining) - ví dụ dùng **Apriori** hoặc **FP-Growth** - đầu ra thường gồm các cột sau:

---

## 1. Cấu trúc luật
| Cột | Mô tả |
|-----|-------|
| **antecedents** | Tập hợp điều kiện (vế trái của luật). Ví dụ: `{A, B} → {C}`, thì `{A, B}` là antecedents. |
| **consequents** | Tập hợp kết quả (vế phải của luật). Ví dụ: `{A, B} → {C}`, thì `{C}` là consequents. |

---

## 2. Các chỉ số tần suất
| Cột | Mô tả | Công thức |
|-----|-------|----------|
| **antecedent support** | Tỷ lệ giao dịch chứa *tất cả* item trong antecedents. | $$\frac{\text{số giao dịch chứa antecedents}}{\text{tổng giao dịch}}$$ |
| **consequent support** | Tỷ lệ giao dịch chứa *tất cả* item trong consequents. | Tương tự antecedent support nhưng cho consequents. |
| **support** | Tỷ lệ giao dịch chứa **cả antecedents và consequents** cùng lúc. | $$\frac{\text{số giao dịch chứa cả A và C}}{\text{tổng giao dịch}}$$ |

---

## 3. Các chỉ số đánh giá sức mạnh luật
| Cột | Mô tả | Công thức |
|-----|-------|----------|
| **confidence** | Xác suất xảy ra consequents khi antecedents đã xảy ra. | $$\frac{\text{support}(A \cup C)}{\text{support}(A)}$$ |
| **lift** | Mức độ ảnh hưởng của antecedents lên consequents so với ngẫu nhiên. <br> - **Lift > 1**: quan hệ dương. <br> - **Lift = 1**: không có quan hệ. <br> - **Lift < 1**: quan hệ âm. | $$\frac{\text{confidence}(A \to C)}{\text{support}(C)}$$ |
| **leverage** | Độ chênh giữa xác suất thực tế và xác suất kỳ vọng nếu A và C độc lập. | $$\text{support}(A \cup C) - \text{support}(A) \times \text{support}(C)$$ |
| **conviction** | Đo mức tin tưởng rằng antecedents xảy ra thì consequents sẽ không bị "vi phạm". | $$\frac{1 - \text{support}(C)}{1 - \text{confidence}(A \to C)}$$ |

---

## 4. Các chỉ số nâng cao
| Cột | Mô tả | Công thức |
|-----|-------|----------|
| **representativity** | Mức độ đại diện của luật so với tập dữ liệu (lọc luật trùng hoặc ít ý nghĩa). | $$\frac{\text{support}(A \cup C)}{\max(\text{support}(A), \text{support}(C))}$$ |
| **zhangs_metric** | Thước đo của Zhang, cân bằng giữa lift và leverage, ổn định khi support thấp. | $$\frac{\text{support}(A \cup C) - \text{support}(A) \times \text{support}(C)}{\max(\text{support}(A \cup C) \times (1 - \text{support}(A)), \text{support}(A) \times (\text{support}(C) - \text{support}(A \cup C)))}$$ |
| **jaccard** | Độ tương đồng giữa A và C. | $$\frac{\text{support}(A \cup C)}{\text{support}(A) + \text{support}(C) - \text{support}(A \cup C)}$$ |
| **certainty** | Mức cải thiện xác suất của C khi biết A. | $$\frac{\text{confidence}(A \to C) - \text{support}(C)}{1 - \text{support}(C)}$$ |
| **kulczynski** | Trung bình cộng của P(C\|A) và P(A\|C). | $$\frac{\text{confidence}(A \to C) + \text{confidence}(C \to A)}{2}$$ |

---

## 5. Ghi chú
- $$A$$: Antecedents  
- $$C$$: Consequents  
- $$\text{support}(X)$$: Tỷ lệ giao dịch chứa tập X.  
- Các chỉ số nên được xem xét **kết hợp** để chọn luật ý nghĩa, tránh chỉ dựa vào một giá trị đơn lẻ.
