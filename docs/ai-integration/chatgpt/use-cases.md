# ChatGPT Use Cases in Excel | Trường hợp Sử dụng

> **Excel & Google Sheets** | AI Integration → ChatGPT

---

## Formula Generation | Tạo Công thức

```
Prompt:
"In Excel, column A = dates, column B = sales, column C = region.
Write a formula to sum all sales in North region for January 2024."

Result:
=SUMPRODUCT((MONTH(A2:A100)=1)*(YEAR(A2:A100)=2024)*(C2:C100="North")*B2:B100)
```

---

## Data Cleaning | Làm sạch Dữ liệu

```
Prompt:
"I have messy phone numbers: +84-909-123-456, 0909123456, (090) 912 3456
Write Excel formulas to normalize them all to: 0xxxxxxxxx"
```

---

## VBA / Apps Script Generation

```
Prompt:
"Write an Excel VBA macro that:
1. Loops through all rows in Sheet1
2. If column C (Status) = 'Overdue', highlight the row in red
3. Send an email summary of overdue items to manager@company.com"
```

---

## Data Analysis | Phân tích Dữ liệu

```
Prompt:
"Here is my monthly sales data for 2023 [paste CSV].
Find:
1. Top 3 months by revenue
2. Month-over-month growth rate
3. Any months with negative growth
Return as a markdown table."
```

---

## Explain Complex Formulas | Giải thích Công thức

```
Prompt:
"Explain this formula in simple Vietnamese:
=INDEX(B2:B10,MATCH(MAX(COUNTIF(B2:B10,B2:B10)),COUNTIF(B2:B10,B2:B10),0))"
```

---

*← [Setup](setup.md) | [Formulas →](formulas.md)*
