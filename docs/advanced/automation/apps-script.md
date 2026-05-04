# Google Apps Script | Tự động hóa với Apps Script

> **Google Sheets** | Advanced → Automation

---

## What is Apps Script? | Apps Script là gì?

**EN:** Google Apps Script is JavaScript-based automation for Google Workspace — Sheets, Docs, Gmail, Drive, and more.

**VI:** Google Apps Script là tự động hóa dựa trên JavaScript cho Google Workspace — Sheets, Docs, Gmail, Drive và nhiều hơn nữa.

**Access:** Extensions → Apps Script

---

## Basic Examples | Ví dụ cơ bản

### Hello World
```javascript
function helloWorld() {
  SpreadsheetApp.getUi().alert('Xin chào từ Apps Script!');
}
```

### Read and Write Data | Đọc và ghi dữ liệu
```javascript
function processData() {
  const sheet = SpreadsheetApp.getActiveSheet();
  const lastRow = sheet.getLastRow();
  
  for (let i = 2; i <= lastRow; i++) {
    const sales = sheet.getRange(i, 3).getValue();
    const category = sales > 1000000 ? 'High' : 'Normal';
    sheet.getRange(i, 4).setValue(category);
  }
}
```

---

## Custom Function | Hàm tùy chỉnh

```javascript
/**
 * Calculate Vietnamese Personal Income Tax
 * @param {number} income Monthly income in VND
 * @return {number} Tax amount
 * @customfunction
 */
function INCOME_TAX(income) {
  const taxableIncome = income - 11000000;  // Personal deduction
  if (taxableIncome <= 0) return 0;
  if (taxableIncome <= 5000000) return taxableIncome * 0.05;
  if (taxableIncome <= 10000000) return 250000 + (taxableIncome - 5000000) * 0.1;
  return 750000 + (taxableIncome - 10000000) * 0.15;
}
```

**Usage:** `=INCOME_TAX(B2)`

---

## Triggers | Kích hoạt tự động

```javascript
// Run every day at 8 AM
function setupTrigger() {
  ScriptApp.newTrigger('dailyReport')
    .timeBased()
    .everyDays(1)
    .atHour(8)
    .create();
}

function dailyReport() {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Sales');
  // ... generate report
  MailApp.sendEmail('manager@company.com', 'Daily Report', 'See attached');
}
```

---

## Send Email from Sheet | Gửi email từ Sheet

```javascript
function sendAlerts() {
  const sheet = SpreadsheetApp.getActiveSheet();
  const data = sheet.getDataRange().getValues();
  
  data.slice(1).forEach(row => {
    if (row[2] < row[3]) {  // Actual < Target
      MailApp.sendEmail(row[4], 'Cảnh báo KPI', 
        `${row[0]} đang dưới mục tiêu: ${row[2]} / ${row[3]}`);
    }
  });
}
```

---

*← [Excel VBA](excel-vba.md)*
