# Reconciliation | Đối soát Kế toán

> **Excel & Google Sheets** | Domains → Accounting

---

## Bank Reconciliation | Đối soát Ngân hàng

**EN:** Match transactions between your ledger and bank statement.  
**VI:** Khớp giao dịch giữa sổ cái và sao kê ngân hàng.

### Match Formula | Công thức khớp

**Check if ledger transaction exists in bank statement:**
```
=IFERROR(VLOOKUP(A2, BankData!$A:$C, 1, 0), "NOT IN BANK")
```

**Using MATCH:**
```
=IF(ISNA(MATCH(A2&B2, BankData!$A:$A&BankData!$B:$B, 0)), "Unmatched", "Matched")
```
*(Ctrl+Shift+Enter for array)*

---

## Identify Unmatched Items | Tìm mục không khớp

**SUMIF check — amounts that appear in ledger but not bank:**
```
=SUMPRODUCT((ISNA(MATCH(A2:A100, BankData!A:A, 0)))*B2:B100)
```

---

## Duplicate Detection | Phát hiện trùng lặp

```
=COUNTIF($A$2:$A2, A2) > 1    → True if this is a duplicate
```

**Highlight duplicates with Conditional Formatting:**
`=COUNTIF($A$2:$A$100, A2)>1`

---

*[Journal →](journal.md)*
