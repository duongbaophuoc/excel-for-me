# KPI Dashboard | Dashboard KPI

> **Excel & Google Sheets** | Advanced → Dashboards

---

## Key KPI Formulas | Công thức KPI chính

### Achievement Rate | Tỷ lệ hoàn thành
```
=Actual/Target
```

### Month-over-Month Growth | Tăng trưởng tháng/tháng
```
=(Current_Month - Previous_Month) / ABS(Previous_Month)
```

### Year-to-Date (YTD) | Lũy kế năm
```
=SUMIFS(Sales, Year, YEAR(TODAY()), Month, "<="&MONTH(TODAY()))
```

### Rolling 12-Month Average | Trung bình 12 tháng liên tiếp
```
=AVERAGE(OFFSET(B2, MATCH(MAX(A:A),A:A,0)-12, 0, 12, 1))
```

---

## KPI Card Template | Mẫu thẻ KPI

| Element | Formula | Format |
|---|---|---|
| Current Value | `=SUM(SalesData[Sales])` | Currency |
| vs Target | `=C2/D2-1` | Percentage, +/- |
| vs Last Year | `=(C2-E2)/E2` | Percentage |
| Trend Arrow | `=IF(F2>0,"▲","▼")` | Green/Red |

---

## Dynamic KPI by Period | KPI động theo kỳ

**Setup:** Cell B1 = dropdown (Jan, Feb, Mar...)

**Formula:**
```
=SUMIF(MonthCol, B1, SalesCol)
```

With INDIRECT:
```
=SUM(INDIRECT("Sales_"&B1))   → references named range Sales_Jan, Sales_Feb...
```

---

*← [Design](design.md)*
