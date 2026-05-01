# Dynamic Reference / Tham chiếu động
## Hàm INDIRECT
- **Task:** Bạn có một ô chọn tên tháng (Sheet name). Bạn muốn công thức tự nhảy vào Sheet đó.
- **Formula:** `=VLOOKUP("Doanh thu", INDIRECT("'" & A1 & "'!A:B"), 2, 0)`
- **Explain:** `A1` chứa chữ "Tháng 5", hàm sẽ tự hiểu là tham chiếu tới `Tháng 5!A:B`.
-----------------
# Dynamic Reference

=INDIRECT(A1 & "!B2")

⚠️ Volatile (slow)