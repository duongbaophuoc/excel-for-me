# AI-Powered Custom Functions | Hàm Tùy chỉnh bằng AI

> **Excel & Google Sheets** | AI Integration → ChatGPT

---

## Apps Script: Call ChatGPT API | Apps Script gọi API ChatGPT

```javascript
function askChatGPT(prompt) {
  var apiKey = PropertiesService.getScriptProperties()
                                .getProperty('OPENAI_KEY');
  var payload = {
    model: 'gpt-4o-mini',
    messages: [{role: 'user', content: String(prompt)}],
    max_tokens: 500
  };
  var options = {
    method: 'post',
    contentType: 'application/json',
    headers: {Authorization: 'Bearer ' + apiKey},
    payload: JSON.stringify(payload)
  };
  var res = UrlFetchApp.fetch(
    'https://api.openai.com/v1/chat/completions', options);
  var data = JSON.parse(res.getContentText());
  return data.choices[0].message.content;
}

/** @customfunction */
function AI_ASK(prompt) {
  return askChatGPT(prompt);
}
```

**Usage in Sheets:**
```
=AI_ASK("Sentiment (Positive/Negative/Neutral): " & A2)
=AI_ASK("Translate to Vietnamese: " & B2)
=AI_ASK("Extract company name from: " & C2)
```

---

## Practical AI Formula Recipes | Công thức AI thực tế

| Task | Formula |
|---|---|
| Sentiment | `=AI_ASK("Positive/Negative/Neutral: "&A2)` |
| Category tag | `=AI_ASK("Tag as Sales/Support/Billing: "&A2)` |
| Name extract | `=AI_ASK("Extract person name: "&A2)` |
| Language detect | `=AI_ASK("Language of this text (one word): "&A2)` |
| Phone validate | `=AI_ASK("Valid VN phone? "&A2&" Yes/No")` |

---

## Cost Control | Kiểm soát Chi phí

- Use `gpt-4o-mini` — 10x cheaper than GPT-4 for simple tasks
- Set `max_tokens` to minimum needed
- Cache results: `=IF(B2<>"", B2, AI_ASK(A2))`

---

*← [Use Cases](use-cases.md)*
