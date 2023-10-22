---
layout: post
title: "Fetching Google Sheet as JSON with Apps Script and JavaScript"
date: 2023-10-22 12:00:00 +0700
categories: google javascript json
---

Google Apps Script is a powerful tool that allows you to automate tasks and build web applications that integrate with various Google services. In this tutorial, we will create a simple web application that fetches data from a Google Sheet as JSON and displays it in a dropdown menu on a webpage.

## what you need

1. A Google account.
2. A Google Sheet with data to fetch. We'll assume your Google Sheet has columns for 'Name' and 'Email'.

## Step 1: Create Your Google Apps Script

1. Open your Google Sheet.
2. Click on `Extensions` in the top menu and select `Apps Script`.
3. Replace the default `myFunction` code with the following:

```javascript
function doGet(e) {
  return ContentService.createTextOutput(getSheetDataAsJSON());
}

function getSheetDataAsJSON() {
  var spreadsheet = SpreadsheetApp.openById('YOUR_SPREADSHEET_ID'); // Replace with your actual spreadsheet ID
  var sheet = spreadsheet.getSheetByName('SHEET_NAME'); // Replace with the name of your target sheet
  var data = sheet.getDataRange().getValues();
  var jsonData = [];

  for (var i = 1; i < data.length; i++) {
    var row = data[i];
    var obj = {
      "name": row[0], // Assuming the name is in the first column (column A)
      "email": row[1] // Assuming the email is in the second column (column B)
    };
    jsonData.push(obj);
  }

  return JSON.stringify(jsonData);
}
```
Save your script. Click on the floppy disk icon to give your project a name and save it.

4. Click on the clock icon (Triggers) in the left sidebar to set up a trigger. Create a new trigger that runs the doGet function on an "Open" event.

5. Now deploy as new webapp with appropriate permission and don't forget to copy webapp URL since we will need it in the next step

## Step 2: Create HTML page with Javascript

```javascript
<!DOCTYPE html>
<html>
<head>
    <title>Data Dropdown</title>
</head>
<body>
    <select id="dataDropdown" class="form-select" style="width: 300px;"></select>
    <script>
        // Fetch active user data using JavaScript (async)
        function getActiveUser() {
            fetch("YOUR_GOOGLE_WEBAPP_DEPLOYMENT_URL")
                .then(response => response.json())
                .then(data => {
                    const dataDropdown = document.getElementById("dataDropdown");

                    // Populate the dropdown with data
                    data.forEach(item => {
                        const option = document.createElement("option");
                        option.value = item.email;
                        option.text = item.name;
                        dataDropdown.appendChild(option);
                    });
                })
                .catch(error => {
                    console.error("Error fetching data:", error);
                });
        }
        getActiveUser();
    </script>
</body>
</html>

```
