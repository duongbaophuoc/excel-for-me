# ChatGPT Integration Setup | Cài đặt Tích hợp ChatGPT

> **Excel & Google Sheets** | AI Integration → ChatGPT

---

## Overview | Tổng quan

**EN:** 3 main ways to use ChatGPT with Excel/Sheets:
1. **ChatGPT web** — paste data, ask questions manually
2. **Excel Add-in** — ChatGPT plugin inside Excel ribbon
3. **API via VBA / Apps Script** — fully automated pipeline

**VI:** 3 cách chính dùng ChatGPT với Excel/Sheets:
1. **ChatGPT web** — dán dữ liệu, hỏi thủ công
2. **Add-in Excel** — plugin ChatGPT trong ribbon Excel
3. **API qua VBA / Apps Script** — pipeline tự động hoàn toàn

---

## Method 1: ChatGPT Web | Phương pháp 1: Web

**Best prompts | Prompt tốt nhất:**

```
"I have this Excel data: [paste table].
Write a VLOOKUP formula to find the salary of employee ID 102."

"Write an Excel formula to sum column B where column A equals 'North'
and column C is greater than 1000000."
```

---

## Method 2: Excel Add-in | Phương pháp 2: Add-in

1. Insert → Get Add-ins → Search "GPT for Excel"
2. Install and enter your OpenAI API key
3. Use custom functions: `=AI.ASK("Classify: " & A2)`

---

## Method 3: API Key Setup | API Key

1. Go to `platform.openai.com` → API Keys → Create new key
2. Store in `PARAMS!B1` cell (never hardcode in formulas)
3. Use via VBA or Apps Script — see [formulas.md](formulas.md)

> ⚠️ Never share files with API key embedded.

---

*[Use Cases →](use-cases.md) | [Formulas →](formulas.md)*
