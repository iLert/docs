---
description: >-
  Create iLert alerts from JIRA issues and get alerted through iLert for high
  priority issues.
---

# Jira Inbound Integration

With the iLert Jira integration you can create alerts in iLert based on Jira issues.

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Jira alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Jira" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/ilert (12).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Webhook in Jira.

![](<../../.gitbook/assets/ilert (13).png>)

## In Jira <a href="#in-topdesk" id="in-topdesk"></a>

### Create webhook <a href="#create-action-sequences" id="create-action-sequences"></a>

{% hint style="info" %}
You need admin permissions to manage Jira webhooks.
{% endhint %}

1. Go to Jira and then to **System** **Settings:**

![](../../.gitbook/assets/projects\_-\_jira.png)

1. Click on the **WebHooks** and then on the **Create a WebHook** button to add a new webhook for iLert

![](../../.gitbook/assets/webhooks\_-\_jira.png)

1. On the next page,  in the section **Name** field, enter a name (e.g. iLert). In the section **URL** field, paste the **Webhook URL** that you generated in iLert. In the section **Issue** choose **created**, **updated** and **deleted** events.

![](<../../.gitbook/assets/webhooks\_-\_jira (1).png>)

1. Scroll down and make sure that the request body is **not excluded**

![](../../.gitbook/assets/screenshot\_23\_09\_21\_\_13\_18.png)

1. Scroll to bottom and click on the **Create** button

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes

**Will alerts in iLert be accepted automatically?**

No, unfortunately Jira events are not compatible with iLert accepted event.

**Can I connect Jira with multiple alert sources from iLert?**

Yes, simply create more webhooks in Jira.
