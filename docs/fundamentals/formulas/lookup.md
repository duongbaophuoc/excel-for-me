# 🔍 Lookup Functions / Hàm tra cứu

---

## 🇺🇸 English

### 1. XLOOKUP ⭐
=XLOOKUP(A2, A:A, B:B, "Not Found")

→ Find value in column A, return from column B

Use case:
- Product lookup
- Customer ID mapping

---

### 2. VLOOKUP
=VLOOKUP(A2, A:B, 2, FALSE)

⚠️ Limitation: cannot lookup left

---

### 3. INDEX + MATCH ⭐
=INDEX(B:B, MATCH(A2, A:A, 0))

→ Flexible and faster in large datasets

---

## 🇻🇳 Tiếng Việt

### 1. XLOOKUP ⭐
=XLOOKUP(A2, A:A, B:B, "Không tìm thấy")

→ Tra cứu dữ liệu

Ứng dụng:
- Tìm sản phẩm
- Mapping ID

---

### 2. VLOOKUP
=VLOOKUP(A2, A:B, 2, FALSE)

⚠️ Không tìm trái được

---

### 3. INDEX + MATCH ⭐
=INDEX(B:B, MATCH(A2, A:A, 0))
