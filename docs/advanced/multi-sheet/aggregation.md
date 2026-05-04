# Multi-Sheet Aggregation | Tổng hợp Đa Sheet

> **Excel & Google Sheets** | Advanced → Multi-Sheet

---

## 3D References | Tham chiếu 3D

**EN:** Sum the same cell across multiple sheets — perfect for monthly or regional workbooks.  
**VI:** Tổng hợp cùng một ô qua nhiều sheet — lý tưởng cho sổ làm việc theo tháng/khu vực.

**Formula:**
```
=SUM(Jan:Dec!B2)
=AVERAGE(Sheet1:Sheet5!C4)
```

> ⚠️ Sheets must be contiguous in the tab bar. / Các sheet phải liền kề trong thanh tab.

---

## SUMIF Across Multiple Sheets

**Formula (Excel 365):**
```
=SUMPRODUCT(SUMIF(INDIRECT("'"&{"Jan","Feb","Mar"}&"'!A:A"),"North",INDIRECT("'"&{"Jan","Feb","Mar"}&"'!B:B")))
```

---

## Consolidate Tool | Công cụ Hợp nhất

**EN:** Use **Data → Consolidate** to merge data from multiple sheets by position or label.  
**VI:** Dùng **Dữ liệu → Hợp nhất** để gộp dữ liệu từ nhiều sheet theo vị trí hoặc nhãn.

---

*← [Advanced](../)*
