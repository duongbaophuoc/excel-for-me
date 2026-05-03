# 📅 Date Functions (Production)

---

## 📊 Data

A2 = 01/01/2024

---

# 1. Add Months

```excel id="d1"
=EDATE(A2,3)
```

→ 01/04/2024

---

# 2. Age Calculation

```excel id="d2"
=DATEDIF(A2,TODAY(),"Y")
```

---

## Edge Cases

* Invalid date → error

---

## Use Case

* HR system
