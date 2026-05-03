# 🔍 Lookup Functions (Production) / Hàm tra cứu 

---

## 📊 Sample Dataset / Dữ liệu mẫu

| ID  | Product | Price |
| --- | ------- | ----- |
| P01 | Apple   | 10    |
| P02 | Banana  | 20    |
| P03 | Orange  | 30    |

---

# 1. Basic Lookup (XLOOKUP)

---

## 🇺🇸 Problem

Find product name using ID

## 🇻🇳 Bài toán

Tìm tên sản phẩm từ mã

---

## 📥 Input

Lookup value: `"P02"`

---

## 💡 Formula

```excel id="l7t3m0"
=XLOOKUP("P02", A2:A4, B2:B4)
```

---

## 🔍 Step-by-step Explanation

🇺🇸

* A2:A4 → lookup array
* B2:B4 → return array
* "P02" → value to find

🇻🇳

* A2:A4 → cột tìm kiếm
* B2:B4 → cột trả về
* "P02" → giá trị cần tìm

---

## ✅ Result

→ Banana

---

## ⚠️ Edge Cases

* If not found → #N/A
* Fix:

```excel id="nm0x48"
=XLOOKUP("P05", A2:A4, B2:B4, "Not Found")
```

---

## 🎯 Use Case

* Product lookup
* Mapping IDs
* Dashboard filters

---

# 2. VLOOKUP (Legacy)

---

## Problem

Same task using older Excel

---

## Formula

```excel id="41q8nm"
=VLOOKUP("P02", A2:C4, 2, FALSE)
```

---

## ⚠️ Limitation

* Cannot lookup left
* Slower than XLOOKUP

---

# 3. INDEX + MATCH (Flexible)

---

## Formula

```excel id="v3p1ys"
=INDEX(B2:B4, MATCH("P02", A2:A4, 0))
```

---

## Why use this?

🇺🇸
More flexible than VLOOKUP

🇻🇳
Linh hoạt hơn VLOOKUP

---

## Edge Case

MATCH returns #N/A → wrap IFERROR
