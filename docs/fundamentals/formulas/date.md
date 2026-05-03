# 📅 Date Functions (Production) / Hàm ngày tháng

---

## 📊 Data / Dữ liệu

| A (Date)   |
| ---------- |
| 01/01/2024 |

---

# 1. Add Months / Cộng tháng

## 🇺🇸 Problem

Add 3 months

## 🇻🇳

Cộng 3 tháng

---

## 📥 Input

A2 = 01/01/2024

---

## 💡 Formula

```excel id="d1"
=EDATE(A2,3)
```

---

## 🔍 Explanation

🇺🇸
Adds months correctly (handles year rollover)

🇻🇳
Tự động xử lý chuyển năm

---

## ✅ Result

→ 01/04/2024

---

## ⚠️ Edge Cases

* Invalid date → error
* Text date → need DATEVALUE

---

# 2. Calculate Age / Tính tuổi

```excel id="d2"
=DATEDIF(A2,TODAY(),"Y")
```

---

## Use Case

* HR system
* Customer profile
