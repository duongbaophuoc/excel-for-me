# Case Study: Churn Analysis | Ca thực tế: Phân tích Churns

> **Excel & Google Sheets** | Case Studies

---

## Scenario | Tình huống

**EN:** A subscription business wants to analyze customer churn: identify at-risk customers, calculate churn rate by cohort, and model revenue impact.

**VI:** Một doanh nghiệp đăng ký muốn phân tích khách hàng rời bỏ: xác định khách hàng có nguy cơ, tính tỷ lệ churn theo cohort và mô hình hóa tác động doanh thu.

---

## Dataset | Tập Dữ liệu

```
Columns: CustomerID | SignupDate | CancelDate | Plan |
         MRR | LastLoginDate | SupportTickets | NPS_Score
```

---

## Step 1: Define Churn | Bước 1: Định nghĩa Churn

**Active customer:**
```
=IF(AND(D2<>"", D2<=TODAY()), "Churned", "Active")
```

**Days since last login (engagement proxy):**
```
=TODAY() - F2
```

**Churn flag:**
```
=IF(OR(G2="Churned", Days_Since_Login>90), 1, 0)
```

---

## Step 2: Churn Rate Calculation | Tính Tỷ lệ Churn

### Monthly Churn Rate | Tỷ lệ Churn Tháng

```
Churned_This_Month = COUNTIFS(CancelDate, ">="&StartOfMonth, CancelDate, "<="&EndOfMonth)
Active_Start = COUNTIFS(SignupDate, "<="&StartOfMonth, CancelDate_or_blank, ">="&StartOfMonth)
Monthly_Churn_Rate = Churned_This_Month / Active_Start
```

**Formulas:**
```
Churned:  =COUNTIFS(D:D,">="&DATE(YEAR(G2),MONTH(G2),1), D:D,"<="&EOMONTH(G2,0))
Active:   =COUNTIFS(B:B,"<="&DATE(YEAR(G2),MONTH(G2),1), D:D,">="&DATE(YEAR(G2),MONTH(G2),1))
Rate:     =B2/C2
```

---

## Step 3: Cohort Analysis | Phân tích Cohort

**EN:** Group customers by signup month and track how many remain active each month.

**VI:** Nhóm khách hàng theo tháng đăng ký và theo dõi bao nhiêu người còn hoạt động mỗi tháng.

### Cohort Table Structure | Cấu trúc Bảng Cohort

| Cohort (Signup Month) | Month 0 | Month 1 | Month 2 | Month 3 | ... |
|---|---|---|---|---|---|
| Jan 2024 | 100% | 88% | 79% | 72% | |
| Feb 2024 | 100% | 90% | 81% | | |

**Formula for each cell:**
```
=COUNTIFS(
  SignupMonth, $A2,          → same cohort
  CancelMonth, ">="&B$1      → still active at month N
) / COUNTIF(SignupMonth, $A2)
```

---

## Step 4: Churn Risk Scoring | Bước 4: Điểm Nguy cơ Churn

**Build a simple churn risk score:**

| Factor | Low Risk | High Risk | Formula |
|---|---|---|---|
| Days since login | <30 | >90 | `=IF(H2>90,3,IF(H2>30,1,0))` |
| Support tickets | 0-1 | 4+ | `=IF(G2>=4,3,IF(G2>=2,1,0))` |
| NPS Score | 8-10 | 0-5 | `=IF(I2<=5,3,IF(I2<=7,1,0))` |
| MRR trend | Growing | Declining | Manual score |

**Total Risk Score:**
```
=SUM(Score_Cols)
```

**Risk Tier:**
```
=IFS(TotalScore>=7,"High Risk - Urgent",
     TotalScore>=4,"Medium Risk - Monitor",
     TRUE, "Low Risk")
```

---

## Step 5: Revenue Impact Model | Bước 5: Mô hình Tác động Doanh thu

### Revenue at Risk | Doanh thu có nguy cơ
```
=SUMIF(RiskTier, "High Risk - Urgent", MRR_Column)
```

### Projected Annual Churn Impact
```
=Monthly_Churn_Rate * 12 * Total_MRR
```

### LTV Lost per Churned Customer
```
=AVERAGE(MRR) / Monthly_Churn_Rate
```

---

## AI Prompt for Churn Insights | Prompt AI cho phân tích Churn

```
"I have this customer churn data [paste cohort table + risk scores].
Analyze:
1. Which signup cohorts have the highest 3-month retention?
2. What pattern do high-risk customers share?
3. Write 3 specific re-engagement strategies for high-risk segments
4. Estimate the revenue impact if we reduce churn by 2% monthly"
```

---

## Retention Improvement Playbook | Playbook Cải thiện Giữ chân

| Risk Level | Action | Expected Impact |
|---|---|---|
| High Risk | Personal outreach within 24h | Recover 20-30% |
| Medium Risk | Automated email sequence | Recover 10-15% |
| Low Risk | Monthly newsletter + feature updates | Maintain 95%+ |
| Recently churned | Win-back campaign (30/60/90 days) | Recover 5-10% |

---

*← [Financial Model](financial-model.md)*
