# ➗ Math Functions (Production) / Hàm toán học

---

## 📊 Data

| Product | Sales |
| ------- | ----- |
| A       | 100   |
| A       | 200   |
| B       | 300   |

---

# 1. SUMIFS / Tổng có điều kiện

## 🇺🇸 Problem

Sum sales of product A

## 🇻🇳

Tính tổng sản phẩm A

---

## 📥 Input

Criteria = "A"

---

## 💡 Formula

```excel id="m1"
=SUMIFS(B2:B4,A2:A4,"A")
```

---

## 🔍 Explanation

🇺🇸

* B2:B4 → sum range
* A2:A4 → criteria range

🇻🇳

* B → vùng tính tổng
* A → vùng điều kiện

---

## ✅ Result

→ 300

---

## ⚠️ Edge Cases

* No match → 0
* Text vs number mismatch

---

# 2. Top N Values / Top N

```excel id="m2"
=SUM(LARGE(B2:B4,{1,2}))
```

---

## Result

→ 500

---

## Use Case

* Top sales analysis
