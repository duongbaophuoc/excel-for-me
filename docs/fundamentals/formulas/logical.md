# Logical Formulas | Công thức Logic

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [IF](#if)
- [AND / OR / NOT](#and--or--not)
- [IFS](#ifs)
- [IFERROR / IFNA](#iferror--ifna)
- [SWITCH](#switch)
- [Rank within Groups](#rank-within-groups)
- [Check if a List is Unique (Has Duplicates)](#check-if-a-list-is-unique)

---

## IF

**Syntax:** `=IF(logical_test, value_if_true, value_if_false)`

**EN:** Returns one value if a condition is TRUE, another if FALSE. The foundation of conditional logic in spreadsheets.

**VI:** Trả về một giá trị nếu điều kiện ĐÚNG, giá trị khác nếu SAI. Nền tảng của logic có điều kiện trong bảng tính.

### Example | Ví dụ

| A (Score) | B (Result) |
|---|---|
| 85 | `=IF(A2>=50,"Pass","Fail")` → **Pass** |
| 42 | `=IF(A3>=50,"Pass","Fail")` → **Fail** |

### Nested IF | IF lồng nhau

```
=IF(A2>=90,"Excellent", IF(A2>=70,"Good", IF(A2>=50,"Pass","Fail")))
```

> 💡 For many conditions, use IFS (see below) instead of deeply nested IFs.

---

## AND / OR / NOT

### AND
**EN:** Returns TRUE only if ALL conditions are true.  
**VI:** Trả về TRUE chỉ khi TẤT CẢ điều kiện đúng.

```
=AND(A2>=18, A2<=60)   → TRUE if age is between 18 and 60
```

### OR
**EN:** Returns TRUE if ANY condition is true.  
**VI:** Trả về TRUE nếu BẤT KỲ điều kiện nào đúng.

```
=OR(A2="Manager", A2="Director")   → TRUE if role is Manager or Director
```

### Combined Example | Ví dụ kết hợp

| A (Age) | B (Role) | C (Eligible?) |
|---|---|---|
| 35 | Manager | `=IF(AND(A2>=25, OR(B2="Manager",B2="Director")), "Yes","No")` → **Yes** |

---

## IFS

> 🆕 Excel 2019+, Excel 365, Google Sheets

**Syntax:** `=IFS(cond1, val1, cond2, val2, ..., TRUE, default)`

**EN:** Tests multiple conditions in order and returns the value for the first TRUE condition.

**VI:** Kiểm tra nhiều điều kiện theo thứ tự và trả về giá trị của điều kiện ĐÚNG đầu tiên.

### Example | Ví dụ

```
=IFS(A2>=90,"Xuất sắc", A2>=70,"Giỏi", A2>=50,"Khá", TRUE,"Yếu")
```

| A (Score) | Result |
|---|---|
| 92 | Xuất sắc |
| 75 | Giỏi |
| 55 | Khá |
| 30 | Yếu |

---

## IFERROR / IFNA

**Syntax:**
- `=IFERROR(value, value_if_error)`
- `=IFNA(value, value_if_na)`

**EN:** Traps errors and replaces them with a friendly message. `IFNA` handles only `#N/A` errors.

**VI:** Bắt lỗi và thay thế bằng thông báo thân thiện. `IFNA` chỉ xử lý lỗi `#N/A`.

### Example | Ví dụ

```
=IFERROR(VLOOKUP(D2, A2:B10, 2, 0), "Not Found")
=IFNA(VLOOKUP(D2, A2:B10, 2, 0), "Không tìm thấy")
```

---

## SWITCH

> 🆕 Excel 2019+, Excel 365, Google Sheets

**Syntax:** `=SWITCH(expression, val1, result1, val2, result2, ..., [default])`

**EN:** Compares an expression against a list of values and returns the matching result. Cleaner than nested IFs for discrete values.

**VI:** So sánh biểu thức với danh sách giá trị và trả về kết quả khớp. Gọn hơn IF lồng nhau cho các giá trị rời rạc.

### Example | Ví dụ

```
=SWITCH(A2, 1,"January",2,"February",3,"March","Other")
```

| A (Month#) | Result |
|---|---|
| 1 | January |
| 3 | March |
| 9 | Other |

---

## Rank within Groups

**EN:** Rank items within their own group (e.g., rank salespeople per region).

**VI:** Xếp hạng các mục trong nhóm riêng của chúng (ví dụ: xếp hạng nhân viên bán hàng theo khu vực).

### Example | Ví dụ

| A (Region) | B (Name) | C (Sales) | D (Rank in Group) |
|---|---|---|---|
| North | An | 500 | `=COUNTIFS($A$2:$A$7,A2,$C$2:$C$7,">"&C2)+1` |
| North | Binh | 800 | |
| South | Chi | 300 | |
| South | Duc | 650 | |

**Formula for D2:**
```
=COUNTIFS($A$2:$A$7, A2, $C$2:$C$7, ">"&C2) + 1
```

**EN:** Counts how many people in the same region have higher sales, then adds 1 → gives rank 1 to the highest.

**VI:** Đếm bao nhiêu người cùng khu vực có doanh số cao hơn, cộng thêm 1 → xếp hạng 1 cho người cao nhất.

---

## Check if a List is Unique

**EN:** Determine whether a range contains any duplicate entries.

**VI:** Xác định xem một vùng dữ liệu có chứa bất kỳ mục trùng lặp nào không.

### Formula | Công thức

```
=SUMPRODUCT((COUNTIF(A2:A10, A2:A10)>1)*1) = 0
```

**Returns TRUE** if all values are unique, **FALSE** if duplicates exist.

**Trả về TRUE** nếu tất cả giá trị là duy nhất, **FALSE** nếu có trùng lặp.

### Example | Ví dụ

| A (IDs) |
|---|
| 101 |
| 102 |
| 101 |
| 104 |

**Formula:** `=SUMPRODUCT((COUNTIF(A2:A5,A2:A5)>1)*1)=0`

**Result:** `FALSE` *(because 101 appears twice / vì 101 xuất hiện hai lần)*

---

## Compatibility | Tương thích

| Formula | Excel 2016 | Excel 365 | Google Sheets |
|---|---|---|---|
| IF / AND / OR / NOT | ✅ | ✅ | ✅ |
| IFS | ❌ | ✅ | ✅ |
| SWITCH | ❌ | ✅ | ✅ |
| IFERROR / IFNA | ✅ | ✅ | ✅ |

---

*← [Lookup Formulas](lookup.md) | [Text Formulas →](text.md)*
