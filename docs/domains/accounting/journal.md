# Journal Entries | Bút toán Kế toán

> **Excel & Google Sheets** | Domains → Accounting

---

## Journal Entry Template | Mẫu Bút toán

| Date | Ref# | Account Code | Account Name | Debit | Credit | Description |
|---|---|---|---|---|---|---|
| 2024-01-15 | JE001 | 1111 | Cash | 50,000,000 | | Received payment |
| 2024-01-15 | JE001 | 4111 | Revenue | | 50,000,000 | Received payment |

---

## Validation Formulas | Công thức kiểm tra

### Debit = Credit Check | Kiểm tra Nợ = Có

```
=SUMIF(C:C, "Debit", E:E) - SUMIF(C:C, "Credit", F:F)
```
Should equal 0 for balanced entries. / Phải bằng 0 cho bút toán cân bằng.

### Running Balance | Số dư lũy kế

```
=B2 + SUMIF($A$2:A2, A2, $C$2:C2) - SUMIF($A$2:A2, A2, $D$2:D2)
```

---

## Trial Balance | Bảng Cân đối Thử

**SUMIF by account:**
```
=SUMIF(JournalData!C:C, A2, JournalData!E:E)  → Total Debits for account
=SUMIF(JournalData!C:C, A2, JournalData!F:F)  → Total Credits for account
```

---

*← [Reconciliation](reconciliation.md)*
