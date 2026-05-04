# Dynamic References | Tham chiếu Động

> **Excel & Google Sheets** | Advanced → Multi-Sheet

---

## INDIRECT Function

**Syntax:** `=INDIRECT(ref_text)`

**EN:** Converts a text string into a live cell reference. Enables dynamic sheet/range references.  
**VI:** Chuyển chuỗi văn bản thành tham chiếu ô. Cho phép tham chiếu sheet/vùng linh hoạt.

**Examples:**
```
=INDIRECT("A1")
=INDIRECT("'"&B1&"'!A1")     → Sheet name from B1
=INDIRECT("R"&A1&"C"&B1, FALSE)  → R1C1 style
```

### Example | Ví dụ

| B1 (Sheet) | Formula | Result |
|---|---|---|
| January | `=INDIRECT("'"&B1&"'!B5")` | Value of B5 in January sheet |

---

## Dynamic Named Ranges | Vùng đặt tên động

**Formula (in Name Manager):**
```
=OFFSET(Sheet1!$A$1, 0, 0, COUNTA(Sheet1!$A:$A), 1)
```

Range expands automatically as data grows. / Vùng tự động mở rộng khi dữ liệu tăng.

---

*← [Aggregation](aggregation.md) | [Cross-File →](cross-file.md)*
