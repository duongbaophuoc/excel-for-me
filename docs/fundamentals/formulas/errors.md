# Error Handling | Xử lý Lỗi trong Excel

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [Common Excel Errors](#common-excel-errors)
- [IFERROR](#iferror)
- [IFNA](#ifna)
- [ISERROR / ISERR / ISNA](#iserror--iserr--isna)
- [Error in Array Formulas](#error-in-array-formulas)
- [Circular Reference](#circular-reference)
- [Error Audit Tips](#error-audit-tips)

---

## Common Excel Errors | Các lỗi Excel thường gặp

| Error | Meaning (EN) | Ý nghĩa (VI) | Common Cause |
|---|---|---|---|
| `#DIV/0!` | Division by zero | Chia cho 0 | `=A2/B2` when B2=0 |
| `#N/A` | Value not available | Giá trị không tồn tại | VLOOKUP can't find value |
| `#VALUE!` | Wrong type | Kiểu dữ liệu sai | Text in numeric formula |
| `#REF!` | Invalid reference | Tham chiếu không hợp lệ | Deleted referenced cell |
| `#NAME?` | Unrecognized name | Tên không nhận dạng được | Typo in formula name |
| `#NUM!` | Invalid number | Số không hợp lệ | `=SQRT(-1)` |
| `#NULL!` | Invalid intersection | Giao nhau không hợp lệ | `=A1:A5 C1:C5` (space instead of comma) |
| `####` | Column too narrow | Cột quá hẹp | Widen the column |

---

## IFERROR

**Syntax:** `=IFERROR(value, value_if_error)`

**EN:** Catches **any** type of error and returns a fallback value.  
**VI:** Bắt **bất kỳ** loại lỗi nào và trả về giá trị dự phòng.

**Formula:**
```
=IFERROR(VLOOKUP(D2, A2:B10, 2, 0), "Not Found")
=IFERROR(A2/B2, 0)
```

### Example | Ví dụ

| A (ID) | B (Name) | D (Search) | Result |
|---|---|---|---|
| 101 | An | 105 | Not Found |
| 102 | Binh | 101 | An |

---

## IFNA

**Syntax:** `=IFNA(value, value_if_na)`

**EN:** Catches only `#N/A` errors — better than IFERROR when you want other errors to surface.  
**VI:** Chỉ bắt lỗi `#N/A` — tốt hơn IFERROR khi bạn muốn các lỗi khác vẫn hiển thị.

**Formula:**
```
=IFNA(VLOOKUP(D2, A2:B10, 2, 0), "Không tìm thấy")
```

> 💡 **Best practice:** Use `IFNA` with VLOOKUP/MATCH, `IFERROR` for division or numeric operations.

---

## ISERROR / ISERR / ISNA

**EN:** Return TRUE or FALSE — useful inside IF conditions.  
**VI:** Trả về TRUE hoặc FALSE — hữu ích bên trong điều kiện IF.

| Function | Catches |
|---|---|
| `ISERROR(x)` | All errors |
| `ISERR(x)` | All errors except #N/A |
| `ISNA(x)` | Only #N/A |

**Formula:**
```
=IF(ISERROR(A2/B2), "Error", A2/B2)
=IF(ISNA(VLOOKUP(D2,A:B,2,0)), "Not Found", VLOOKUP(D2,A:B,2,0))
```

---

## Error in Array Formulas

**EN:** Use `IFERROR` inside array formulas to handle individual element errors.  
**VI:** Dùng `IFERROR` bên trong công thức mảng để xử lý lỗi từng phần tử.

**Formula:**
```
=SUMPRODUCT(IFERROR(A2:A10 / B2:B10, 0))
```
*(Divides each pair, replaces errors with 0, then sums)*

**With FILTER (Excel 365):**
```
=IFERROR(FILTER(A2:A10, B2:B10="North"), "No match")
```

---

## Circular Reference

**EN:** A circular reference occurs when a formula refers to its own cell, directly or indirectly. Excel alerts you when this happens.

**VI:** Tham chiếu vòng xảy ra khi công thức tham chiếu đến chính ô của nó, trực tiếp hoặc gián tiếp. Excel cảnh báo khi điều này xảy ra.

### How to find circular references | Cách tìm tham chiếu vòng

1. Go to **Formulas → Error Checking → Circular References**
2. Vào **Công thức → Kiểm tra lỗi → Tham chiếu vòng**

### Intentional iterative calculation | Tính toán lặp chủ ý

- Excel Options → Formulas → Enable Iterative Calculation
- Tùy chọn Excel → Công thức → Bật Tính toán lặp

---

## Error Audit Tips | Mẹo kiểm tra lỗi

### Trace Precedents / Dependents

| Action | Shortcut |
|---|---|
| Trace Precedents | Ctrl+[ |
| Trace Dependents | Ctrl+] |
| Remove Arrows | Alt+M, A, A |

### Evaluate Formula | Đánh giá công thức

- **Formulas → Evaluate Formula** — step through formula evaluation one step at a time.
- Useful for debugging complex nested formulas.

### F9 Key | Phím F9

**EN:** Select part of a formula in the formula bar and press F9 to evaluate just that portion.  
**VI:** Chọn một phần công thức trong thanh công thức và nhấn F9 để tính toán phần đó.

**Example:**
```
=SUM(IF(A2:A5>10, A2:A5, 0))
     ↑ select this part and press F9 → see the array {TRUE,FALSE,TRUE,TRUE}
```

---

## Formula Auditing Checklist | Danh sách kiểm tra

- [ ] Are all referenced ranges correct? *(Tất cả vùng tham chiếu đúng?)*
- [ ] Are column/row references absolute ($) where needed? *(Tham chiếu tuyệt đối khi cần?)*
- [ ] Does the formula handle empty cells? *(Công thức xử lý ô trống?)*
- [ ] Is the formula wrapped in IFERROR where appropriate? *(Đã bọc IFERROR chưa?)*
- [ ] Are text/number types consistent in comparisons? *(Kiểu dữ liệu nhất quán?)*

---

*← [Array Formulas](array.md) | Back to [Fundamentals Index](../)*
