# Case Study: Financial Model | Ca thực tế: Mô hình Tài chính

> **Excel & Google Sheets** | Case Studies

---

## Scenario | Tình huống

**EN:** Build a 3-year integrated financial model for a SaaS startup in Vietnam: P&L, Balance Sheet, Cash Flow, and unit economics.

**VI:** Xây dựng mô hình tài chính tích hợp 3 năm cho startup SaaS tại Việt Nam: P&L, Bảng cân đối, Dòng tiền và kinh tế đơn vị.

---

## Model Architecture | Kiến trúc Mô hình

```
Sheet: ASSUMPTIONS   → All input variables (blue cells)
Sheet: REVENUE       → Revenue build-up by product/segment
Sheet: OPEX          → Cost structure
Sheet: P&L           → Income Statement
Sheet: BALANCE       → Balance Sheet
Sheet: CASHFLOW      → Cash Flow Statement
Sheet: UNIT_ECON     → CAC, LTV, Payback Period
Sheet: DASHBOARD     → Charts and summary metrics
```

---

## ASSUMPTIONS Sheet | Sheet Giả định

| Parameter | Y1 | Y2 | Y3 | Notes |
|---|---|---|---|---|
| Starting ARR (VND) | 500M | — | — | Input |
| MoM Growth Rate | 12% | 10% | 8% | Input |
| Churn Rate (annual) | 15% | 12% | 10% | Input |
| Gross Margin | 70% | 72% | 75% | Input |
| S&M as % Rev | 35% | 30% | 25% | Input |
| R&D as % Rev | 20% | 18% | 15% | Input |
| G&A as % Rev | 15% | 12% | 10% | Input |

> 💡 All colored input cells should have Data Validation for range limits.

---

## Revenue Model (SaaS) | Mô hình Doanh thu

### Monthly Recurring Revenue (MRR)
```
MRR_t = MRR_(t-1) * (1 + Growth_Rate) * (1 - Monthly_Churn)
     + New_MRR_t
```

**Formula (row 2 = Jan Year 1):**
```
B3 = B2 * (1 + ASSUMPTIONS!B3) * (1 - ASSUMPTIONS!B4/12)
```

### Annual Recurring Revenue (ARR)
```
=MRR * 12
```

### Net Revenue Retention (NRR)
```
NRR = (Beginning_ARR - Churn_ARR + Expansion_ARR) / Beginning_ARR
```

---

## P&L Build | Xây dựng P&L

```
Revenue:              =SUM(monthly MRR) * 12
COGS:                 =Revenue * (1 - Gross_Margin)
Gross Profit:         =Revenue - COGS
Gross Margin %:       =Gross_Profit / Revenue

S&M Expense:          =Revenue * SM_Rate
R&D Expense:          =Revenue * RD_Rate
G&A Expense:          =Revenue * GA_Rate
Total OpEx:           =SUM(SM, RD, GA)

EBITDA:               =Gross_Profit - Total_OpEx
EBITDA Margin:        =EBITDA / Revenue

D&A:                  =Fixed_Assets / Useful_Life
EBIT:                 =EBITDA - D&A
Interest:             =Debt * Interest_Rate
EBT:                  =EBIT - Interest
Tax:                  =MAX(0, EBT * Tax_Rate)
Net Income:           =EBT - Tax
```

---

## Unit Economics | Kinh tế Đơn vị

### Customer Acquisition Cost (CAC)
```
CAC = Total_SM_Spend / New_Customers_Acquired
```

### Customer Lifetime Value (LTV)
```
LTV = ARPU * Gross_Margin / Churn_Rate
```

### LTV/CAC Ratio (target > 3x)
```
=LTV / CAC
```

### Payback Period (months)
```
=CAC / (ARPU * Gross_Margin)
```

---

## Sensitivity Analysis | Phân tích Độ nhạy

**EN:** Use Excel's Data Table to show how Net Income changes with Growth Rate and Churn Rate.

**VI:** Dùng Data Table của Excel để thấy Net Income thay đổi thế nào theo Growth Rate và Churn Rate.

**Setup:**
1. Create a 2-D table with Growth Rate across top, Churn Rate down side
2. Corner cell = Net_Income formula reference
3. Data → What-If Analysis → Data Table
4. Row input cell = Growth Rate assumption cell
5. Column input cell = Churn Rate assumption cell

---

## Model Integrity Checks | Kiểm tra Tính toàn vẹn Mô hình

```
Balance Sheet check:   Assets = Liabilities + Equity → =IF(ABS(Assets-L_E)<1,"OK","ERROR")
Cash Flow check:       Change in Cash = Ending - Beginning Cash
Revenue check:         ARR / 12 = Average Monthly Revenue
```

---

## AI Review Prompt | Prompt Đánh giá bằng AI

```
"Review this SaaS financial model structure [paste assumptions + P&L].
Check for:
1. Formula logic errors
2. Unrealistic assumptions vs Vietnamese SaaS benchmarks
3. Missing line items
4. Circular reference risks
5. Suggest 3 improvements"
```

---

*← [Sales Analysis](sales-analysis.md) | [Churn Analysis →](churn-analysis.md)*
