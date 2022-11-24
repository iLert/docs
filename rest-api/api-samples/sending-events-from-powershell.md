# Sending events from PowerShell

The code below creates a new alert event in ilert, which might \(depending on your alert sources configuration\) create an alert.

```text
$headers = New-Object "System.Collections.Generic.Dictionary[[String],[String]]"
$headers.Add("content-type", "application/json")

$body = "{`n  `"apiKey`": `".....YOUR SOURCE API KEY....`",`n  `"eventType`": `"ALERT`",`n  `"summary`": `"string`",`n  `"details`": `"string`",`n  `"incidentKey`": `"string`",`n  `"priority`": `"HIGH`",`n  `"images`": [`n    {`n      `"src`": `"string`",`n      `"href`": `"string`",`n      `"alt`": `"string`"`n    }`n  ],`n  `"links`": [`n    {`n      `"href`": `"string`",`n      `"text`": `"string`"`n    }`n  ],`n  `"customDetails`": {}`n}"

$response = Invoke-RestMethod 'https://api.ilert.com/api/v1/events ' -Method 'POST' -Headers $headers -Body $body
$response | ConvertTo-Json
```

