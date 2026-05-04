# Financial Functions | Hàm Tài chính

> **Excel & Google Sheets** | Domains → Finance
> *Based on Excel Formulas Bible — Financial Functions Series*

---

## Table of Contents | Mục lục

- [Calculate EMI (Loan Payment)](#calculate-emi)
- [Interest Part of EMI](#interest-part-of-emi)
- [Principal Part of EMI](#principal-part-of-emi)
- [Number of EMIs to Pay Off a Loan](#number-of-emis)
- [Calculate Interest Rate](#calculate-interest-rate)
- [Compounded Interest](#compounded-interest)
- [Effective Interest Rate](#effective-interest-rate)

---

## Calculate EMI | Tính khoản trả góp EMI

**EN:** EMI = Equated Monthly Installment. Use the PMT function.  
**VI:** EMI = Khoản trả hàng tháng cố định. Dùng hàm PMT.

**Syntax:** `=PMT(rate, nper, pv, [fv], [type])`

| Argument | Meaning (EN) | Ý nghĩa (VI) |
|---|---|---|
| `rate` | Monthly interest rate (annual/12) | Lãi suất tháng |
| `nper` | Total number of payments | Tổng số kỳ thanh toán |
| `pv` | Present value (loan amount) | Giá trị hiện tại (số tiền vay) |
| `fv` | Future value (default 0) | Giá trị tương lai |
| `type` | 0=end of period, 1=beginning | 0=cuối kỳ, 1=đầu kỳ |

### Example | Ví dụ

**Scenario:** Loan 500,000,000 VND, 12% annual rate, 60 months

| Input | Value |
|---|---|
| Loan amount | 500,000,000 |
| Annual rate | 12% |
| Monthly rate (B3/12) | 1% |
| Tenure (months) | 60 |

**Formula:**
```
=PMT(B3/12, B4, -B2)
```
**Result:** `~11,122,444 VND/month`

> 💡 Use negative PV (or negate result) to get a positive EMI value.

---

## Interest Part of EMI | Phần Lãi trong EMI

**Syntax:** `=IPMT(rate, per, nper, pv)`

**EN:** Returns the interest portion of a specific payment number.  
**VI:** Trả về phần lãi của một kỳ thanh toán cụ thể.

**Formula:** *(Interest portion of 1st payment)*
```
=IPMT(12%/12, 1, 60, -500000000)
```

| Period | IPMT | PPMT |
|---|---|---|
| Month 1 | `=IPMT(1%, 1, 60, -500M)` ≈ 5,000,000 | ≈ 6,122,444 |
| Month 30 | `=IPMT(1%, 30, 60, -500M)` ≈ 2,800,000 | ≈ 8,322,444 |
| Month 60 | `=IPMT(1%, 60, 60, -500M)` ≈ 110,000 | ≈ 11,012,444 |

---

## Principal Part of EMI | Phần Vốn gốc trong EMI

**Syntax:** `=PPMT(rate, per, nper, pv)`

**Formula:** *(Principal portion of 1st payment)*
```
=PPMT(12%/12, 1, 60, -500000000)
```

> ✅ IPMT + PPMT = PMT (total EMI) for every period.

---

## Number of EMIs to Pay Off a Loan | Số kỳ EMI cần trả

**Syntax:** `=NPER(rate, pmt, pv)`

**EN:** Given a fixed monthly payment, how many months to pay off the loan?  
**VI:** Với khoản trả cố định hàng tháng, cần bao nhiêu tháng để trả hết?

**Formula:**
```
=NPER(12%/12, -8000000, 500000000)
```

| Loan | Rate/month | Payment/month | Months |
|---|---|---|---|
| 500,000,000 | 1% | 8,000,000 | `=NPER(1%, -8000000, 500000000)` ≈ 87 |

---

## Calculate Interest Rate | Tính Lãi suất

**Syntax:** `=RATE(nper, pmt, pv) * 12` *(for annual rate)*

**EN:** Find the monthly/annual interest rate given payment and loan details.  
**VI:** Tìm lãi suất tháng/năm khi biết khoản thanh toán và thông tin khoản vay.

**Formula:**
```
=RATE(60, -11122444, 500000000) * 12
```
**Result:** ≈ 12% annual

---

## Compounded Interest | Lãi suất Kép

**EN:** Calculate the future value of an investment with compound interest.  
**VI:** Tính giá trị tương lai của khoản đầu tư với lãi suất kép.

**Syntax:** `=FV(rate, nper, pmt, [pv])`

**Formula:** *(10M invested at 8% annually for 10 years)*
```
=FV(8%/12, 120, 0, -10000000)
```
**Result:** ≈ 22,196,402 VND

**Simple compound formula:**
```
= Principal * (1 + rate)^years
= 10000000 * (1+8%)^10
```

---

## Effective Interest Rate | Lãi suất Hiệu dụng

**EN:** Convert nominal rate to effective annual rate (EAR), accounting for compounding frequency.  
**VI:** Chuyển lãi suất danh nghĩa sang lãi suất hiệu dụng hàng năm (EAR).

**Syntax:** `=EFFECT(nominal_rate, npery)`

**Formula:** *(12% nominal, compounded monthly)*
```
=EFFECT(12%, 12)
```
**Result:** ≈ 12.68%

**Manual formula:**
```
=(1 + nominal_rate/n)^n - 1
=(1 + 12%/12)^12 - 1
```

---

## Loan Amortization Schedule | Bảng khấu hao vay

| Month | Opening Balance | EMI | Interest | Principal | Closing Balance |
|---|---|---|---|---|---|
| 1 | 500,000,000 | `=PMT(...)` | `=IPMT(...)` | `=PPMT(...)` | Opening - Principal |
| 2 | Prev Closing | (same) | (per=2) | (per=2) | ... |

**Build with formulas:**
```
A2: 1                         (Month)
B2: 500000000                 (Opening Balance)
C2: =PMT($E$1/12, $E$2, -$E$3)   (Fixed EMI)
D2: =IPMT($E$1/12, A2, $E$2, -$E$3)  (Interest)
E2: =PPMT($E$1/12, A2, $E$2, -$E$3)  (Principal)
F2: =B2-E2                    (Closing Balance)
B3: =F2                       (Next month opening)
```

---

*← [Domains](../)*
