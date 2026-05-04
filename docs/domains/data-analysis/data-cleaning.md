# Data Cleaning | Làm sạch Dữ liệu

> **Excel & Google Sheets** | Domains → Data Analysis

---

## Common Data Issues | Vấn đề dữ liệu phổ biến

| Issue | Formula Fix | Hàm xử lý |
|---|---|---|
| Leading/trailing spaces | `=TRIM(A2)` | Xóa khoảng trắng thừa |
| Mixed case | `=PROPER(A2)` | Chuẩn hóa hoa thường |
| Extra spaces between words | `=TRIM(A2)` | Xóa khoảng trắng giữa từ |
| Numbers stored as text | `=VALUE(A2)` or `*1` | Chuyển văn bản thành số |
| Dates stored as text | `=DATEVALUE(A2)` | Chuyển văn bản thành ngày |

---

## Standardize Text | Chuẩn hóa văn bản

```
=UPPER(A2)         → UPPERCASE
=LOWER(A2)         → lowercase
=PROPER(A2)        → Title Case
=TRIM(A2)          → Remove extra spaces
=CLEAN(A2)         → Remove non-printable characters
=SUBSTITUTE(A2, "  ", " ")  → Replace double spaces
```

---

## Remove Duplicates | Xóa trùng lặp

**Flag duplicates (keep first):**
```
=IF(COUNTIF($A$2:A2, A2)>1, "Duplicate", "Unique")
```

**Remove with Excel feature:**
Data → Remove Duplicates → select columns

---

## Split Combined Data | Tách dữ liệu kết hợp

**Split "First Last" into two columns:**
```
First:  =LEFT(A2, FIND(" ",A2)-1)
Last:   =RIGHT(A2, LEN(A2)-FIND(" ",A2))
```

**Text to Columns (manual):** Data → Text to Columns → Delimiter

---

## Validate Data Types | Kiểm tra kiểu dữ liệu

```
=ISNUMBER(A2)     → Is it a number?
=ISTEXT(A2)       → Is it text?
=ISBLANK(A2)      → Is it empty?
=ISDATE(A2)       → Is it a date? (Sheets only)
=ISNUMBER(DATEVALUE(TEXT(A2,"YYYY-MM-DD")))  → Excel date check
```

---

## Find & Replace Patterns | Tìm & thay thế theo mẫu

**Remove all dashes from phone numbers:**
```
=SUBSTITUTE(SUBSTITUTE(A2, "-", ""), " ", "")
```

**Normalize Vietnamese phone (0xx → +84xx):**
```
=IF(LEFT(A2,1)="0", "+84"&MID(A2,2,9), A2)
```

---

*[Aggregation →](aggregation.md)*
