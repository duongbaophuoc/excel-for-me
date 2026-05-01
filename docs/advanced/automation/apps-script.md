// Tác vụ: Tự động gửi Email nhắc nợ khi cột "Trạng thái" là "Quá hạn"
function sendReminderEmails() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Công nợ");
  var data = sheet.getDataRange().getValues();
  
  data.forEach(function(row) {
    if (row[3] == "Quá hạn") { // Cột D
      MailApp.sendEmail(row[1], "Nhắc thanh toán", "Bạn có khoản nợ chưa thanh toán...");
    }
  });
}
------------
# Apps Script

function test(){
 Logger.log("Hello");
}

💡 Automation in Sheets