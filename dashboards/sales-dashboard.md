# Sales Dashboard | Dashboard Bán hàng

> **Excel & Google Sheets** | Dashboards

---

## Overview | Tổng quan

**EN:** A complete sales dashboard template tracking revenue, pipeline, rep performance, and product mix.

**VI:** Mẫu dashboard bán hàng đầy đủ theo dõi doanh thu, pipeline, hiệu suất nhân viên và cơ cấu sản phẩm.

---

## Sheet Structure | Cấu trúc Sheet

```
Sheet: RAW_SALES    → Transaction-level sales data
Sheet: TARGETS      → Monthly targets per rep and region
Sheet: CALC         → Intermediate calculations
Sheet: DASHBOARD    → Visual output (charts + KPIs)
Sheet: PARAMS       → Config: date ranges, filter values
```

---

## RAW_SALES Schema | Sơ đồ dữ liệu thô

| Column | Field | Type | Example |
|---|---|---|---|
| A | Date | Date | 2024-01-15 |
| B | OrderID | Text | ORD-0001 |
| C | SalesRep | Text | Nguyen Van An |
| D | Region | Text | North |
| E | Product | Text | Product A |
| F | Category | Text | Electronics |
| G | Quantity | Number | 5 |
| H | UnitPrice | Currency | 2,000,000 |
| I | Revenue | Formula | `=G2*H2` |
| J | COGS | Currency | 1,200,000 |
| K | GrossProfit | Formula | `=I2-J2*G2` |

---

## Key KPI Formulas | Công thức KPI chính

### Total Revenue MTD | Doanh thu tháng này
```
=SUMPRODUCT(
  (MONTH(RAW_SALES!A:A)=MONTH(TODAY()))*
  (YEAR(RAW_SALES!A:A)=YEAR(TODAY()))*
  RAW_SALES!I:I
)
```

### Revenue vs Target (%) | Doanh thu vs Mục tiêu
```
=MTD_Revenue / VLOOKUP(MONTH(TODAY()), TARGETS!A:B, 2, 0)
```

### Top Performing Rep | Nhân viên xuất sắc nhất
```
=INDEX(
  RAW_SALES!C:C,
  MATCH(
    MAXIFS(RAW_SALES!I:I, MONTH(RAW_SALES!A:A), MONTH(TODAY())),
    RAW_SALES!I:I, 0
  )
)
```

### MoM Revenue Growth | Tăng trưởng tháng/tháng
```
=(MTD_Revenue - Last_Month_Revenue) / ABS(Last_Month_Revenue)
```

### Win Rate (if pipeline data available)
```
=COUNTIF(Pipeline!E:E, "Won") / COUNTA(Pipeline!E:E)
```

---

## Sales by Region | Doanh thu theo Khu vực

```
North: =SUMIF(RAW_SALES!D:D, "North", RAW_SALES!I:I)
South: =SUMIF(RAW_SALES!D:D, "South", RAW_SALES!I:I)
Central: =SUMIF(RAW_SALES!D:D, "Central", RAW_SALES!I:I)
```

---

## Rep Leaderboard | Bảng xếp hạng Nhân viên

```
Formula for rank column:
=RANK(C2, $C$2:$C$20, -1)   → Rank by revenue descending
```

**Full leaderboard with SUMIF:**
```
Rep Revenue: =SUMIF(RAW_SALES!C:C, A2, RAW_SALES!I:I)
Rep Target:  =VLOOKUP(A2, TARGETS!A:C, 3, 0)
Achievement: =B2/C2
```

---

## Recommended Charts | Biểu đồ đề xuất

| Chart | Type | Data |
|---|---|---|
| Monthly Revenue Trend | Line | Month vs Revenue (12 months) |
| Revenue by Region | Donut | Region vs Revenue |
| Rep Leaderboard | Horizontal Bar | Rep vs Revenue (sorted) |
| Product Mix | Treemap / Bar | Category vs Revenue |
| Daily Sales Heatmap | Conditional Format | Day vs Week grid |

---

## Conditional Formatting Rules | Quy tắc Định dạng điều kiện

**Achievement KPI colors:**
```
>= 100%: Green  (#00B050)  → =C2/D2>=1
>= 80%:  Yellow (#FFEB9C)  → =AND(C2/D2>=0.8, C2/D2<1)
< 80%:   Red    (#FF0000)  → =C2/D2<0.8
```

---

*← [Dashboards](.) | [Finance Dashboard →](finance-dashboard.md)*
