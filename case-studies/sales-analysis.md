# Case Study: Sales Analysis | Ca thực tế: Phân tích Bán hàng

> **Excel & Google Sheets** | Case Studies

---

## Scenario | Tình huống

**EN:** A regional retail chain with 5 stores wants to analyze 12 months of transaction data to find underperforming stores, best-selling SKUs, and seasonal trends.

**VI:** Một chuỗi bán lẻ khu vực với 5 cửa hàng muốn phân tích 12 tháng dữ liệu giao dịch để tìm cửa hàng kém hiệu quả, SKU bán chạy nhất và xu hướng mùa vụ.

---

## Dataset | Tập Dữ liệu

```
Columns: TransactionDate | StoreID | SKU | ProductName |
         Category | Qty | UnitPrice | Revenue | COGS
Rows: ~50,000 transactions
Period: Jan–Dec 2024
```

---

## Step 1: Data Cleaning | Bước 1: Làm sạch Dữ liệu

**Remove blanks:**
```
Filter → Custom Filter → "is not blank" on Revenue column
```

**Standardize store names (inconsistent entries):**
```
=SWITCH(TRIM(UPPER(A2)),
  "STORE 1","Store_01",
  "S1","Store_01",
  "STORE1","Store_01",
  A2)
```

**Check for negative revenue (returns):**
```
=COUNTIF(H:H,"<0")   → flag for review
```

---

## Step 2: Key Aggregations | Bước 2: Tổng hợp chính

### Revenue by Store | Doanh thu theo Cửa hàng
```
=SUMIF($B$2:$B$50000, F2, $H$2:$H$50000)
```

### Revenue by Month | Doanh thu theo Tháng
```
=SUMPRODUCT((MONTH($A$2:$A$50000)=G2)*$H$2:$H$50000)
```

### Top 10 SKUs by Revenue | Top 10 SKU theo Doanh thu
```
Step 1: SUMIF by SKU into summary table
Step 2: =LARGE(RevenueCol, ROW(A1))  → get rank values
Step 3: =INDEX(SKUCol, MATCH(K2, RevenueCol, 0))  → get SKU name
```

### Gross Profit % by Category
```
=(SUMIF(CategoryCol, A2, RevenueCol) - SUMIF(CategoryCol, A2, COGSCol))
/ SUMIF(CategoryCol, A2, RevenueCol)
```

---

## Step 3: Seasonal Analysis | Bước 3: Phân tích Mùa vụ

**Monthly index (value vs annual average):**
```
Monthly_Avg = Annual_Revenue / 12
Seasonal_Index = Month_Revenue / Monthly_Avg
```

**Formula:**
```
=SUMPRODUCT((MONTH(DateCol)=B2)*RevenueCol) / (SUM(RevenueCol)/12)
```

**Result interpretation:**
- Index > 1.0 = above-average month (peak season)
- Index < 1.0 = below-average month (off-season)

---

## Step 4: Store Performance Ranking | Bước 4: Xếp hạng Cửa hàng

| Store | Revenue | Target | Achievement | Rank |
|---|---|---|---|---|
| Store_01 | formula | manual | =B2/C2 | =RANK(D2,$D$2:$D$6,-1) |

**Identify underperformers:**
```
=IF(D2<0.8, "Underperforming - Review", IF(D2<1, "Below Target", "On Track"))
```

---

## Step 5: Dashboard Summary | Bước 5: Tóm tắt Dashboard

**Build PivotTable:**
- Rows: StoreID
- Columns: Month number
- Values: Revenue (Sum)

**Create sparklines** for each store's monthly trend.

**Add slicers** for Category and StoreID to make interactive.

---

## AI-Assisted Analysis | Phân tích hỗ trợ AI

**Prompt for ChatGPT/Claude:**
```
"Here is a pivot table of monthly revenue by store [paste data].
Identify:
1. Which stores are consistently underperforming?
2. Are there any unusual spikes or drops that need investigation?
3. Recommend which 2 stores to prioritize for operational review."
```

---

## Key Findings Template | Mẫu Phát hiện Chính

```
1. Total Revenue 2024: X VND (+Y% vs 2023)
2. Best performing store: Store_XX (Z% above target)
3. Underperforming stores: Store_XX, Store_YY
4. Top SKU: Product Name (contributing X% of revenue)
5. Peak season: Month X (seasonal index: 1.35)
6. Slowest month: Month Y (seasonal index: 0.72)
7. Recommended actions: [3 bullet points]
```

---

*← [Case Studies](.) | [Financial Model →](financial-model.md)*
