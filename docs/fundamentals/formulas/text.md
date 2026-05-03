# 🔤 Text Functions (Production) / Hàm xử lý chuỗi

---

## 📊 Sample Data / Dữ liệu mẫu

| A (Full Name)    |
| ---------------- |
| John Michael Doe |
| Anna             |

---

# 1. Extract First Name / Tách tên

## 🇺🇸 Problem

Extract first name from full name

## 🇻🇳 Bài toán

Tách tên từ họ tên đầy đủ

---

## 📥 Input

A2 = "John Michael Doe"

---

## 💡 Formula

```excel id="t1"
=LEFT(A2,FIND(" ",A2)-1)
```

---

## 🔍 Explanation

🇺🇸

* FIND(" ",A2) → first space position
* LEFT → extract text before space

🇻🇳

* FIND tìm vị trí dấu cách đầu tiên
* LEFT lấy phần bên trái

---

## ✅ Result

→ John

---

## ⚠️ Edge Cases

❗ If only one word (Anna) → error

Fix:

```excel id="t2"
=IFERROR(LEFT(A2,FIND(" ",A2)-1),A2)
```

---

## 🎯 Use Case

* CRM cleaning
* User data parsing

---

# 2. Extract Last Name / Tách họ

## 💡 Formula

```excel id="t3"
=RIGHT(A2,LEN(A2)-FIND("@",SUBSTITUTE(A2," ","@",LEN(A2)-LEN(SUBSTITUTE(A2," ","")))))
```

---

## 🔍 Explanation

🇺🇸

* Replace last space with @
* FIND position
* Extract right side

🇻🇳

* Thay khoảng trắng cuối bằng @
* Tìm vị trí → cắt bên phải

---

## ✅ Result

→ Doe
