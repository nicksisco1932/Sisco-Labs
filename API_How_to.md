# 📊 Google Sheets API Logger via Google Apps Script + PowerShell

This project demonstrates how to send data from PowerShell to a Google Sheet using **Google Apps Script** as a custom API endpoint.

---

## ✅ Use Case

Log structured data (like fitness, nutrition, or any other loggable values) into a Google Sheet via an HTTP POST request.

---

## 🧱 Tools Used

- Google Sheets
- Google Apps Script (deployed as a Web App)
- PowerShell (for sending HTTP requests)

---

## 📋 Step-by-Step Setup

### 1. **Create Your Google Sheet**

1. Go to [Google Sheets](https://sheets.google.com).
2. Create a new sheet and name it something like `Fitness Test`.
3. Rename the first tab (bottom-left) to: `Sheet1`
4. Add headers:
    ```plaintext
    A1: Date | B1: Workout | C1: Calories
    ```

---

### 2. **Write the Apps Script**

1. Go to [Google Apps Script](https://script.google.com).
2. Create a new project.
3. Paste this code in `Code.gs` (or `First.gs`):

```javascript
function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Sheet1");
    Logger.log(e.postData.contents);  // for debugging

    const body = JSON.parse(e.postData.contents);
    const { date, workout, calories } = body;

    sheet.appendRow([date, workout, calories]);

    return ContentService
      .createTextOutput(JSON.stringify({ status: "success", row: [date, workout, calories] }))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (error) {
    Logger.log(error);
    return ContentService
      .createTextOutput(JSON.stringify({ status: "error", message: error.message }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
