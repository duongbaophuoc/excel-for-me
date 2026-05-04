# Feature Engineering in Excel | Kỹ thuật Đặc trưng trong Excel

> **Excel & Google Sheets** | Domains → Data Science

---

## Date-Based Features | Đặc trưng dựa trên Ngày

```
Year:         =YEAR(A2)
Month:        =MONTH(A2)
Day:          =DAY(A2)
Day of week:  =WEEKDAY(A2, 2)    → 1=Mon, 7=Sun
Quarter:      =ROUNDUP(MONTH(A2)/3, 0)
Is Weekend:   =IF(WEEKDAY(A2,2)>5, 1, 0)
Week number:  =WEEKNUM(A2, 2)
```

---

## Binning / Bucketing | Phân nhóm

**Age buckets:**
```
=IFS(A2<18,"Under 18", A2<30,"18-29", A2<45,"30-44", A2<60,"45-59", TRUE,"60+")
```

**Revenue tiers:**
```
=CHOOSE(MATCH(B2, {0,1000000,5000000,20000000}, 1), "Low","Medium","High","Enterprise")
```

---

## Encoding Categorical Variables | Mã hóa biến phân loại

**Label encoding (map to numbers):**
```
=MATCH(A2, {"Low","Medium","High"}, 0) - 1    → 0, 1, 2
```

**One-hot encoding (binary columns):**
```
Is_North: =IF(A2="North", 1, 0)
Is_South: =IF(A2="South", 1, 0)
```

---

## Lag Features | Đặc trưng trễ

**Lag 1 (previous value):**
```
=OFFSET(B2, -1, 0)    → previous row value
```

**Rolling 3-period average:**
```
=AVERAGE(OFFSET(B2, -3, 0, 3, 1))
```

---

## Normalization | Chuẩn hóa

**Min-Max Normalization (0–1):**
```
=(A2 - MIN($A$2:$A$100)) / (MAX($A$2:$A$100) - MIN($A$2:$A$100))
```

**Z-score Standardization:**
```
=(A2 - AVERAGE($A$2:$A$100)) / STDEV($A$2:$A$100)
```

---

*← [Statistics](statistics.md)*
