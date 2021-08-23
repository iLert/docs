---
description: >-
  The iLert Sensu Integration helps you to create incidents into your channels
  or resolve incidents.
---

# Sensu Integration

[Sensu](https://sensu.io/) is a tool that functions as an observability Pipeline that delivers monitoring as code on any cloud.

## In iLert

1. Go to the "Alert sources" tab and click "Create new alert source"

2. Enter a name and select your desired escalation policy. Select "Sensu" as the **Integration Type** and click **Save**.

3. On the next page, a API key is generated. You will need the API Key when setting up the handler in Sensu.

## In Sensu

1. Add Sensu iLert Handler

```text
sensuctl asset add ilert/sensu-ilert
```

2. Make sure that the asset was added to your Sensu backend. Run:

```text
sensuctl asset info ilert/sensu-ilert
```

3. In the following command, replace &lt;ilert\_key&gt; with your iLert API key. Then run the updated command:

```text
sensuctl handler create sensu \
--type pipe \
--filters is_incident \
--runtime-assets ilert/sensu-ilert \
--command "sensu-ilert-handler -t <ilert_key>"
```

4. Make sure that your handler was added by retrieving the complete handler definition in YAML or JSON format:

```text
sensuctl handler info ilert --format yaml
```

5. Trigger an event. You can try with **file\_exists** check and iLert handler workflow in place, you can remove a file to cause Sensu to send a non-OK event.

