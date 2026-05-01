# Feature Engineering in Excel / Kỹ thuật đặc trưng
- **Binning/Bucketing:** Chuyển đổi dữ liệu số liên tục (Tuổi) sang nhóm (Thanh niên, Trung niên) bằng hàm `LOOKUP`.
- **One-Hot Encoding:** Chuyển dữ liệu phân loại (Màu sắc: Đỏ, Xanh) thành các cột số 0 và 1 bằng hàm `IF`.
- **Scaling:** Chuẩn hóa dữ liệu về khoảng [0, 1] để so sánh các chỉ số khác đơn vị.
  - **Formula:** `=(X - MIN) / (MAX - MIN)`
-------------------
# Feature Engineering

- Normalize
- Encode
- Transform