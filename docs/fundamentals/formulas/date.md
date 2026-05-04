# Date & Time Formulas | Công thức Ngày & Giờ

> **Excel & Google Sheets** | Fundamentals → Formulas

---

## Table of Contents | Mục lục

- [Add / Subtract Months from a Date](#add--subtract-months)
- [Add / Subtract Years from a Date](#add--subtract-years)
- [Convert Number to Month Name](#convert-number-to-month-name)
- [Convert Date to Calendar Quarter](#convert-date-to-calendar-quarter)
- [Convert Date to Indian Financial Year Quarter](#convert-date-to-financial-year-quarter)
- [Calculate Age from Birthday](#calculate-age-from-birthday)
- [Number to Date Format Conversion](#number-to-date-format-conversion)
- [Number to Time Format Conversion](#number-to-time-format-conversion)
- [Days in a Month](#days-in-a-month)
- [Leap Year Check](#leap-year-check)
- [First Day of the Month](#first-day-of-the-month)
- [Last Day of the Month](#last-day-of-the-month)
- [First Working Day of the Month](#first-working-day-of-the-month)
- [Last Working Day of the Month](#last-working-day-of-the-month)
- [Count Mondays (or Any Weekday) Between 2 Dates](#count-weekdays-between-2-dates)
- [Find Next/Previous Weekday](#find-nextprevious-weekday)
- [Date for Nth Day of the Year](#date-for-nth-day-of-the-year)
- [Convert to Julian Date and Back](#julian-date)
- [Extract Date and Time from Timestamp](#extract-date-and-time-from-timestamp)
- [Convert Number to Years and Months](#convert-number-to-years-and-months)
- [Financial Year Formula](#financial-year-formula)
- [First/Last Working Day of the Year](#firstlast-working-day-of-the-year)
- [Maximum Consecutive Occurrences](#maximum-consecutive-occurrences)

---

## Add / Subtract Months

**EN:** Add or subtract a number of months from a date. Use `EDATE`.  
**VI:** Cộng hoặc trừ số tháng từ một ngày. Dùng `EDATE`.

**Syntax:** `=EDATE(start_date, months)`

| A (Date) | Formula | Result |
|---|---|---|
| 2024-01-15 | `=EDATE(A2, 3)` | 2024-04-15 |
| 2024-01-15 | `=EDATE(A2, -2)` | 2023-11-15 |

---

## Add / Subtract Years

**EN:** Add or subtract years by multiplying by 12 with EDATE.  
**VI:** Cộng hoặc trừ năm bằng cách nhân với 12 trong EDATE.

**Formula:** *(Add 2 years)*
```
=EDATE(A2, 2*12)
```

**Alternative:** *(More explicit)*
```
=DATE(YEAR(A2)+2, MONTH(A2), DAY(A2))
```

| A (Date) | +2 Years |
|---|---|
| 2022-06-01 | 2024-06-01 |

---

## Convert Number to Month Name

**Formula:**
```
=TEXT(DATE(2000, A2, 1), "MMMM")
```

**Short name (Jan, Feb...):**
```
=TEXT(DATE(2000, A2, 1), "MMM")
```

| A (Month #) | Full Name | Short |
|---|---|---|
| 1 | January | Jan |
| 6 | June | Jun |
| 12 | December | Dec |

---

## Convert Date to Calendar Quarter

**Formula:**
```
=ROUNDUP(MONTH(A2)/3, 0)
```

**With "Q" prefix:**
```
="Q"&ROUNDUP(MONTH(A2)/3,0)
```

| A (Date) | Quarter |
|---|---|
| 2024-02-10 | Q1 |
| 2024-07-05 | Q3 |
| 2024-11-30 | Q4 |

---

## Convert Date to Financial Year Quarter

**EN:** Indian FY starts April 1. Q1 = Apr–Jun, Q2 = Jul–Sep, Q3 = Oct–Dec, Q4 = Jan–Mar.  
**VI:** Năm tài chính Ấn Độ bắt đầu từ 1/4. Q1 = Tháng 4–6, v.v.

**Formula:**
```
=CHOOSE(MONTH(A2),4,4,4,1,1,1,2,2,2,3,3,3)
```

| A (Date) | FY Quarter |
|---|---|
| 2024-04-01 | 1 |
| 2024-10-15 | 3 |
| 2024-02-28 | 4 |

---

## Calculate Age from Birthday

**Formula using DATEDIF:**
```
=DATEDIF(A2, TODAY(), "Y")
```

**Full Age (Y years, M months, D days):**
```
=DATEDIF(A2,TODAY(),"Y")&" years, "&DATEDIF(A2,TODAY(),"YM")&" months, "&DATEDIF(A2,TODAY(),"MD")&" days"
```

| A (Birthdate) | Age |
|---|---|
| 1990-05-15 | 34 |
| 2000-12-01 | 23 |

> ⚠️ `DATEDIF` is undocumented but works in all Excel versions and Google Sheets.

---

## Number to Date Format Conversion

**EN:** Convert a number like 20240115 to a proper date 2024-01-15.  
**VI:** Chuyển số như 20240115 thành ngày đúng định dạng 2024-01-15.

**Formula:**
```
=DATE(LEFT(A2,4), MID(A2,5,2), RIGHT(A2,2))
```

| A (Number) | Date |
|---|---|
| 20240115 | 2024-01-15 |
| 20231231 | 2023-12-31 |

---

## Number to Time Format Conversion

**EN:** Convert a number like 1430 to time 14:30.  
**VI:** Chuyển số như 1430 thành giờ 14:30.

**Formula:**
```
=TIME(INT(A2/100), MOD(A2,100), 0)
```

| A (Number) | Time |
|---|---|
| 1430 | 14:30 |
| 900 | 09:00 |

---

## Days in a Month

**Formula:**
```
=DAY(EOMONTH(A2, 0))
```

| A (Date) | Days in Month |
|---|---|
| 2024-02-01 | 29 (leap year) |
| 2024-01-15 | 31 |

---

## Leap Year Check

**Formula:**
```
=IF(OR(MOD(YEAR(A2),400)=0, AND(MOD(YEAR(A2),4)=0, MOD(YEAR(A2),100)<>0)), "Leap Year","Not Leap Year")
```

**Shorter:**
```
=DAY(DATE(YEAR(A2),3,0))=29
```
*(Returns TRUE for leap year)*

| A (Date) | Leap Year? |
|---|---|
| 2024-01-01 | TRUE |
| 2023-01-01 | FALSE |
| 2100-01-01 | FALSE |

---

## First Day of the Month

**Formula:**
```
=A2 - DAY(A2) + 1
```

**Or:** `=EOMONTH(A2, -1) + 1`

| A (Date) | First Day |
|---|---|
| 2024-07-15 | 2024-07-01 |

---

## Last Day of the Month

**Formula:**
```
=EOMONTH(A2, 0)
```

| A (Date) | Last Day |
|---|---|
| 2024-02-15 | 2024-02-29 |
| 2024-07-01 | 2024-07-31 |

---

## First Working Day of the Month

**EN:** Skip weekends for the first working day.  
**VI:** Bỏ qua cuối tuần để lấy ngày làm việc đầu tiên.

**Formula:**
```
=WORKDAY(EOMONTH(A2,-1), 1)
```

| A (Date) | First Working Day |
|---|---|
| 2024-06-15 | 2024-06-03 (Mon, if Jun 1 is Sat) |

---

## Last Working Day of the Month

**Formula:**
```
=WORKDAY(EOMONTH(A2,0)+1, -1)
```

| A (Date) | Last Working Day |
|---|---|
| 2024-06-15 | 2024-06-28 (Fri) |

---

## Count Weekdays Between 2 Dates

**EN:** Count the number of Mondays (or any specific weekday) between two dates.  
**VI:** Đếm số ngày Thứ Hai (hoặc bất kỳ thứ nào) giữa hai ngày.

**Formula:** *(Count Mondays — weekday 2)*
```
=SUMPRODUCT((WEEKDAY(ROW(INDIRECT(A2&":"&B2)),2)=1)*1)
```

**Simpler approach:**
```
=INT((B2-A2-WEEKDAY(B2,2)+1+7)/7)
```
*(Adjust +1 offset to change target weekday)*

| A (Start) | B (End) | Mondays |
|---|---|---|
| 2024-01-01 | 2024-01-31 | 4 |

---

## Find Next/Previous Weekday

### Next Monday after a date | Thứ Hai tiếp theo

**Formula:**
```
=A2 + MOD(2 - WEEKDAY(A2, 2), 7) + IF(MOD(2-WEEKDAY(A2,2),7)=0, 7, 0)
```

**Simplified (next specific weekday n=2 for Mon):**
```
=A2 + MOD(2-WEEKDAY(A2)+7, 7) + IF(MOD(2-WEEKDAY(A2)+7,7)=0,7,0)
```

### Previous Monday | Thứ Hai trước đó

**Formula:**
```
=A2 - MOD(WEEKDAY(A2, 2) - 1, 7) - IF(MOD(WEEKDAY(A2,2)-1,7)=0, 7, 0)
```

---

## Date for Nth Day of the Year

**EN:** Get the date of the Nth day (e.g., day 100) of a given year.  
**VI:** Lấy ngày tương ứng với ngày thứ N (ví dụ: ngày 100) của năm.

**Formula:**
```
=DATE(A2, 1, B2)
```

| A (Year) | B (Day#) | Date |
|---|---|---|
| 2024 | 100 | 2024-04-09 |
| 2024 | 1 | 2024-01-01 |

---

## Julian Date

### Excel (Gregorian) → Julian | Chuyển sang Julian

**Formula:**
```
=A2-DATE(YEAR(A2),1,0)+INT(7*YEAR(A2)/100)
```

*(Standard Julian Day Number approximation)*

### Julian → Excel (Gregorian) | Julian về Gregorian

**Formula:**
```
=A2+DATE(YEAR(A2),1,0)-INT(7*YEAR(A2)/100)
```

---

## Extract Date and Time from Timestamp

### Extract Date | Trích xuất Ngày

```
=INT(A2)
```
*(Then format as Date)*

### Extract Time | Trích xuất Giờ

```
=MOD(A2, 1)
```
*(Then format as Time)*

| A (Timestamp) | Date | Time |
|---|---|---|
| 2024-07-15 14:30 | 2024-07-15 | 14:30 |

---

## Convert Number to Years and Months

**EN:** Convert 14 months → "1 Year, 2 Months".  
**VI:** Chuyển 14 tháng thành "1 Năm, 2 Tháng".

**Formula:**
```
=INT(A2/12)&" Year(s), "&MOD(A2,12)&" Month(s)"
```

| A (Months) | Result |
|---|---|
| 14 | 1 Year(s), 2 Month(s) |
| 36 | 3 Year(s), 0 Month(s) |

---

## Financial Year Formula

**EN:** Return financial year label like "2024-25" or "FY25" for a given date.  
**VI:** Trả về nhãn năm tài chính như "2024-25" hoặc "FY25".

**Formula (April–March FY):**
```
=IF(MONTH(A2)>=4, YEAR(A2)&"-"&RIGHT(YEAR(A2)+1,2), YEAR(A2)-1&"-"&RIGHT(YEAR(A2),2))
```

**FY Label (FY25 style):**
```
=IF(MONTH(A2)>=4, "FY"&RIGHT(YEAR(A2)+1,2), "FY"&RIGHT(YEAR(A2),2))
```

| A (Date) | FY Label |
|---|---|
| 2024-05-01 | 2024-25 |
| 2024-02-15 | 2023-24 |

---

## First/Last Working Day of the Year

### First Working Day | Ngày làm việc đầu năm

**Formula:**
```
=WORKDAY(DATE(A2,1,0), 1)
```

### Last Working Day | Ngày làm việc cuối năm

**Formula:**
```
=WORKDAY(DATE(A2,12,32), -1)
```

---

## Maximum Consecutive Occurrences

**EN:** Find the maximum number of times a particular value appears consecutively.  
**VI:** Tìm số lần tối đa một giá trị xuất hiện liên tiếp.

**Formula:**
```
=MAX(FREQUENCY(IF(A2:A20="Win",ROW(A2:A20)),IF(A2:A20<>"Win",ROW(A2:A20))))
```
*(Ctrl+Shift+Enter)*

| A (Results) |
|---|
| Win |
| Win |
| Lose |
| Win |
| Win |
| Win |

**Result:** `3` *(three Wins in a row)*

---

## Compatibility | Tương thích

| Formula | Excel 2016 | Excel 365 | Google Sheets |
|---|---|---|---|
| EDATE / EOMONTH | ✅ | ✅ | ✅ |
| DATEDIF | ✅ | ✅ | ✅ |
| WORKDAY / NETWORKDAYS | ✅ | ✅ | ✅ |
| WEEKDAY | ✅ | ✅ | ✅ |

---

*← [Math Formulas](math.md) | [Array Formulas →](array.md)*
