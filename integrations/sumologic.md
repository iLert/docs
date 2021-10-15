---
description: >-
  Create iLert alerts from Sumologic alerts and get alerted through iLert for
  high priority issues.
---

# Sumologic Integration

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create a Sumologic alert source <a href="create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/Screenshot\_16\_03\_21\__16\_37.png)

1. Enter a name and select your desired escalation policy. Select "Sumologic" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/Screenshot\_16\_03\_21\__16\_38.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the connection in Sumologic.

![](../.gitbook/assets/Screenshot\_16\_03\_21\__16\_39.png)

## In Sumologic <a href="in-splunk" id="in-splunk"></a>

### Create a notification setting <a href="create-action-sequences" id="create-action-sequences"></a>

1. Go to Sumologic, then to **Manage Data -> Alerts**, click on the **Connections** tab and then on the **Add (+)** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\__16\_42.png)

1. On the next page,  click on the **Webhook** tile

![](../.gitbook/assets/Screenshot\_16\_03\_21\__16\_44.png)

1. On the next page, name the connection e.g. iLert, paste the **Webhook URL** that you generated in iLert, in the **Payload** section following payload object, then click on the **Save** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\__16\_47.png)

```javascript
{
  "Name": "{{Name}}",
  "Description": "{{Description}}",
  "MonitorType": "{{MonitorType}}",
  "Query": "{{Query}}",
  "QueryURL": "{{QueryURL}}",
  "ResultsJson": "{{ResultsJson}}",
  "NumQueryResults": "{{NumQueryResults}}",
  "Id": "{{Id}}",
  "DetectionMethod": "{{DetectionMethod}}",
  "TriggerType": "{{TriggerType}}",
  "TriggerTimeRange": "{{TriggerTimeRange}}",
  "TriggerTime": "{{TriggerTime}}",
  "TriggerCondition": "{{TriggerCondition}}",
  "TriggerValue": "{{TriggerValue}}",
  "TriggerTimeStart": "{{TriggerTimeStart}}",
  "TriggerTimeEnd": "{{TriggerTimeEnd}}",
  "SourceURL": "{{SourceURL}}",
  "SearchName": "{{SearchName}}"
}
```

Finished! Your Sumologic alerts will now create alerts in iLert.

## FAQ <a href="faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

No, unfortunately Sumologic's notification is not compatible with iLert's resolve event.

**Can I connect Sumologic with multiple alert sources from iLert?**

Yes, simply add more connections in Sumologic.
