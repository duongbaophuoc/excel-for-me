# Formula Performance Optimization | Tối ưu Hiệu năng Công thức

> **Excel & Google Sheets** | Advanced → Performance

---

## Why Formulas Can Slow Down | Lý do công thức chậm

**EN:** Large spreadsheets with volatile functions, excessive array formulas, or cross-sheet references recalculate constantly.  
**VI:** Bảng tính lớn với hàm volatile, công thức mảng nhiều hoặc tham chiếu xuyên sheet tính toán liên tục.

---

## Volatile Functions to Minimize | Hàm volatile cần hạn chế

| Function | Issue | Alternative |
|---|---|---|
| `NOW()` | Recalculates on every change | Store value, use Ctrl+; for static date |
| `TODAY()` | Same | Store as value if static |
| `RAND()` / `RANDBETWEEN()` | Changes every calculation | Paste as values after generating |
| `INDIRECT()` | Forces recalc | Use direct references where possible |
| `OFFSET()` | Volatile | Use INDEX for static ranges |

---

## Replace VLOOKUP with INDEX+MATCH

**EN:** INDEX+MATCH is faster than VLOOKUP on large datasets because it doesn't need to scan entire columns.  
**VI:** INDEX+MATCH nhanh hơn VLOOKUP trên tập dữ liệu lớn vì không cần quét toàn bộ cột.

```
❌ Slow: =VLOOKUP(D2, A:C, 3, 0)
✅ Fast: =INDEX(C:C, MATCH(D2, A:A, 0))
```

---

## Use Tables (ListObjects) | Dùng Bảng (ListObjects)

**EN:** Excel Tables auto-expand, use structured references, and recalculate only changed columns.  
**VI:** Excel Tables tự mở rộng, dùng tham chiếu có cấu trúc và chỉ tính lại cột thay đổi.

```
=SUM(Table1[Sales])        → structured reference
=SUMIF(Table1[Region], "North", Table1[Sales])
```

---

## Manual Calculation Mode

**EN:** Switch to manual recalculation when editing large files.  
**VI:** Chuyển sang chế độ tính tay khi chỉnh sửa file lớn.

- **Formulas → Calculation Options → Manual**
- Press **F9** to recalculate manually

---

## Power Query vs Formulas | Power Query so với Công thức

| Scenario | Recommendation |
|---|---|
| Static data transformation | Power Query (faster, no formula overhead) |
| Dynamic per-cell logic | Formulas |
| Large dataset aggregation | PivotTable or Power Query |

---

*[Best Practices →](best-practices.md)*
