# Cross-File References | Tham chiếu Xuyên file

> **Excel & Google Sheets** | Advanced → Multi-Sheet

---

## Excel External References

**Syntax:**
```
=[WorkbookName.xlsx]SheetName!$A$1
='C:\\Reports\\[Sales2024.xlsx]January'!$B$5
```

> ⚠️ Use absolute references ($) for cross-file links.

---

## IMPORTRANGE (Google Sheets)

**Syntax:** `=IMPORTRANGE("url", "range")`

```
=IMPORTRANGE("https://docs.google.com/spreadsheets/d/ID", "Sheet1!A1:C100")
```

One-time permission grant required. / Cần cấp quyền một lần.

### Combine with QUERY

```
=QUERY(IMPORTRANGE("URL","Sheet1!A:D"), "SELECT Col1, Col3 WHERE Col2='North'")
```

---

*← [Dynamic References](dynamic-reference.md) | Back to [Advanced](../)*
