# Regression Analysis | Phân tích Hồi quy

> **Excel & Google Sheets** | Domains → Forecasting

---

## Simple Linear Regression | Hồi quy tuyến tính đơn

**Formula:** `y = a + b*x`

### Using LINEST

**Syntax:** `=LINEST(known_ys, known_xs, [const], [stats])`

```
{=LINEST(B2:B20, A2:A20, TRUE, TRUE)}
```
*(Ctrl+Shift+Enter — returns array of stats)*

### SLOPE and INTERCEPT

```
=SLOPE(B2:B20, A2:A20)      → b (coefficient)
=INTERCEPT(B2:B20, A2:A20)  → a (intercept)
=CORREL(A2:A20, B2:B20)     → R (correlation)
=RSQ(B2:B20, A2:A20)        → R² (coefficient of determination)
```

### Predict with FORECAST.LINEAR

```
=FORECAST.LINEAR(x_value, known_ys, known_xs)
```

---

## Example | Ví dụ

| A (Ad Spend) | B (Sales) |
|---|---|
| 10M | 85M |
| 15M | 110M |
| 20M | 145M |
| 25M | 175M |

```
Slope:     =SLOPE(B2:B5, A2:A5)      → ~6.1 (each 1M ad spend → 6.1M sales)
Intercept: =INTERCEPT(B2:B5, A2:A5) → ~25M base sales
R²:        =RSQ(B2:B5, A2:A5)       → closer to 1 = better fit

Predict for 30M spend:
=FORECAST.LINEAR(30, B2:B5, A2:A5)  → ~208M
```

---

## Multiple Regression via Data Analysis Toolpak

1. Data → Data Analysis → Regression
2. Set Input Y Range (dependent), Input X Range (independent variables)
3. Check Labels, set Output Range
4. Click OK → Regression summary output

---

*← [Time Series](time-series.md)*
