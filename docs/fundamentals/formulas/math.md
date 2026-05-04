# Math & Statistical Formulas | Công thức Toán học & Thống kê

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [SUM of Digits](#sum-of-digits)
- [Numerology Sum (Reduce to Single Digit)](#numerology-sum)
- [Count Unique Values](#count-unique-values)
- [Count Unique Values Conditionally](#count-unique-values-conditionally)
- [Most Frequently Occurring Value](#most-frequently-occurring-value)
- [COUNTIF on Filtered List](#countif-on-filtered-list)
- [SUMIF on Filtered List](#sumif-on-filtered-list)
- [Sum Bottom N Values](#sum-bottom-n-values)
- [Sum Every Nth Row](#sum-every-nth-row)
- [MAXIF / MINIF](#maxif--minif)
- [MEDIANIF / MODEIF](#medianif--modeif)
- [Count No. of Cells Having Numbers Only](#count-number-only-cells)
- [Count No. of Cells Having Characters Only](#count-character-only-cells)
- [Find Nth Largest with Duplicates](#find-nth-largest-with-duplicates)
- [Generate Unique List from Duplicates](#generate-unique-list-from-duplicates)
- [Roman Numerals](#roman-numerals)
- [Extract Integer and Decimal Portions](#extract-integer-and-decimal)
- [Geometric Mean Ignoring Zero/Negative](#geometric-mean)
- [Rank within Groups](#rank-within-groups)
- [COUNTIF for Non-Contiguous Range](#countif-non-contiguous)
- [Sequential & Repeating Number Patterns](#sequential--repeating-number-patterns)
- [Non-Repeating Random Numbers](#non-repeating-random-numbers)
- [Column Name / Range from Number](#column-name-from-number)

---

## SUM of Digits

### All Numbers | Tất cả số

**EN:** Sum the individual digits of a number (e.g., 1234 → 1+2+3+4 = 10).  
**VI:** Cộng từng chữ số của một số (ví dụ: 1234 → 1+2+3+4 = 10).

**Formula (Ctrl+Shift+Enter):**
```
=SUMPRODUCT(MID(A2, ROW(INDIRECT("1:"&LEN(A2))), 1) * 1)
```

### Mixed Numbers and Text | Hỗn hợp số và chữ

**Formula (Ctrl+Shift+Enter):**
```
=SUMPRODUCT(IFERROR(MID(A2, ROW(INDIRECT("1:"&LEN(A2))), 1) * 1, 0))
```

| A (Input) | Sum of digits |
|---|---|
| 1234 | 10 |
| AB12CD3 | 6 |

---

## Numerology Sum

**EN:** Repeatedly sum digits until a single digit remains (e.g., 9876 → 30 → 3).  
**VI:** Cộng chữ số liên tục cho đến khi còn một chữ số (ví dụ: 9876 → 30 → 3).

**Formula:**
```
=MOD(A2-1, 9) + 1
```

| A (Number) | Numerology Sum |
|---|---|
| 9876 | 3 |
| 1234 | 1 |
| 9 | 9 |

---

## Count Unique Values

**EN:** Count the number of unique (distinct) values in a range.  
**VI:** Đếm số lượng giá trị duy nhất (không trùng) trong vùng dữ liệu.

**Formula:**
```
=SUMPRODUCT(1/COUNTIF(A2:A10, A2:A10))
```

> ⚠️ Fails if range contains blank cells. Use the version below for blanks.

**Formula with blanks | Công thức khi có ô rỗng:**
```
=SUMPRODUCT((A2:A10<>"")/COUNTIF(A2:A10, A2:A10&""))
```

| A (Values) |
|---|
| Apple |
| Banana |
| Apple |
| Cherry |

**Result:** `3` *(Apple, Banana, Cherry)*

---

## Count Unique Values Conditionally

**EN:** Count unique values that meet a condition (like COUNTIF but for unique values).  
**VI:** Đếm giá trị duy nhất thỏa mãn điều kiện.

**Formula:** *(Unique Products in "North" region)*
```
=SUMPRODUCT((A2:A10="North")/COUNTIFS(A2:A10, A2:A10, B2:B10, B2:B10))
```

| A (Region) | B (Product) |
|---|---|
| North | Apple |
| North | Apple |
| North | Mango |
| South | Apple |

**Result:** `2` *(North has Apple + Mango)*

---

## Most Frequently Occurring Value

### For Text | Cho văn bản

**Formula:**
```
=INDEX(A2:A10, MATCH(MAX(COUNTIF(A2:A10, A2:A10)), COUNTIF(A2:A10, A2:A10), 0))
```
*(Ctrl+Shift+Enter)*

### For Numbers | Cho số

**Formula:**
```
=MODE(A2:A10)
```

| A (Values) | Formula Result |
|---|---|
| Apple | Apple |
| Banana | |
| Apple | |
| Cherry | |

---

## COUNTIF on Filtered List

**EN:** COUNTIF counts hidden rows too. To count only visible rows, use SUBTOTAL.  
**VI:** COUNTIF đếm cả hàng ẩn. Để đếm chỉ hàng hiển thị, dùng SUBTOTAL.

**Formula:**
```
=SUMPRODUCT((A2:A100="Apple") * SUBTOTAL(103, OFFSET(A2, ROW(A2:A100)-ROW(A2), 0)))
```

---

## SUMIF on Filtered List

**EN:** Sum only visible rows that match a condition.  
**VI:** Tính tổng chỉ các hàng hiển thị thỏa mãn điều kiện.

**Formula:**
```
=SUMPRODUCT((A2:A100="North") * B2:B100 * SUBTOTAL(103, OFFSET(A2, ROW(A2:A100)-ROW(A2), 0)))
```

---

## Sum Bottom N Values

**EN:** Sum the N smallest values in a range.  
**VI:** Tính tổng N giá trị nhỏ nhất trong vùng dữ liệu.

**Formula:** *(Sum bottom 3)*
```
=SUMPRODUCT(SMALL(A2:A10, ROW(INDIRECT("1:3"))))
```

| A (Values) | Bottom 3 sum |
|---|---|
| 10 | 6+8+9 = **23** |
| 8 | |
| 25 | |
| 6 | |
| 9 | |

---

## Sum Every Nth Row

**EN:** Sum every 3rd row (or any N).  
**VI:** Tính tổng cứ mỗi hàng thứ 3 (hoặc bất kỳ N nào).

**Formula:** *(Sum every 3rd row starting from row 1)*
```
=SUMPRODUCT((MOD(ROW(A1:A30)-ROW(A1),3)=0)*A1:A30)
```

| A (Values) | Every 3rd sum |
|---|---|
| 10 (row 1) | 10+40+70 = 120 |
| 20 | |
| 30 | |
| 40 (row 4) | |

---

## MAXIF / MINIF

> 🆕 MAXIFS / MINIFS available in Excel 2019+, Google Sheets

### MAXIF (Excel 2016 — array)

**Formula:**
```
=MAX(IF(A2:A10="North", B2:B10))
```
*(Ctrl+Shift+Enter)*

### MAXIFS (Excel 365 / 2019+)

**Formula:**
```
=MAXIFS(B2:B10, A2:A10, "North")
```

### MINIF / MINIFS — same pattern

| A (Region) | B (Sales) | Max North | Min North |
|---|---|---|---|
| North | 500 | 800 | 500 |
| North | 800 | | |
| South | 300 | | |

---

## MEDIANIF / MODEIF

**EN:** Excel has no built-in MEDIANIF. Use an array formula.  
**VI:** Excel không có hàm MEDIANIF sẵn có. Dùng công thức mảng.

### MEDIANIF

**Formula:**
```
=MEDIAN(IF(A2:A10="North", B2:B10))
```
*(Ctrl+Shift+Enter)*

### MODEIF

**Formula:**
```
=MODE(IF(A2:A10="North", B2:B10))
```
*(Ctrl+Shift+Enter)*

---

## Count Number-Only Cells

**Formula:**
```
=SUMPRODUCT((LEN(TRIM(A2:A10))=LEN(SUBSTITUTE(TRIM(A2:A10)," ","")))*(A2:A10<>"")*(ISNUMBER(A2:A10*1)))
```

**Simpler version:**
```
=COUNT(A2:A10)
```
*(COUNT only counts cells containing numbers)*

---

## Count Character-Only Cells

**Formula:**
```
=SUMPRODUCT((NOT(ISNUMBER(A2:A10)))*(A2:A10<>"")*(ISTEXT(A2:A10)))
```

---

## Find Nth Largest with Duplicates

**EN:** `LARGE` with duplicates returns the same value. Use COUNTIF to find the true nth unique large value.  
**VI:** `LARGE` với trùng lặp trả về cùng giá trị. Dùng COUNTIF để tìm giá trị lớn thứ n thực sự.

**Formula:** *(3rd largest, treating duplicates as one)*
```
=LARGE(IF(MATCH(A2:A10,A2:A10,0)=ROW(A2:A10)-ROW(A2)+1,A2:A10),3)
```
*(Ctrl+Shift+Enter)*

---

## Generate Unique List from Duplicates

**Formula:** *(Extract unique values — classic Excel)*
```
=IFERROR(INDEX($A$2:$A$10, MATCH(0, COUNTIF($B$1:B1, $A$2:$A$10), 0)), "")
```
*(Ctrl+Shift+Enter, drag down)*

> 🆕 In Excel 365 / Google Sheets: `=UNIQUE(A2:A10)`

---

## Roman Numerals

**Syntax:** `=ROMAN(number, [form])`

**Formula:**
```
=ROMAN(2024)
```

| Number | Roman |
|---|---|
| 2024 | MMXXIV |
| 14 | XIV |
| 9 | IX |

---

## Extract Integer and Decimal

### Integer Part | Phần nguyên

```
=INT(A2)          → 3  (from 3.75)
=TRUNC(A2)        → 3  (from 3.75)
```

### Decimal Part | Phần thập phân

```
=A2 - INT(A2)     → 0.75  (from 3.75)
=MOD(A2, 1)       → 0.75
```

---

## Geometric Mean

**EN:** Calculate geometric mean, ignoring zeroes and negative values.  
**VI:** Tính trung bình nhân, bỏ qua giá trị 0 và âm.

**Formula:**
```
=EXP(AVERAGEIF(A2:A10, ">0", LN(A2:A10)))
```

| A (Values) | Geometric Mean |
|---|---|
| 2 | ≈ 4.16 |
| 8 | |
| -3 (ignored) | |
| 4 | |
| 0 (ignored) | |

---

## COUNTIF Non-Contiguous Range

**EN:** Apply COUNTIF across non-contiguous ranges.  
**VI:** Áp dụng COUNTIF trên nhiều vùng không liên tiếp.

**Formula:**
```
=COUNTIF(A2:A10,"Apple") + COUNTIF(C2:C10,"Apple") + COUNTIF(E2:E10,"Apple")
```

**Or using SUMPRODUCT:**
```
=SUMPRODUCT(COUNTIF(INDIRECT({"A2:A10","C2:C10","E2:E10"}),"Apple"))
```

---

## Sequential & Repeating Number Patterns

### Generate 1,2,3,1,2,3... | Tạo chuỗi lặp

**Formula:**
```
=MOD(ROW(A1)-1, 3) + 1
```

### Repeat and Increment: 1,1,1,2,2,2,3,3,3...

**Formula:**
```
=INT((ROW(A1)-1)/3) + 1
```

---

## Non-Repeating Random Numbers

**EN:** Generate unique random integers between 1 and N.  
**VI:** Tạo số nguyên ngẫu nhiên không trùng lặp từ 1 đến N.

**Formula approach:** Add helper column with `=RAND()`, then rank:
```
=RANK(B2, $B$2:$B$11, 1)
```

> 🆕 In Excel 365: `=SORTBY(SEQUENCE(10), RANDARRAY(10))`

---

## Column Name from Number

**EN:** Get Excel column letter(s) from a column number.  
**VI:** Lấy tên cột Excel từ số thứ tự cột.

**Formula:**
```
=SUBSTITUTE(ADDRESS(1, A2, 4), "1", "")
```

| A (Col #) | Column Name |
|---|---|
| 1 | A |
| 26 | Z |
| 27 | AA |
| 703 | AAA |

### Get Column Range | Lấy vùng cột

**Formula:** *(Get range string for column 3, rows 2–100)*
```
=SUBSTITUTE(ADDRESS(2,A2,4),1,"")&"2:"&SUBSTITUTE(ADDRESS(1,A2,4),1,"")&"100"
```

---

## Compatibility | Tương thích

| Formula | Excel 2016 | Excel 365 | Google Sheets |
|---|---|---|---|
| SUMPRODUCT | ✅ | ✅ | ✅ |
| MAXIFS / MINIFS | ❌ | ✅ | ✅ |
| UNIQUE | ❌ | ✅ | ✅ |
| SORTBY / SEQUENCE | ❌ | ✅ | ✅ |
| ROMAN | ✅ | ✅ | ✅ |

---

*← [Text Formulas](text.md) | [Date Formulas →](date.md)*
