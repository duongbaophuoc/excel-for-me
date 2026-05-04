# Time Series Forecasting | Dự báo Chuỗi thời gian

> **Excel & Google Sheets** | Domains → Forecasting

---

## Forecast Sheet | Trang tính Dự báo

**EN:** Excel 365 has a built-in Forecast Sheet using exponential smoothing (ETS).  
**VI:** Excel 365 có Forecast Sheet tích hợp sử dụng làm trơn hàm mũ (ETS).

**Steps:**
1. Select your time series data (date + value columns)
2. Data → Forecast Sheet
3. Set forecast end date → Create

---

## FORECAST.ETS

**Syntax:** `=FORECAST.ETS(target_date, values, timeline, [seasonality], [data_completion], [aggregation])`

**Formula:**
```
=FORECAST.ETS(A20, B2:B19, A2:A19, 12)
```
*(12 = monthly seasonality)*

---

## Moving Average | Trung bình động

**3-period moving average:**
```
=AVERAGE(B2:B4)    → drag down
```

**Weighted moving average (more recent = more weight):**
```
=(B4*3 + B3*2 + B2*1) / 6
```

---

## TREND and GROWTH

**TREND (linear):**
```
=TREND(known_ys, known_xs, new_xs)
```

**GROWTH (exponential):**
```
=GROWTH(known_ys, known_xs, new_xs)
```

### Example | Ví dụ

| A (Month) | B (Sales) | C (Trend Forecast) |
|---|---|---|
| 1–12 | 100k–180k | |
| 13 | | `=TREND(B2:B13,A2:A13,A14)` |

---

## Seasonality Adjustment | Điều chỉnh Mùa vụ

**Seasonal Index = Period Average / Overall Average:**
```
Seasonal_Index_Jan = AVERAGE(all January values) / AVERAGE(all values)
```

**Deseasonalized forecast:**
```
=Base_Forecast * Seasonal_Index
```

---

*[Regression →](regression.md)*
