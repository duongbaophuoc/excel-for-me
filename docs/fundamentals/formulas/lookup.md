# 🔍 Lookup Functions

## 🇺🇸 English

### XLOOKUP ⭐

#### Description
Modern lookup function replacing VLOOKUP.

#### Syntax
=XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found])

#### Example
=XLOOKUP(A2, A:A, B:B, "Not Found")

#### Tips
- Can lookup left or right
- Handles errors directly

#### Common Errors
- #N/A when not found

---

### INDEX + MATCH

#### Syntax
=INDEX(B:B, MATCH(A2, A:A, 0))

#### Example
=INDEX(B:B, MATCH("Apple", A:A, 0))

---

## 🇻🇳 Tiếng Việt

### XLOOKUP ⭐

#### Mô tả
Hàm tra cứu hiện đại thay thế VLOOKUP.

#### Cú pháp
=XLOOKUP(giá_trị, vùng_tìm, vùng_trả_về, [không_tìm_thấy])

#### Ví dụ
=XLOOKUP(A2, A:A, B:B, "Không tìm thấy")

#### Mẹo
- Có thể tìm trái/phải
- Không cần IFERROR

#### Lỗi thường gặp
- #N/A khi không tìm thấy

---

### INDEX + MATCH

#### Cú pháp
=INDEX(B:B, MATCH(A2, A:A, 0))

#### Ví dụ
=INDEX(B:B, MATCH("Apple", A:A, 0))
