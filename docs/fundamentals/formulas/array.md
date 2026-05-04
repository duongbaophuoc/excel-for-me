# Array Formulas | Công thức Mảng

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [What are Array Formulas?](#what-are-array-formulas)
- [CSE vs Dynamic Arrays](#cse-vs-dynamic-arrays)
- [SUMPRODUCT as Array Alternative](#sumproduct-as-array-alternative)
- [Conditional Sum with Multiple Criteria (Array)](#conditional-sum-with-multiple-criteria)
- [Count with Multiple Conditions](#count-with-multiple-conditions)
- [Extracting Data with Conditions](#extracting-data-with-conditions)
- [Dynamic Arrays (Excel 365 / Google Sheets)](#dynamic-arrays)
- [FILTER](#filter)
- [SORT / SORTBY](#sort--sortby)
- [UNIQUE](#unique)
- [SEQUENCE](#sequence)
- [XLOOKUP with Arrays](#xlookup-with-arrays)

---

## What are Array Formulas?

**EN:** Array formulas process multiple values simultaneously, returning either a single result or an array of results. They are the backbone of complex Excel calculations.

**VI:** Công thức mảng xử lý nhiều giá trị đồng thời, trả về một kết quả đơn lẻ hoặc một mảng kết quả. Đây là nền tảng của các phép tính Excel phức tạp.

### Two Types | Hai loại

| Type | Entry | Available |
|---|---|---|
| **CSE (Legacy)** | Ctrl+Shift+Enter | All versions |
| **Dynamic Arrays** | Enter (normal) | Excel 365, Google Sheets |

---

## CSE vs Dynamic Arrays

### CSE Array (Legacy) | Mảng CSE (Cũ)

**Formula:** *(Sum of products — manual array)*
```
{=SUM(A2:A5 * B2:B5)}
```
*Displayed with curly braces `{}` — press Ctrl+Shift+Enter*

### Dynamic Array (Modern) | Mảng động (Hiện đại)

**Formula:** *(Same result, no CSE needed in Excel 365)*
```
=SUM(A2:A5 * B2:B5)
```

| A (Qty) | B (Price) | Sum of Qty×Price |
|---|---|---|
| 5 | 100 | 500 |
| 3 | 250 | 750 |
| 8 | 80 | 640 |
| | | **Total: 1890** |

---

## SUMPRODUCT as Array Alternative

**EN:** SUMPRODUCT works like an array formula but does **not** require Ctrl+Shift+Enter — the safest way to write conditional aggregations in legacy Excel.

**VI:** SUMPRODUCT hoạt động như công thức mảng nhưng **không** cần Ctrl+Shift+Enter — cách an toàn nhất để viết tổng hợp có điều kiện trong Excel cũ.

**Formula:** *(Sum sales where region is "North" AND product is "Apple")*
```
=SUMPRODUCT((A2:A10="North") * (B2:B10="Apple") * C2:C10)
```

| A (Region) | B (Product) | C (Sales) |
|---|---|---|
| North | Apple | 500 |
| North | Mango | 300 |
| South | Apple | 200 |

**Result:** `500`

---

## Conditional Sum with Multiple Criteria

**Formula A — SUMPRODUCT:**
```
=SUMPRODUCT((A2:A10="North")*(B2:B10="Apple")*C2:C10)
```

**Formula B — SUMIFS:**
```
=SUMIFS(C2:C10, A2:A10, "North", B2:B10, "Apple")
```

> 💡 Use SUMIFS when possible — it's easier to read and faster. Use SUMPRODUCT for more complex logic.

---

## Count with Multiple Conditions

**Formula:**
```
=COUNTIFS(A2:A10, "North", B2:B10, "Apple")
```

**Array version:**
```
=SUM((A2:A10="North")*(B2:B10="Apple"))
```
*(Ctrl+Shift+Enter)*

---

## Extracting Data with Conditions

**EN:** Return a list of values that meet a condition.  
**VI:** Trả về danh sách giá trị thỏa mãn điều kiện.

**Legacy approach (CSE):**
```
=IFERROR(INDEX($B$2:$B$10, SMALL(IF($A$2:$A$10="North", ROW($A$2:$A$10)-ROW($A$2)+1), ROW(A1))), "")
```
*(Ctrl+Shift+Enter, drag down)*

**Modern approach (Excel 365):**
```
=FILTER(B2:B10, A2:A10="North")
```

---

## Dynamic Arrays

> 🆕 Excel 365 and Google Sheets — formulas that automatically spill results into multiple cells

**EN:** Dynamic array formulas "spill" their results automatically. No need to select a range first.

**VI:** Công thức mảng động tự động "đổ" kết quả ra nhiều ô. Không cần chọn vùng trước.

---

## FILTER

**Syntax:** `=FILTER(array, include, [if_empty])`

**EN:** Returns a filtered subset of an array based on conditions.  
**VI:** Trả về tập hợp con đã lọc của mảng theo điều kiện.

**Formula:**
```
=FILTER(A2:C10, B2:B10="North", "No results")
```

**Multiple conditions:**
```
=FILTER(A2:C10, (B2:B10="North") * (C2:C10>1000))
```

| A (Name) | B (Region) | C (Sales) |
|---|---|---|
| An | North | 1200 |
| Binh | South | 800 |
| Chi | North | 600 |

**Formula:** `=FILTER(A2:A4, B2:B4="North")`  
**Result:** `An, Chi` *(spills down)*

---

## SORT / SORTBY

**SORT — by a column:**
```
=SORT(A2:C10, 3, -1)
```
*(Sort by column 3 descending)*

**SORTBY — by external criteria:**
```
=SORTBY(A2:B10, C2:C10, -1)
```
*(Sort A2:B10 by C column descending)*

| A (Name) | B (Score) | Sorted (desc) |
|---|---|---|
| An | 85 | Chi: 92 |
| Binh | 70 | An: 85 |
| Chi | 92 | Binh: 70 |

---

## UNIQUE

**Syntax:** `=UNIQUE(array, [by_col], [exactly_once])`

**Formula:**
```
=UNIQUE(A2:A10)
```

**Unique rows in a multi-column range:**
```
=UNIQUE(A2:B10)
```

| A (Values) | UNIQUE Result |
|---|---|
| Apple | Apple |
| Banana | Banana |
| Apple | Cherry |
| Cherry | |

---

## SEQUENCE

**Syntax:** `=SEQUENCE(rows, [cols], [start], [step])`

**EN:** Generate a sequence of numbers automatically.  
**VI:** Tạo chuỗi số tự động.

**Examples:**
```
=SEQUENCE(5)              → 1,2,3,4,5
=SEQUENCE(5,1,0,2)        → 0,2,4,6,8
=SEQUENCE(3,3)            → 3×3 matrix 1–9
```

**Date sequence (every 7 days):**
```
=SEQUENCE(10, 1, TODAY(), 7)
```

---

## XLOOKUP with Arrays

**EN:** XLOOKUP can return multiple columns at once.  
**VI:** XLOOKUP có thể trả về nhiều cột cùng lúc.

**Formula:**
```
=XLOOKUP(G2, A2:A10, B2:D10, "Not found")
```
*(Returns columns B, C, D for the matching row)*

---

## Practical Pattern Summary | Tóm tắt pattern thực tế

| Task | Legacy Formula | Modern Formula |
|---|---|---|
| Conditional sum | `SUMPRODUCT(...)` | `SUMIFS(...)` |
| Unique count | `SUMPRODUCT(1/COUNTIF(...))` | `COUNTA(UNIQUE(...))` |
| Extract filtered list | `INDEX/MATCH/SMALL` CSE | `=FILTER(...)` |
| Unique values | `INDEX/MATCH/COUNTIF` CSE | `=UNIQUE(...)` |
| Number sequence | `ROW(INDIRECT(...))` | `=SEQUENCE(...)` |
| Sorted output | VBA or manual | `=SORT(...)` |

---

## Compatibility | Tương thích

| Feature | Excel 2016 | Excel 365 | Google Sheets |
|---|---|---|---|
| CSE array formulas | ✅ | ✅ | ✅ |
| SUMPRODUCT | ✅ | ✅ | ✅ |
| FILTER | ❌ | ✅ | ✅ |
| SORT / SORTBY | ❌ | ✅ | ✅ |
| UNIQUE | ❌ | ✅ | ✅ |
| SEQUENCE | ❌ | ✅ | ✅ |

---

*← [Date Formulas](date.md) | [Error Handling →](errors.md)*
