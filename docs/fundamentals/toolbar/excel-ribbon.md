# Excel Ribbon Guide | Hướng dẫn Excel Ribbon

> **Excel** | Fundamentals → Toolbar

---

## Overview | Tổng quan

**EN:** The Excel Ribbon organizes commands into tabs and groups. Understanding the layout saves navigation time.

**VI:** Excel Ribbon sắp xếp lệnh thành các tab và nhóm. Hiểu bố cục giúp tiết kiệm thời gian.

---

## Key Tabs | Các tab chính

### Home Tab | Tab Home

| Group | Key Features |
|---|---|
| Clipboard | Cut, Copy, Paste Special |
| Font | Bold, Italic, Font Color, Size |
| Alignment | Wrap Text, Merge & Center |
| Number | Format as Currency, %, Date |
| Styles | Conditional Formatting, Table |
| Cells | Insert/Delete Rows & Columns |
| Editing | AutoSum (Alt+=), Find & Select |

### Insert Tab | Tab Chèn

| Group | Key Features |
|---|---|
| Tables | PivotTable, Table |
| Charts | Bar, Line, Pie, Scatter |
| Sparklines | Mini charts in cells |
| Links | Hyperlink |
| Text | Text Box, Header/Footer |

### Formulas Tab | Tab Công thức

| Group | Key Features |
|---|---|
| Function Library | Insert Function (Shift+F3) |
| Defined Names | Name Manager |
| Formula Auditing | Trace Precedents/Dependents |
| Calculation | Calculate Now (F9) |

### Data Tab | Tab Dữ liệu

| Group | Key Features |
|---|---|
| Get & Transform | Power Query |
| Queries & Connections | Refresh connections |
| Sort & Filter | Sort, Filter, Advanced Filter |
| Data Tools | Text to Columns, Remove Duplicates, Data Validation |
| Forecast | What-If Analysis, Forecast Sheet |

### Review Tab | Tab Kiểm tra

| Group | Key Features |
|---|---|
| Proofing | Spelling (F7) |
| Protect | Protect Sheet, Protect Workbook |
| Comments | New Comment, Show All |

### View Tab | Tab Xem

| Group | Key Features |
|---|---|
| Workbook Views | Normal, Page Layout, Page Break |
| Show | Formula Bar, Gridlines, Headings |
| Freeze Panes | Freeze Top Row, First Column |
| Window | Split, New Window, Arrange All |
| Macros | View / Record Macro |

---

## Quick Access Toolbar (QAT) | Thanh công cụ nhanh

**EN:** Add your most-used commands to the QAT for one-click access.  
**VI:** Thêm lệnh dùng nhiều nhất vào QAT để truy cập một clic.

**Recommended QAT commands:**
- Save (Ctrl+S)
- Undo / Redo
- Sort Ascending / Descending
- Print Preview
- Format Painter

**How to add:** Right-click any button → "Add to Quick Access Toolbar"

---

## File Info Formulas | Công thức thông tin file

### Get File Name | Lấy tên file

```
=RIGHT(CELL("filename",A1),LEN(CELL("filename",A1))-FIND("[",CELL("filename",A1)))
```

> ⚠️ File must be saved first. Returns `""` for unsaved files.

### Get Workbook Name | Lấy tên workbook

```
=MID(CELL("filename",A1),FIND("[",CELL("filename",A1))+1,FIND("]",CELL("filename",A1))-FIND("[",CELL("filename",A1))-1)
```

### Get Sheet Name | Lấy tên sheet

```
=RIGHT(CELL("filename",A1),LEN(CELL("filename",A1))-FIND("]",CELL("filename",A1)))
```

### Get Workbook Directory | Lấy đường dẫn thư mục

```
=LEFT(CELL("filename",A1),FIND("[",CELL("filename",A1))-1)
```

| Formula | Example Result |
|---|---|
| File Name | SalesReport.xlsx] |
| Workbook Name | SalesReport.xlsx |
| Sheet Name | Sheet1 |
| Directory | C:\Users\User\Documents\ |

---

*← Back to [Fundamentals](../)*
