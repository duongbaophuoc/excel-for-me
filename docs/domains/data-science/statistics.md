# Statistical Functions | Hàm Thống kê

> **Excel & Google Sheets** | Domains → Data Science

---

## Descriptive Statistics | Thống kê mô tả

| Function | Formula | Meaning |
|---|---|---|
| Mean | `=AVERAGE(A2:A100)` | Trung bình |
| Median | `=MEDIAN(A2:A100)` | Trung vị |
| Mode | `=MODE(A2:A100)` | Giá trị xuất hiện nhiều nhất |
| Std Dev (sample) | `=STDEV(A2:A100)` | Độ lệch chuẩn mẫu |
| Std Dev (population) | `=STDEVP(A2:A100)` | Độ lệch chuẩn tổng thể |
| Variance | `=VAR(A2:A100)` | Phương sai |
| Min / Max | `=MIN/MAX(A2:A100)` | Nhỏ nhất / Lớn nhất |
| Range | `=MAX(A2:A100)-MIN(A2:A100)` | Khoảng biến thiên |
| Skewness | `=SKEW(A2:A100)` | Độ lệch phân phối |
| Kurtosis | `=KURT(A2:A100)` | Độ nhọn phân phối |

---

## Percentiles and Quartiles | Bách phân vị và Tứ phân vị

```
=PERCENTILE(A2:A100, 0.75)    → 75th percentile
=QUARTILE(A2:A100, 1)         → Q1 (25th)
=QUARTILE(A2:A100, 3)         → Q3 (75th)
IQR = Q3 - Q1
```

---

## Z-Score | Điểm Z

**Formula:**
```
=(A2 - AVERAGE($A$2:$A$100)) / STDEV($A$2:$A$100)
```

**EN:** Z-score > 2 or < -2 may indicate outliers.  
**VI:** Z-score > 2 hoặc < -2 có thể là ngoại lệ.

---

## NORM.DIST / NORM.INV

**Normal distribution probability:**
```
=NORM.DIST(x, mean, std_dev, TRUE)    → cumulative probability
=NORM.INV(probability, mean, std_dev) → value at probability
```

---

## Correlation Matrix | Ma trận tương quan

**For pairs:** `=CORREL(A2:A100, B2:B100)`

**Full matrix:** Use Data → Data Analysis → Correlation

---

*[Feature Engineering →](feature-engineering.md)*
