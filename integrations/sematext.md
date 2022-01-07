---
description: >-
  Create iLert alerts from Sematext alerts and get alerted through iLert for
  high priority issues.
---

# Sematext Integration

Sematext Cloud is an all-in-one infrastructure performance and log monitoring, real user, frontend, API, website, and uptime monitoring SaaS.

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Sematext alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_37.png)

1. Enter a name and select your desired escalation policy. Select "Sematext" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_56.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the notification hook in Sematext.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_57.png)

## In Sematext <a href="#in-splunk" id="in-splunk"></a>

### Create a notification hook <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Sematext, then to **Alerts -> Notification Hooks** and then on the **New Notification Hook** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_00.png)

1. On the next page,  click on the **Custom** tile

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_03.png)

1. On the next modal page, name the hook e.g. iLert, paste the **Webhook URL** that you generated in iLert, in the **Send data as** section choose **Json**, in the **HTTP method** section choose **POST**, in the **Parameters** section choose the following payload, then click on the **Save Notification Hook** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_59.png)

```javascript
{
    "backToNormal": "$backToNormal",
    "ruleType": "$ruleType",
    "description": "$description",
    "title": "$title",
    "applicationId": "$applicationId",
    "url": "$url",
    "createTimestamp": "$createTimestamp"
}
```

1. Edit your alert rule to send notification to iLert

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_08.png)

Finished! Your Sematext alerts will now create alerts in iLert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an alert has been completed in Sematext, the associated alert in iLert will be resolved automatically.

**Can I connect Sematext with multiple alert sources from iLert?**

Yes, simply add more notification hooks in Sematext.
