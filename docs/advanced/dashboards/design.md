# Dashboard Design | Thiết kế Dashboard

> **Excel & Google Sheets** | Advanced → Dashboards

---

## Dashboard Principles | Nguyên tắc Dashboard

**EN:** A great dashboard answers 3 questions at a glance: What happened? Why? What should I do?  
**VI:** Dashboard tốt trả lời 3 câu hỏi một cái nhìn: Điều gì đã xảy ra? Tại sao? Phải làm gì?

---

## Layout Structure | Cấu trúc bố cục

```
+------------------------------------------+
|  HEADER: Title + Date + Key Message       |
+------------+------------+----------------+
|  KPI 1     |  KPI 2     |   KPI 3        |
+------------+------------+----------------+
|                                           |
|   Main Chart (large, dominant)            |
|                                           |
+--------------------+----------------------+
| Secondary Chart 1  | Secondary Chart 2   |
+--------------------+----------------------+
|   Detail Table / Drill-down               |
+------------------------------------------+
```

---

## Chart Selection Guide | Hướng dẫn chọn biểu đồ

| Data Type | Best Chart | Biểu đồ tốt nhất |
|---|---|---|
| Trend over time | Line chart | Biểu đồ đường |
| Category comparison | Bar/Column chart | Biểu đồ cột/thanh |
| Part of whole | Pie / Donut | Biểu đồ tròn |
| Distribution | Histogram | Biểu đồ tần suất |
| Correlation | Scatter plot | Biểu đồ phân tán |
| Progress to goal | Gauge / Bullet | Biểu đồ tiến độ |

---

## Conditional Formatting for KPIs | Định dạng có điều kiện cho KPI

**Traffic Light System:**
```
Green  (>=100% of target):  =C2/D2 >= 1
Yellow (80–99% of target):  =AND(C2/D2>=0.8, C2/D2<1)
Red    (<80% of target):    =C2/D2 < 0.8
```

**Sparklines:** Insert → Sparklines → Line/Column/Win-Loss

---

## Interactive Elements | Yếu tố tương tác

- **Slicers** (connected to PivotTables) for filter buttons
- **Drop-down validation** for user-selectable parameters
- **Form Controls** (checkbox, combo box) for dynamic toggles
- **OFFSET + MATCH** for interactive chart ranges

---

*[KPI Dashboard →](kpi.md)*
