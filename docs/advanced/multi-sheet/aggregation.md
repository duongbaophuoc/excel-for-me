# Multi-sheet Aggregation / Tổng hợp đa Sheet
## 1. 3D Reference (Excel Only)
- **Task:** Tính tổng ô A1 của Sheet tháng 1 đến tháng 12.
- **Formula:** `=SUM('Tháng 1:Tháng 12'!A1)`

## 2. Query Aggregation (Google Sheets)
- **Formula:** `=QUERY({Sheet1!A:B; Sheet2!A:B}, "SELECT Col1, SUM(Col2) GROUP BY Col1")`
- **Note:** Dấu `{}` dùng để gộp các mảng dữ liệu lại với nhau.
------------------------------
# Multi-sheet Aggregation

=SUM(Sheet1:Sheet10!A1)

={Sheet1!A:B;Sheet2!A:B}

💡 Combine data