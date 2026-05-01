# Logical Functions / Hàm Logic
- **IFS:** `=IFS(A1>90, "A", A1>80, "B", TRUE, "F")`
  - *Dùng thay thế IF lồng nhau để code sạch hơn.*
- **IFERROR:** `=IFERROR(Công_thức, Giá_trị_thay_thế)`
  - *Xử lý các lỗi xấu xí như #N/A hoặc #DIV/0!.*
-------------------
# Logical

=IF(A1>10,"High","Low")
=IFS(A1>90,"A",A1>80,"B")
=AND(A1>0,B1>0)
=OR(A1>0,B1>0)
=IFERROR(A1/B1,0)

💡 Use for decision logic