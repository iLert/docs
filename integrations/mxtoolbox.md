---
description: >-
  Create ilert alerts from MXToolBox alerts and get alerted through ilert for
  high priority issues.
---

# MXToolBox Integration

MxToolbox supports global Internet operations by providing free, fast and accurate network diagnostic and lookup tools. Millions of technology professionals use MxToolbox to help diagnose and resolve a wide range of infrastructure issues.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a MXToolBox alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_37.png)

1. Enter a name and select your desired escalation policy. Select "MXToolBox" as the **Integration Type** and click on **Save**.

![](<../.gitbook/assets/iLert (36).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the notification callback in MXToolBox.

![](<../.gitbook/assets/iLert (37).png>)

## In MXToolBox <a href="#in-splunk" id="in-splunk"></a>

### Create a notification hook <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to MXToolBox, then to **Notifications** and then create a new Notification policy or change the Default notifications policy

![](../.gitbook/assets/Mozilla\_Firefox.png)

1. On the next page,  click on the **Custom** tile

![](<../.gitbook/assets/Mozilla\_Firefox (1).png>)

1. Open the notification policy, in the **Callback** section paste the **Webhook URL** that you generated in ilert, in the **Format** section choose **Default.** Make sure that the **Webhook URL** was **\*\*saved and the** payload **matches the following format: \*\***

```javascript
{
    "Command": "{Command}",
    "Argument": "{Argument}",
    "Name": "{Name}",
    "TransitionId": {TransitionId},
    "AlertType": "{AlertType}",
    "AlertTime": "{AlertTime}",
    "PolicyName": "{PolicyName}",
    "StatusChange": "{StatusChange}",
    "UrlDetails": "{UrlDetails}"
}
```

Finished! Your MXToolBox alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert has been completed in MXToolBox, the associated alert in ilert will be resolved automatically.

**Can I connect MXToolBox with multiple alert sources from ilert?**

Yes, simply add more notification policies in MXToolBox.
