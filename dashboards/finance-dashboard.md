# Finance Dashboard | Dashboard Tài chính

> **Excel & Google Sheets** | Dashboards

---

## Overview | Tổng quan

**EN:** Financial performance dashboard for P&L, cash flow, and budget variance tracking.

**VI:** Dashboard hiệu suất tài chính cho P&L, dòng tiền và theo dõi chênh lệch ngân sách.

---

## Sheet Structure | Cấu trúc

```
Sheet: P&L          → Monthly P&L data (actuals)
Sheet: BUDGET       → Annual budget by month
Sheet: CASHFLOW     → Cash flow statement
Sheet: DASHBOARD    → Financial KPIs and charts
```

---

## P&L Summary Formulas | Công thức P&L

### Revenue
```
=SUMIF(P&L!A:A, "Revenue", P&L!B:B)
```

### Gross Profit Margin
```
=(Revenue - COGS) / Revenue
```

### EBITDA
```
=Revenue - COGS - OpEx + Depreciation + Amortization
```

### Net Profit Margin
```
=Net_Profit / Revenue
```

---

## Budget Variance Analysis | Phân tích Chênh lệch Ngân sách

### Variance Amount | Chênh lệch tuyệt đối
```
=Actual - Budget
```

### Variance % | Chênh lệch %
```
=(Actual - Budget) / ABS(Budget)
```

### Traffic light for variance:
```
Favorable (>5%):   Green
On track (±5%):    Yellow
Unfavorable (<-5%): Red
```

---

## Cash Flow Formulas | Công thức Dòng tiền

### Operating Cash Flow
```
=Net_Income + Depreciation - Change_in_Working_Capital
```

### Days Sales Outstanding (DSO)
```
=Accounts_Receivable / (Annual_Revenue / 365)
```

### Days Payable Outstanding (DPO)
```
=Accounts_Payable / (COGS / 365)
```

### Cash Conversion Cycle
```
=DIO + DSO - DPO
```
*(DIO = Days Inventory Outstanding)*

---

## YTD Tracking | Theo dõi Lũy kế Năm

```
YTD Revenue: =SUMIF(P&L!MonthCol,"<="&MONTH(TODAY()),P&L!RevenueCol)
YTD Budget:  =SUMIF(BUDGET!MonthCol,"<="&MONTH(TODAY()),BUDGET!RevenueCol)
YTD Var%:    =(YTD_Revenue-YTD_Budget)/ABS(YTD_Budget)
```

---

## Recommended Charts | Biểu đồ

| Chart | Type | Purpose |
|---|---|---|
| Revenue vs Budget | Combo (bar + line) | Track monthly actuals vs plan |
| P&L Waterfall | Waterfall | Show revenue → expenses → profit |
| Cash Position | Area chart | Cash balance trend |
| Expense Breakdown | Donut | Cost structure visualization |

---

*← [Sales Dashboard](sales-dashboard.md) | [KPI Dashboard →](kpi-dashboard.md)*
