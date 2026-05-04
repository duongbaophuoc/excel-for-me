# Budgeting Templates | Mẫu Ngân sách

> **Excel & Google Sheets** | Domains → Finance

---

## Annual Budget Structure | Cấu trúc Ngân sách Năm

```
Sheet: BUDGET_INPUT    → manual entry of targets
Sheet: ACTUALS         → import from accounting
Sheet: VARIANCE        → auto-calculated differences
Sheet: DASHBOARD       → charts and KPIs
```

---

## Budget vs Actual Formula | Ngân sách vs Thực tế

### Variance Amount | Chênh lệch tuyệt đối
```
=Actual - Budget
```

### Variance % | Chênh lệch %
```
=(Actual - Budget) / ABS(Budget)
```

### Favorable / Unfavorable | Thuận lợi / Bất lợi
```
=IF(C2-B2>0, "Favorable", "Unfavorable")   (for revenue)
=IF(C2-B2<0, "Favorable", "Unfavorable")   (for expenses)
```

---

## Rolling Forecast (3+9, 6+6) | Dự báo Lăn

**EN:** Replace past actuals with forecast for remaining months.

**Formula (use actuals until current month, then budget):**
```
=IF(MONTH(A2)<=MONTH(TODAY()), Actuals_Row, Budget_Row)
```

---

## YTD Budget Tracking | Theo dõi Ngân sách Lũy kế

```
YTD Budget:   =SUMIF(MonthCol,"<="&MONTH(TODAY()),BudgetCol)
YTD Actual:   =SUMIF(MonthCol,"<="&MONTH(TODAY()),ActualCol)
YTD Variance: =YTD_Actual - YTD_Budget
```

---

*← [DCF Model](dcf-model.md)*
