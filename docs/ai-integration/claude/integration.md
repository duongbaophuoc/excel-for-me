# Claude AI Integration | Tích hợp Claude AI

> **Excel & Google Sheets** | AI Integration → Claude

---

## Overview | Tổng quan

**EN:** Claude (Anthropic) excels at complex reasoning, nuanced multi-condition formulas, and long document analysis.

**VI:** Claude (Anthropic) xuất sắc ở lý luận phức tạp, công thức nhiều điều kiện và phân tích tài liệu dài.

---

## Method 1: Claude.ai Web | Dùng claude.ai

Best for interactive formula building and model review.
Tốt nhất cho xây dựng công thức tương tác và xem xét mô hình.

**Power Prompts | Prompt mạnh:**

```
"You are an Excel expert. I have:
- Sheet 'Sales': Date, SalesRep, Region, Product, Amount
- Sheet 'Targets': SalesRep, MonthlyTarget

Write formulas for 'Dashboard' sheet showing:
1. Each rep YTD actual vs target (% achievement)
2. Top 3 products by revenue this month
3. Region with highest MoM growth"
```

---

## Method 2: Claude API via Apps Script

```javascript
function askClaude(prompt) {
  var apiKey = PropertiesService.getScriptProperties()
                                .getProperty('CLAUDE_KEY');
  var payload = {
    model: 'claude-haiku-4-5-20251001',
    max_tokens: 1024,
    messages: [{role: 'user', content: String(prompt)}]
  };
  var options = {
    method: 'post',
    contentType: 'application/json',
    headers: {
      'x-api-key': apiKey,
      'anthropic-version': '2023-06-01'
    },
    payload: JSON.stringify(payload)
  };
  var res = UrlFetchApp.fetch(
    'https://api.anthropic.com/v1/messages', options);
  var data = JSON.parse(res.getContentText());
  return data.content[0].text;
}

/** @customfunction */
function CLAUDE(prompt) {
  return askClaude(prompt);
}
```

**Usage:** `=CLAUDE("Summarize in 1 sentence: " & A2)`

---

## Method 3: Claude API via Excel VBA

```vba
Function AskClaude(prompt As String) As String
    Dim http As Object
    Dim apiKey As String
    apiKey = Sheets("PARAMS").Range("B2").Value

    Set http = CreateObject("MSXML2.XMLHTTP")
    http.Open "POST", "https://api.anthropic.com/v1/messages", False
    http.setRequestHeader "Content-Type", "application/json"
    http.setRequestHeader "x-api-key", apiKey
    http.setRequestHeader "anthropic-version", "2023-06-01"

    Dim cleanPrompt As String
    cleanPrompt = Replace(prompt, Chr(34), Chr(39))

    Dim body As String
    body = "{" & Chr(34) & "model" & Chr(34) & ":" & Chr(34) & _
           "claude-haiku-4-5-20251001" & Chr(34) & "," & _
           Chr(34) & "max_tokens" & Chr(34) & ":1024," & _
           Chr(34) & "messages" & Chr(34) & ":[{" & _
           Chr(34) & "role" & Chr(34) & ":" & Chr(34) & "user" & Chr(34) & "," & _
           Chr(34) & "content" & Chr(34) & ":" & Chr(34) & cleanPrompt & Chr(34) & "}]}"

    http.send body

    Dim resp As String
    resp = http.responseText
    Dim p1 As Long, p2 As Long
    p1 = InStr(resp, Chr(34) & "text" & Chr(34) & ":") + 8
    p2 = InStr(p1, resp, Chr(34)) - 1
    AskClaude = Mid(resp, p1, p2 - p1 + 1)
End Function
```

---

## Claude vs ChatGPT vs Gemini

| Capability | Claude | ChatGPT | Gemini |
|---|---|---|---|
| Complex multi-condition formulas | ✅ Best | ✅ Excellent | ✅ Good |
| Long data analysis | ✅ 200K context | ✅ 128K | ✅ 1M |
| VBA refactoring | ✅ Very good | ✅ Very good | ✅ Good |
| Native Sheets plugin | ❌ | ⚠️ Add-in | ✅ Built-in |
| Vietnamese language | ✅ Very good | ✅ Excellent | ✅ Good |
| Reasoning clarity | ✅ Best | ✅ Good | ✅ Good |

---

## Best Use Cases for Claude | Trường hợp tốt nhất

1. **Complex multi-condition formulas** — handles ambiguous requirements well
2. **Refactoring messy VBA** — explains what broken code does, then fixes it
3. **Financial model audit** — checks logic errors in DCF / budgeting
4. **Data schema design** — recommends optimal sheet/table structure
5. **Formula documentation** — explains every formula in a sheet for handover

---

*← [AI Integration](../)*
