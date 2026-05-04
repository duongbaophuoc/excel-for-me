# Pivot Tables | Bảng Pivot

> **Excel & Google Sheets** | Domains → Data Analysis

---

## Creating a Pivot Table | Tạo Bảng Pivot

**EN:** Pivot tables summarize large datasets dynamically without formulas.  
**VI:** Bảng Pivot tóm tắt tập dữ liệu lớn một cách linh hoạt mà không cần công thức.

**Steps | Các bước:**
1. Click inside your data table
2. Insert → PivotTable
3. Choose New Worksheet
4. Drag fields to Rows, Columns, Values, Filters

---

## Field Settings | Cài đặt trường

| Area | Usage (EN) | Cách dùng (VI) |
|---|---|---|
| **Rows** | Category grouping | Nhóm theo danh mục |
| **Columns** | Horizontal grouping | Nhóm theo chiều ngang |
| **Values** | Aggregation (SUM, COUNT...) | Tổng hợp |
| **Filters** | Global filter | Lọc toàn cục |

---

## Calculated Fields | Trường tính toán

**EN:** Create custom formulas inside the PivotTable.  
**VI:** Tạo công thức tùy chỉnh bên trong PivotTable.

**Access:** PivotTable Analyze → Fields, Items & Sets → Calculated Field

**Example:**
```
Name: Profit Margin
Formula: = Revenue - Cost
```

---

## GETPIVOTDATA Formula | Hàm GETPIVOTDATA

**EN:** Extract specific values from a PivotTable with a formula.  
**VI:** Trích xuất giá trị cụ thể từ PivotTable bằng công thức.

**Formula (auto-generated when you click a pivot cell):**
```
=GETPIVOTDATA("Sales", $A$3, "Region", "North", "Product", "Apple")
```

---

## Slicers & Timelines | Bộ cắt & Dòng thời gian

- **Slicer:** PivotTable Analyze → Insert Slicer → click to filter
- **Timeline:** Insert → Timeline → filter by date period

---

*← [Aggregation](aggregation.md)*
