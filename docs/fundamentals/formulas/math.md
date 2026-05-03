# ➗ Math Functions (Production)

---

## 📊 Data

| Product | Sales |
| ------- | ----- |
| A       | 100   |
| A       | 200   |

---

# 1. SUMIFS

## Formula

```excel id="m1"
=SUMIFS(B2:B3,A2:A3,"A")
```

---

## Result

→ 300

---

## Edge Cases

* No match → 0

---

# 2. Sum Top N

```excel id="m2"
=SUM(LARGE(B2:B10,{1,2,3}))
```

---

## Use Case

* Top performers
