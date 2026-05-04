# Data Aggregation | Tổng hợp Dữ liệu

> **Excel & Google Sheets** | Domains → Data Analysis

---

## SUMIF / SUMIFS

**Syntax:** `=SUMIFS(sum_range, criteria1_range, criteria1, ...)`

**Single condition:**
```
=SUMIF(A2:A100, "North", C2:C100)
```

**Multiple conditions:**
```
=SUMIFS(C2:C100, A2:A100, "North", B2:B100, "Apple")
```

---

## COUNTIF / COUNTIFS

```
=COUNTIF(A2:A100, "North")
=COUNTIFS(A2:A100, "North", B2:B100, ">1000000")
```

---

## AVERAGEIF / AVERAGEIFS

```
=AVERAGEIF(A2:A100, "North", C2:C100)
=AVERAGEIFS(C2:C100, A2:A100, "North", B2:B100, "Apple")
```

---

## SUMPRODUCT for Complex Aggregation

**Multi-condition with operators:**
```
=SUMPRODUCT((A2:A100="North")*(C2:C100>1000000)*D2:D100)
```

**Weighted average:**
```
=SUMPRODUCT(B2:B10 * C2:C10) / SUM(C2:C10)
```

---

## Dynamic Aggregation with OFFSET

**Sum last N rows:**
```
=SUM(OFFSET(C2, COUNT(C:C)-N, 0, N, 1))
```

---

*← [Data Cleaning](data-cleaning.md) | [Pivot Table →](pivot-table.md)*
