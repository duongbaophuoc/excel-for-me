# DCF Model | Mô hình DCF (Dòng tiền chiết khấu)

> **Excel & Google Sheets** | Domains → Finance

---

## What is DCF? | DCF là gì?

**EN:** Discounted Cash Flow (DCF) values an investment by discounting future cash flows to their present value using a discount rate (WACC or required return).

**VI:** Dòng tiền chiết khấu (DCF) định giá đầu tư bằng cách chiết khấu các dòng tiền tương lai về giá trị hiện tại sử dụng tỷ lệ chiết khấu (WACC hoặc tỷ suất yêu cầu).

**Formula:**
```
NPV = CF1/(1+r)^1 + CF2/(1+r)^2 + ... + CFn/(1+r)^n - Initial Investment
```

---

## NPV Formula | Hàm NPV

**Syntax:** `=NPV(rate, value1, [value2], ...) - initial_investment`

**EN:** NPV does NOT include the Year 0 (initial investment) — subtract it separately.  
**VI:** NPV không bao gồm Năm 0 (đầu tư ban đầu) — trừ riêng.

### Example | Ví dụ

| Year | Cash Flow (VND) |
|---|---|
| 0 (Investment) | -1,000,000,000 |
| 1 | 250,000,000 |
| 2 | 320,000,000 |
| 3 | 380,000,000 |
| 4 | 420,000,000 |
| 5 | 500,000,000 |

**Formula (10% discount rate):**
```
=NPV(10%, B3:B7) + B2
```
*(B2 is negative, B3:B7 are Years 1–5)*

**Result:** If positive → investment creates value / NPV dương → đầu tư tạo ra giá trị

---

## IRR Formula | Hàm IRR (Tỷ suất hoàn vốn nội bộ)

**Syntax:** `=IRR(values, [guess])`

**EN:** The discount rate at which NPV = 0. Accept investment if IRR > WACC.  
**VI:** Tỷ lệ chiết khấu khiến NPV = 0. Chấp nhận đầu tư nếu IRR > WACC.

**Formula:**
```
=IRR(B2:B7)
```

> 💡 Include Year 0 (negative value) in the range for IRR — unlike NPV.

---

## Terminal Value | Giá trị cuối kỳ

**Gordon Growth Model:**
```
TV = FCF_n * (1 + g) / (WACC - g)
```

**Formula:**
```
=B7*(1+G_RATE)/(WACC-G_RATE)
```

Where `G_RATE` = perpetual growth rate (typically 2-3%)

---

*← [Financial Functions](financial-functions.md) | [Budgeting →](budgeting.md)*
