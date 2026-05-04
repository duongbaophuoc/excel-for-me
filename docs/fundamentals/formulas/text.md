# Text Formulas | Công thức Văn bản

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [Extract Names (First / Middle / Last)](#extract-names)
- [Abbreviate Names](#abbreviate-names)
- [Remove Alphabets from a String](#remove-alphabets-from-a-string)
- [Remove Numbers from a String](#remove-numbers-from-a-string)
- [Count Characters Without Blanks](#count-characters-without-blanks)
- [Count a Character in a String](#count-a-character-in-a-string)
- [Count Non-Numbers in a String](#count-non-numbers-in-a-string)
- [Count Numbers in a String](#count-numbers-in-a-string)
- [Count Only Alphabets in a String](#count-only-alphabets-in-a-string)
- [Count Words in a Cell / Range](#count-words-in-a-cell--range)
- [Location of First/Last Number in a String](#location-of-firstlast-number-in-a-string)
- [Extract Username and Domain from Email](#extract-username-and-domain-from-email)

---

## Extract Names

### Extract First Name | Trích xuất Tên

**EN:** Extract everything before the first space.  
**VI:** Trích xuất tất cả trước khoảng trắng đầu tiên.

**Formula:**
```
=LEFT(A2, FIND(" ", A2) - 1)
```

### Extract Last Name | Trích xuất Họ

**EN:** Extract everything after the last space.  
**VI:** Trích xuất tất cả sau khoảng trắng cuối cùng.

**Formula:**
```
=RIGHT(A2, LEN(A2) - FIND("*", SUBSTITUTE(A2, " ", "*", LEN(A2) - LEN(SUBSTITUTE(A2," ","")))))
```

### Extract Middle Name | Trích xuất Tên đệm

**Formula:**
```
=MID(A2, FIND(" ",A2)+1, FIND(" ",A2,FIND(" ",A2)+1)-FIND(" ",A2)-1)
```

### Extract Middle Name Initial | Trích xuất Chữ cái đầu Tên đệm

**Formula:**
```
=MID(A2, FIND(" ",A2)+1, 1)
```

### Remove Middle Name | Xóa Tên đệm

**Formula:**
```
=LEFT(A2,FIND(" ",A2)) & RIGHT(A2,LEN(A2)-FIND(" ",A2,FIND(" ",A2)+1))
```

### Full Example | Ví dụ đầy đủ

| A (Full Name) | First | Middle | Last | No Middle |
|---|---|---|---|---|
| Nguyen Van An | Nguyen | Van | An | Nguyen An |
| Tran Thi Bich | Tran | Thi | Bich | Tran Bich |

---

## Abbreviate Names

**EN:** Convert "Nguyen Van An" to "N.V.An" — initials for first/middle, full last name.

**VI:** Chuyển "Nguyen Van An" thành "N.V.An" — viết tắt tên đầu/đệm, giữ nguyên tên cuối.

**Formula:**
```
=LEFT(A2,1)&"."&MID(A2,FIND(" ",A2)+1,1)&"."&RIGHT(A2,LEN(A2)-FIND(" ",A2,FIND(" ",A2)+1))
```

| A (Full Name) | Result |
|---|---|
| Nguyen Van An | N.V.An |
| Le Thi Hoa | L.T.Hoa |

---

## Remove Alphabets from a String

**EN:** Strip all letters, keep only numbers and symbols.  
**VI:** Xóa tất cả chữ cái, chỉ giữ lại số và ký hiệu.

**Formula (Array — Ctrl+Shift+Enter in classic Excel):**
```
=TEXTJOIN("",TRUE,IF(ISNUMBER(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)*1),MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1),""))
```

| A (Input) | Result |
|---|---|
| ABC123DEF456 | 123456 |
| Revenue2024Q1 | 20241 |

---

## Remove Numbers from a String

**EN:** Strip all digits, keep only letters and symbols.  
**VI:** Xóa tất cả chữ số, chỉ giữ lại chữ cái và ký hiệu.

**Formula (Array):**
```
=TEXTJOIN("",TRUE,IF(ISERROR(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)*1),MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1),""))
```

| A (Input) | Result |
|---|---|
| Revenue2024 | Revenue |
| Batch001Test | BatchTest |

---

## Count Characters Without Blanks

**EN:** Count only non-space characters in a string.  
**VI:** Đếm chỉ các ký tự không phải khoảng trắng.

**Formula:**
```
=LEN(SUBSTITUTE(A2," ",""))
```

| A (Text) | LEN(A2) | Without spaces |
|---|---|---|
| "Hello World" | 11 | 10 |
| "Xin chao ban" | 12 | 10 |

---

## Count a Character in a String

**EN:** Count how many times a specific character appears.  
**VI:** Đếm bao nhiêu lần một ký tự cụ thể xuất hiện.

**Formula:** *(Count "a" in A2)*
```
=LEN(A2) - LEN(SUBSTITUTE(A2, "a", ""))
```

| A (Text) | Count of "a" |
|---|---|
| banana | `=LEN(A2)-LEN(SUBSTITUTE(A2,"a",""))` → **3** |
| Excel formula | 1 |

---

## Count Non-Numbers in a String

**Formula:**
```
=SUM(IF(ISERROR(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)*1),1,0))
```
*(Ctrl+Shift+Enter)*

| A (Input) | Non-numeric chars |
|---|---|
| ABC123 | 3 |
| 2024Q1 | 2 |

---

## Count Numbers in a String

**Formula:**
```
=SUM(IF(ISNUMBER(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)*1),1,0))
```
*(Ctrl+Shift+Enter)*

| A (Input) | Numeric chars |
|---|---|
| ABC123 | 3 |
| 2024Q1 | 5 |

---

## Count Only Alphabets in a String

**Formula:**
```
=SUMPRODUCT((CODE(UPPER(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)))>=65)*(CODE(UPPER(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)))<=90))
```

| A (Input) | Alpha count |
|---|---|
| ABC123! | 3 |
| Hello2024 | 5 |

---

## Count Words in a Cell / Range

### Single Cell | Một ô

**Formula:**
```
=LEN(TRIM(A2)) - LEN(SUBSTITUTE(TRIM(A2)," ","")) + 1
```

### Entire Range | Cả vùng dữ liệu

**Formula:**
```
=SUMPRODUCT(LEN(TRIM(A2:A10)) - LEN(SUBSTITUTE(TRIM(A2:A10)," ","")) + (LEN(TRIM(A2:A10))>0))
```

| A (Text) | Word Count |
|---|---|
| Hello World | 2 |
| Xin chao cac ban | 4 |

---

## Location of First/Last Number in a String

### First Number Position | Vị trí số đầu tiên

**Formula:**
```
=MIN(FIND({0,1,2,3,4,5,6,7,8,9}, A2&"0123456789"))
```

### Last Number Position | Vị trí số cuối cùng

**Formula:**
```
=MAX(IF(ISNUMBER(MID(A2,ROW(INDIRECT("1:"&LEN(A2))),1)*1), ROW(INDIRECT("1:"&LEN(A2)))))
```
*(Ctrl+Shift+Enter)*

| A (Input) | First # pos | Last # pos |
|---|---|---|
| AB12CD34 | 3 | 8 |
| Revenue2024 | 8 | 11 |

---

## Extract Username and Domain from Email

### Username (before @) | Tên người dùng

**Formula:**
```
=LEFT(A2, FIND("@", A2) - 1)
```

### Domain (after @) | Tên miền

**Formula:**
```
=RIGHT(A2, LEN(A2) - FIND("@", A2))
```

| A (Email) | Username | Domain |
|---|---|---|
| an.nguyen@company.vn | an.nguyen | company.vn |
| admin@excel.com | admin | excel.com |

---

## Compatibility | Tương thích

| Formula | Excel 2016 | Excel 365 | Google Sheets |
|---|---|---|---|
| LEFT / RIGHT / MID | ✅ | ✅ | ✅ |
| TEXTJOIN | ❌ | ✅ | ✅ |
| FIND / SUBSTITUTE | ✅ | ✅ | ✅ |
| Array formulas | ✅ (CSE) | ✅ (dynamic) | ✅ |

---

*← [Logical Formulas](logical.md) | [Math Formulas →](math.md)*
