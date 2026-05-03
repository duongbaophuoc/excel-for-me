# 🧠 Logical Functions (Production)

---

## 📊 Data

| Score |
| ----- |
| 95    |
| 70    |

---

# 1. IF Classification

## 🇺🇸 Problem

Classify pass/fail

## 🇻🇳

Phân loại đậu/rớt

---

## Input

A2 = 95

---

## Formula

```excel id="if1"
=IF(A2>=80,"Pass","Fail")
```

---

## Explanation

* Check condition A2>=80
* TRUE → Pass
* FALSE → Fail

---

## Result

95 → Pass

---

## Edge Cases

* Blank cell → returns FALSE branch
* Use:

```excel id="if2"
=IF(A2="","",IF(A2>=80,"Pass","Fail"))
```

---

## Use Case

* Grading system
* Risk classification

---

# 2. IFERROR

```excel id="if3"
=IFERROR(A2/B2,0)
```

→ Avoid crash when divide by zero
