# Spreadsheet Best Practices | Thực hành Tốt nhất

> **Excel & Google Sheets** | Advanced → Performance

---

## Data Architecture | Kiến trúc Dữ liệu

### Separation of Concerns | Phân tách trách nhiệm

```
Sheet: RAW_DATA    → never edit manually, import/paste only
Sheet: CALC        → intermediate calculations
Sheet: OUTPUT      → final tables, charts, dashboards
Sheet: PARAMS      → constants, lookup tables, config values
```

---

## Naming Conventions | Quy ước Đặt tên

| Element | Convention | Example |
|---|---|---|
| Sheets | PascalCase | `SalesData`, `MonthlyReport` |
| Named ranges | snake_case | `tax_rate`, `base_salary` |
| Columns | No spaces | `OrderDate`, `UnitPrice` |
| Files | kebab-case | `annual-budget-2024.xlsx` |

---

## Formula Rules | Quy tắc công thức

- ✅ Lock lookup tables with absolute references: `$A$1:$C$100`
- ✅ Use named ranges for constants: `=sales * tax_rate`
- ✅ Avoid selecting entire columns (A:A) in large files — use bounded ranges
- ✅ Add input validation to prevent wrong data types
- ❌ Avoid deeply nested IF (use IFS or SWITCH)
- ❌ Avoid circular references unless intentional
- ❌ Avoid hardcoding values inside formulas

---

## Version Control | Quản lý phiên bản

- Name files: `report-v1.0-2024-01.xlsx`, `report-v1.1-2024-02.xlsx`
- Use Google Sheets' **File → Version history** for automatic versioning
- Export to CSV for key snapshots

---

*← [Optimization](optimization.md)*
