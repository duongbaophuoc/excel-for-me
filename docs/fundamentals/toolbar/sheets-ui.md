# Google Sheets UI Guide | Hướng dẫn Giao diện Google Sheets

> **Google Sheets** | Fundamentals → Toolbar

---

## Menu Structure | Cấu trúc menu

| Menu | Key Features (EN) | Tính năng chính (VI) |
|---|---|---|
| **File** | Import, Download, Share, Version history | Nhập, Tải xuống, Chia sẻ, Lịch sử |
| **Edit** | Undo, Find & Replace, Paste Special | Hoàn tác, Tìm & Thay, Dán đặc biệt |
| **View** | Freeze, Gridlines, Protected ranges | Cố định, Lưới, Vùng bảo vệ |
| **Insert** | Rows, Columns, Charts, Images, Forms | Hàng, Cột, Biểu đồ, Ảnh, Form |
| **Format** | Number, Text wrapping, Conditional formatting | Số, Bao văn bản, Định dạng điều kiện |
| **Data** | Sort, Filter, Data validation, Pivot table | Sắp xếp, Lọc, Xác thực, Pivot |
| **Tools** | Macros, Apps Script, Notifications | Macro, Apps Script, Thông báo |
| **Extensions** | Add-ons, ChatGPT, etc. | Tiện ích mở rộng |
| **Help** | Function list, Keyboard shortcuts | Danh sách hàm, Phím tắt |

---

## Toolbar Icons | Biểu tượng thanh công cụ

| Icon Group | Functions |
|---|---|
| Undo / Redo | Standard undo/redo |
| Print | Print settings |
| Paint format | Format painter (like Excel) |
| Zoom | 50%–200% view |
| Font controls | Name, Size, Bold, Italic, Color |
| Cell format | $, %, .0, merge, align |
| Borders | All border styles |
| Functions | Insert function (=) |
| Filters | Filter row |
| Links | Insert link |
| Comments | Insert comment |

---

## Sheets-Only Features | Tính năng riêng của Sheets

### Named Functions | Hàm tự đặt tên

**EN:** Create reusable custom formulas without Apps Script.  
**VI:** Tạo công thức tùy chỉnh có thể dùng lại mà không cần Apps Script.

**Data → Named functions → Add new function**

```
Name: TAXCALC
Arguments: income
Formula: =income * 0.1
```

Usage: `=TAXCALC(B2)`

---

### Smart Chips | Thẻ thông minh

**EN:** Insert `@` to embed: People, Files, Dates, Maps, Finance data.  
**VI:** Nhập `@` để nhúng: Người dùng, File, Ngày, Bản đồ, Dữ liệu tài chính.

---

### Connected Sheets (BigQuery) | Kết nối BigQuery

**EN:** Query BigQuery datasets directly inside Sheets.  
**VI:** Truy vấn dữ liệu BigQuery trực tiếp trong Sheets.

`Data → Data connectors → BigQuery`

---

### Protected Ranges | Vùng được bảo vệ

**EN:** Lock specific cells while allowing editing in others.  
**VI:** Khóa ô cụ thể trong khi vẫn cho phép chỉnh sửa ở ô khác.

`Data → Protect sheets and ranges`

---

*← [Excel Ribbon](excel-ribbon.md) | Back to [Fundamentals](../)*
