' Tác vụ: Tự động lưu Sheet hiện tại thành file PDF riêng biệt
Sub SaveAsPDF()
    Dim ws As Worksheet
    Set ws = ActiveSheet
    ws.ExportAsFixedFormat Type:=xlTypePDF, _
        Filename:="C:\Reports\" & ws.Name & ".pdf"
End Sub
-------------
# Excel VBA

Sub Hello()
 MsgBox "Hello"
End Sub

💡 Automation in Excel