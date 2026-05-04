# KPI Dashboard | Dashboard KPI Tổng hợp

> **Excel & Google Sheets** | Dashboards

---

## Overview | Tổng quan

**EN:** A universal KPI tracking dashboard adaptable to any business function: sales, ops, HR, finance, or customer success.

**VI:** Dashboard theo dõi KPI tổng quát có thể điều chỉnh cho mọi bộ phận: bán hàng, vận hành, nhân sự, tài chính hoặc chăm sóc khách hàng.

---

## Universal KPI Card Formula | Công thức Thẻ KPI Chung

| Element | Formula | Description |
|---|---|---|
| Current Value | `=SUM(DataRange)` | Actual this period |
| Target | `=VLOOKUP(Period, Targets, 2, 0)` | Period target |
| Achievement % | `=Current/Target` | Format as % |
| vs Last Period | `=(Current-LastPeriod)/ABS(LastPeriod)` | MoM/YoY |
| Status | `=IF(Current/Target>=1,"✅","⚠️")` | Quick indicator |
| Trend Arrow | `=IF(vs_Last>0,"▲ "&TEXT(vs_Last,"0%"),"▼ "&TEXT(vs_Last,"0%"))` | Direction |

---

## Common KPI Sets by Function | Bộ KPI theo Bộ phận

### Sales | Bán hàng
```
Revenue, # New Customers, Win Rate, Average Deal Size,
Sales Cycle Length, Pipeline Value
```

### Customer Success | Chăm sóc Khách hàng
```
NPS Score, CSAT, Churn Rate, Customer LTV,
First Response Time, Resolution Rate
```

### Operations | Vận hành
```
On-Time Delivery %, Defect Rate, Inventory Turnover,
Fulfillment Cost, OEE (Overall Equipment Effectiveness)
```

### HR | Nhân sự
```
Headcount, Turnover Rate, Time-to-Fill,
Training Hours/Employee, Absenteeism Rate
```

---

## Sparkline KPIs | KPI với Sparkline

**EN:** Add mini trend charts next to KPI values using Sparklines.  
**VI:** Thêm biểu đồ xu hướng nhỏ bên cạnh giá trị KPI bằng Sparklines.

1. Select cell next to KPI value
2. Insert → Sparklines → Line
3. Set data range to last 12 months of that KPI

---

## Dynamic Period Selection | Chọn Kỳ Động

**Setup:** Cell B1 = Data Validation dropdown → list of periods (Jan, Feb... or Q1, Q2...)

**Formula responds to selection:**
```
=SUMIF(DataSheet!MonthCol, B1, DataSheet!ValueCol)
```

**With CHOOSE for quarters:**
```
=CHOOSE(B1, Q1_Value, Q2_Value, Q3_Value, Q4_Value)
```

---

## Executive Summary Table | Bảng Tóm tắt Điều hành

| KPI | Target | Actual | Achievement | Status |
|---|---|---|---|---|
| Revenue | 10B | `=formula` | `=C2/B2` | `=IF(D2>=1,"✅","⚠️")` |
| New Customers | 500 | `=formula` | `=C3/B3` | `=IF(D3>=1,"✅","⚠️")` |
| Gross Margin | 40% | `=formula` | `=C4/B4` | `=IF(D4>=0.95,"✅","⚠️")` |

---

*← [Finance Dashboard](finance-dashboard.md)*
