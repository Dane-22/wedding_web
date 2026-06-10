# Google Sheets Setup for RSVP Form

This guide will help you set up Google Sheets to collect RSVP form submissions.

## Step 1: Create a Google Sheet

1. Go to [sheets.google.com](https://sheets.google.com)
2. Create a new spreadsheet
3. Name it something like "Wedding RSVP"
4. In the first row, add these headers:
   - A1: Timestamp
   - B1: Full Name
   - C1: Email
   - D1: Contact Number
   - E1: Attendance
   - F1: Message

## Step 2: Add Google Apps Script

1. In your Google Sheet, go to **Extensions > Apps Script**
2. Delete any existing code
3. Paste the following code:

```javascript
function doPost(e) {
  try {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    var data = JSON.parse(e.postData.contents);
    
    sheet.appendRow([
      new Date(),
      data.fullName,
      data.email,
      data.contactNumber,
      data.attendance,
      data.message
    ]);
    
    return ContentService
      .createTextOutput(JSON.stringify({ 'result': 'success' }))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (error) {
    return ContentService
      .createTextOutput(JSON.stringify({ 'result': 'error', 'error': error.toString() }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}

function doGet(e) {
  return ContentService
    .createTextOutput(JSON.stringify({ 'status': 'RSVP form endpoint is active' }))
    .setMimeType(ContentService.MimeType.JSON);
}
```

4. Click the **Save** icon (floppy disk)
5. Name the project (e.g., "RSVP Form Handler")

## Step 3: Deploy as Web App

1. Click **Deploy > New deployment**
2. Click the gear icon ⚙️ next to "Select type"
3. Select **Web app**
4. Fill in the details:
   - **Description**: RSVP Form
   - **Execute as**: Me (your email)
   - **Who has access**: Anyone
5. Click **Deploy**
6. Copy the **Web app URL** (it will look like: `https://script.google.com/macros/s/.../exec`)

## Step 4: Update Your HTML File

1. Open `index.html` in your wedding website
2. Find the line that says:
   ```javascript
   var GOOGLE_SCRIPT_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL_HERE';
   ```
3. Replace it with your actual Web app URL:
   ```javascript
   var GOOGLE_SCRIPT_URL = 'https://script.google.com/macros/s/YOUR_ACTUAL_URL/exec';
   ```

## Step 5: Test Your Form

1. Open your wedding website in a browser
2. Navigate to the RSVP section
3. Fill out the form and submit
4. Check your Google Sheet - you should see the new entry appear

## Important Notes

- **Anyone can access**: Since you set "Who has access" to "Anyone", anyone with the URL can submit data. This is necessary for the form to work without authentication.
- **No hosting required**: The form submits directly to Google's servers, so you don't need any backend hosting.
- **Rate limits**: Google Apps Script has rate limits. For a wedding RSVP, this shouldn't be an issue, but be aware.
- **Data privacy**: The data is stored in your personal Google Drive. Make sure to share the sheet with your partner if needed.

## Troubleshooting

**Form shows "Please configure your Google Apps Script URL"**
- Make sure you replaced the placeholder URL in index.html with your actual Web app URL

**Form shows error when submitting**
- Check that your Web app is deployed as "Anyone" can access
- Verify the URL is correct
- Check the Google Apps Script execution log (Extensions > Apps Script > Executions)

**Data not appearing in Google Sheet**
- Check the Apps Script execution log for errors
- Make sure the sheet has the correct headers in row 1
- Verify the column names in the script match your sheet headers

**CORS errors**
- The script uses `mode: 'no-cors'` to avoid CORS issues
- This means you won't get detailed error responses, but submissions should still work
