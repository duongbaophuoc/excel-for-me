# Gemini Integration | Tích hợp Google Gemini

> **Google Sheets** | AI Integration → Gemini

---

## Method 1: Gemini Side Panel (Built-in) | Bảng bên Tích hợp

**EN:** Click the Gemini icon (✨) in the top-right of Google Sheets.
**VI:** Nhấp vào biểu tượng Gemini (✨) ở góc trên phải Google Sheets.

**What you can say | Có thể nói:**
- "Summarize the data in this sheet"
- "Create a chart showing monthly revenue trend"
- "Write a formula to calculate cumulative sales"
- "Identify any anomalies in column C"

---

## Method 2: Gemini API via Apps Script | API qua Apps Script

```javascript
function askGemini(prompt) {
  var apiKey = PropertiesService.getScriptProperties()
                                .getProperty('GEMINI_KEY');
  var url = 'https://generativelanguage.googleapis.com/v1beta/models/'
          + 'gemini-1.5-flash:generateContent?key=' + apiKey;

  var payload = {
    contents: [{parts: [{text: String(prompt)}]}]
  };
  var options = {
    method: 'post',
    contentType: 'application/json',
    payload: JSON.stringify(payload)
  };
  var res = UrlFetchApp.fetch(url, options);
  var data = JSON.parse(res.getContentText());
  return data.candidates[0].content.parts[0].text;
}

/** @customfunction */
function GEMINI(prompt) {
  return askGemini(prompt);
}
```

**Usage:** `=GEMINI("Classify feedback as Bug/Feature/Question: " & A2)`

---

## Gemini vs ChatGPT vs Claude for Sheets

| Feature | Gemini | ChatGPT | Claude |
|---|---|---|---|
| Native Sheets integration | ✅ Built-in | ⚠️ Add-in | ❌ |
| Google Drive access | ✅ Yes | ❌ No | ❌ |
| Free tier | ✅ Flash free | ⚠️ Limited | ⚠️ Limited |
| Formula quality | ✅ Very good | ✅ Excellent | ✅ Excellent |
| Vietnamese support | ✅ Good | ✅ Excellent | ✅ Very good |
| Long context | ✅ 1M tokens | ✅ 128K | ✅ 200K |

---

## Power Prompt Examples | Ví dụ Prompt mạnh

```
"Write a Google Sheets QUERY formula to show rows where
region='South' and amount>5000000, sorted by date descending."

"I have sales data in A1:E50. Which 5 customers have highest
lifetime value? Return a table with Name, LTV, Last Purchase Date."
```

---

*← [AI Integration](../)*
