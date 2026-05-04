# Lookup & Reference Formulas | Công thức Tra cứu & Tham chiếu

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [VLOOKUP](#vlookup)
- [Multi-Column VLOOKUP](#multi-column-vlookup)
- [VLOOKUP Right to Left](#vlookup-right-to-left)
- [Case-Sensitive VLOOKUP](#case-sensitive-vlookup)
- [INDEX + MATCH](#index--match)
- [XLOOKUP](#xlookup)
- [Find First/Last Non-Blank in a Range](#find-firstlast-non-blank)

---

## VLOOKUP

**Syntax:** `=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])`

**EN:** Searches for a value in the first column of a range and returns a value from a specified column in the same row.

**VI:** Tìm kiếm giá trị trong cột đầu tiên của vùng dữ liệu và trả về giá trị từ cột chỉ định trong cùng hàng đó.

### Example | Ví dụ

| A (Employee ID) | B (Name) | C (Salary) |
|---|---|---|
| 101 | Nguyen Van A | 15,000,000 |
| 102 | Tran Thi B | 18,000,000 |
| 103 | Le Van C | 12,000,000 |

**Formula:** `=VLOOKUP(102, A2:C4, 2, 0)`

**Result:** `Tran Thi B`

> ⚠️ `range_lookup = 0` (or FALSE) for exact match. Always use 0 for most business use cases.  
> ⚠️ Dùng `0` (hoặc FALSE) để tìm kiếm chính xác. Luôn dùng `0` trong hầu hết trường hợp thực tế.

---

## Multi-Column VLOOKUP

**EN:** When you need to look up based on two or more columns combined, concatenate the lookup keys.

**VI:** Khi cần tra cứu dựa trên hai hoặc nhiều cột kết hợp, nối các khóa tra cứu lại.

### Example | Ví dụ

| A (Region) | B (Product) | C (Sales) |
|---|---|---|
| North | Apple | 500 |
| South | Apple | 320 |
| North | Mango | 410 |

**Helper column D (concat key):** `=A2&"|"&B2` → `North|Apple`

**Formula:**
```
=VLOOKUP("North|Mango", D2:E4, 2, 0)
```
**Result:** `410`

> 💡 **Alternative without helper column (array formula):**
> ```
> =INDEX(C2:C4, MATCH("North"&"|"&"Mango", A2:A4&"|"&B2:B4, 0))
> ```
> Press **Ctrl+Shift+Enter** in Excel (not needed in Google Sheets or Excel 365).

---

## VLOOKUP Right to Left

**EN:** Standard VLOOKUP cannot look to the left. Use `INDEX+MATCH` instead.

**VI:** VLOOKUP tiêu chuẩn không thể tra cứu sang trái. Hãy dùng `INDEX+MATCH`.

### Example | Ví dụ

| A (Name) | B (ID) |
|---|---|
| Nguyen Van A | 101 |
| Tran Thi B | 102 |

**Goal:** Find the Name given ID = 102 (B column → A column = right to left)

**Formula:**
```
=INDEX(A2:A3, MATCH(102, B2:B3, 0))
```
**Result:** `Tran Thi B`

---

## Case-Sensitive VLOOKUP

**EN:** VLOOKUP is not case-sensitive by default. Use `EXACT` inside an array formula.

**VI:** VLOOKUP mặc định không phân biệt hoa thường. Dùng hàm `EXACT` trong công thức mảng.

### Example | Ví dụ

| A (Code) | B (Value) |
|---|---|
| abc | Low |
| ABC | HIGH |
| Abc | Medium |

**Formula (Ctrl+Shift+Enter in classic Excel):**
```
=INDEX(B2:B4, MATCH(TRUE, EXACT(A2:A4, "ABC"), 0))
```
**Result:** `HIGH`

---

## INDEX + MATCH

**Syntax:**
```
=INDEX(return_range, MATCH(lookup_value, lookup_range, 0))
```

**EN:** The most flexible lookup combination in Excel. Works left-to-right, right-to-left, and with multiple criteria.

**VI:** Kết hợp tra cứu linh hoạt nhất trong Excel. Hoạt động cả trái sang phải, phải sang trái và nhiều tiêu chí.

### Example | Ví dụ

| A (City) | B (Revenue) |
|---|---|
| Ha Noi | 120,000 |
| Ho Chi Minh | 250,000 |
| Da Nang | 85,000 |

**Formula:** `=INDEX(B2:B4, MATCH("Da Nang", A2:A4, 0))`

**Result:** `85,000`

---

## XLOOKUP

> 🆕 Available in Excel 365, Excel 2021, and Google Sheets

**Syntax:** `=XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])`

**EN:** The modern replacement for VLOOKUP. Searches any direction, returns multiple columns, and handles errors natively.

**VI:** Thay thế hiện đại cho VLOOKUP. Tìm kiếm mọi hướng, trả về nhiều cột, xử lý lỗi sẵn có.

### Example | Ví dụ

| A (ID) | B (Name) | C (Dept) |
|---|---|---|
| 101 | An | IT |
| 102 | Binh | HR |
| 103 | Chi | Finance |

**Formula:** `=XLOOKUP(102, A2:A4, B2:C4, "Not found")`

**Result:** `Binh  HR` *(returns both columns)*

---

## Find First/Last Non-Blank

### Find First Non-Blank Value in a Range | Tìm giá trị không rỗng đầu tiên

**Formula:**
```
=INDEX(A1:A10, MATCH(TRUE, A1:A10<>"", 0))
```
*(Ctrl+Shift+Enter in classic Excel)*

### Find Last Non-Blank Value in a Range | Tìm giá trị không rỗng cuối cùng

**Formula:**
```
=LOOKUP(2, 1/(A1:A10<>""), A1:A10)
```

### Find First Numeric Value | Tìm giá trị số đầu tiên

**Formula:**
```
=INDEX(A1:A10, MATCH(TRUE, ISNUMBER(A1:A10), 0))
```

### Find Last Numeric Value | Tìm giá trị số cuối cùng

**Formula:**
```
=LOOKUP(2, 1/ISNUMBER(A1:A10), A1:A10)
```

### Find Last Used Value | Tìm giá trị cuối cùng được sử dụng

**Formula:**
```
=LOOKUP(2, 1/(A1:A100<>""), A1:A100)
```

---

## Compatibility | Tương thích

| Formula | Excel 2016 | Excel 365 | Google Sheets |
|---|---|---|---|
| VLOOKUP | ✅ | ✅ | ✅ |
| INDEX+MATCH | ✅ | ✅ | ✅ |
| XLOOKUP | ❌ | ✅ | ✅ |

---

*Next: [Logical Formulas →](logical.md)*
