# Bulk Reply Web

`index.html` is a small browser UI for the bulk-reply flow.

## Required Power Automate setup

Use the **When an HTTP request is received** trigger with this JSON schema:

```json
{
  "type": "object",
  "properties": {
    "EmailList": { "type": "string" },
    "Text1": { "type": "string" }
  }
}
```

The page sends `EmailList` and `Text1` as JSON. It automatically splits the email list into batches of 50 and calls the flow sequentially. Add a **Response** action after `Apply to each` with status code `200` and body `{"status":"completed"}` so the page can show when the batch has actually finished.

The page includes two message templates and shows product URLs as plain text instead of HTML hyperlinks.

Keep the HTTP trigger URL private. Do not publish it in a public website without authentication or a server-side proxy.
