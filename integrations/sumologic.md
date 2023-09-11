---
description: >-
  Create ilert alerts from Sumo Logic monitoring and get alerted through ilert
  for high-priority issues.
---

# Sumo Logic Integration

## In ilert: Create a Sumo Logic alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Sumo Logic** in the search field, click on the Sumo Logic tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Sumo Logic <a href="#in-splunk" id="in-splunk"></a>

### Create a notification setting <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Sumo Logic, then to **Manage Data -> Monitoring**, click on the **Connections** tab and then on the **Add (+)** button

<figure><img src="../.gitbook/assets/Sumo logic connect.png" alt=""><figcaption></figcaption></figure>

2. On the next page, click on the **Webhook** tile

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_44.png)

3. On the next page, name the connection e.g. ilert, paste the **Webhook URL** that you generated in ilert, in the **Payload** section following payload object, then click on the **Save** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_47.png)

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

Finished! Your Sumo Logic alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately, Sumo Logic's notification is not compatible with ilert's resolve event.

**Can I connect Sumo Logic with multiple alert sources from ilert?**

Yes, simply add more connections in Sumo Logic.
