# Excel VBA | Tự động hóa với VBA

> **Excel** | Advanced → Automation

---

## What is VBA? | VBA là gì?

**EN:** Visual Basic for Applications (VBA) is Excel's built-in programming language for automating repetitive tasks, creating custom functions, and building interactive tools.

**VI:** Visual Basic for Applications (VBA) là ngôn ngữ lập trình tích hợp của Excel để tự động hóa các tác vụ lặp lại, tạo hàm tùy chỉnh và xây dựng công cụ tương tác.

---

## Getting Started | Bắt đầu

1. Press **Alt+F11** to open the VBA Editor / Nhấn Alt+F11 để mở VBA Editor
2. Insert → Module
3. Write your macro, press **F5** to run

---

## Basic Macro Examples | Ví dụ Macro cơ bản

### Hello World
```vba
Sub HelloWorld()
    MsgBox "Xin chào từ VBA!"
End Sub
```

### Auto-format a table
```vba
Sub FormatSalesTable()
    Dim ws As Worksheet
    Set ws = ThisWorkbook.Sheets("Sales")
    
    With ws.Range("A1:E1")
        .Font.Bold = True
        .Interior.Color = RGB(0, 112, 192)
        .Font.Color = RGB(255, 255, 255)
    End With
    
    ws.Range("A:E").Columns.AutoFit
    MsgBox "Định dạng hoàn tất!"
End Sub
```

### Loop through rows | Vòng lặp qua hàng
```vba
Sub ProcessSales()
    Dim i As Long
    Dim lastRow As Long
    lastRow = Cells(Rows.Count, "A").End(xlUp).Row
    
    For i = 2 To lastRow
        If Cells(i, "C").Value > 1000000 Then
            Cells(i, "D").Value = "High Value"
        Else
            Cells(i, "D").Value = "Normal"
        End If
    Next i
End Sub
```

---

## Custom Function (UDF) | Hàm tùy chỉnh

```vba
Function VAT_CALC(amount As Double, Optional rate As Double = 0.1) As Double
    ' Calculate Vietnamese VAT
    VAT_CALC = amount * rate
End Function
```

**Usage in cell:** `=VAT_CALC(B2, 0.1)`

---

## Event-driven Macros | Macro theo sự kiện

```vba
' Runs every time a cell changes in Sheet1
Private Sub Worksheet_Change(ByVal Target As Range)
    If Not Intersect(Target, Range("B:B")) Is Nothing Then
        Target.Offset(0, 1).Value = Now()  ' Log timestamp
    End If
End Sub
```

---

*[Apps Script →](apps-script.md)*
