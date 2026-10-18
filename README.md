# Bulk Reply Web

`index.html` is a small browser UI for the bulk-reply flow.

## Required Power Automate setup

The current flow still uses **Manually trigger a flow**. To connect this page, create a copy of the flow or replace the trigger with **When an HTTP request is received** and define this JSON schema:

```json
{
  "type": "object",
  "properties": {
    "EmailList": { "type": "string" },
    "Text1": { "type": "string" }
  }
}
```

The page sends `EmailList` and `Text1` as JSON. It automatically splits the email list into batches of 50 and calls the flow sequentially.

Keep the HTTP trigger URL private. Do not publish it in a public website without authentication or a server-side proxy.
