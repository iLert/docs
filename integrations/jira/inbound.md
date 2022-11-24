---
description: >-
  Create ilert alerts from JIRA issues and get alerted through ilert for high
  priority issues.
---

# Jira Inbound Integration

With the ilert Jira integration you can create alerts in ilert based on Jira issues.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Jira alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Jira" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/iLert (12).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Webhook in Jira.

![](<../../.gitbook/assets/iLert (13).png>)

## In Jira <a href="#in-topdesk" id="in-topdesk"></a>

### Create webhook <a href="#create-action-sequences" id="create-action-sequences"></a>

{% hint style="info" %}
You need admin permissions to manage Jira webhooks.
{% endhint %}

1. Go to Jira and then to **System** **Settings:**

![](../../.gitbook/assets/Projects\_-\_Jira.png)

1. Click on the **WebHooks** and then on the **Create a WebHook** button to add a new webhook for ilert

![](../../.gitbook/assets/WebHooks\_-\_Jira.png)

1. On the next page,  in the section **Name** field, enter a name (e.g. ilert). In the section **URL** field, paste the **Webhook URL** that you generated in ilert. In the section **Issue** choose **created**, **updated** and **deleted** events.

![](<../../.gitbook/assets/WebHooks\_-\_Jira (1).png>)

1. Scroll down and make sure that the request body is **not excluded**

![](../../.gitbook/assets/Screenshot\_23\_09\_21\_\_13\_18.png)

1. Scroll to bottom and click on the **Create** button

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes

**Will alerts in ilert be accepted automatically?**

No, unfortunately Jira events are not compatible with ilert accepted event.

**Can I connect Jira with multiple alert sources from ilert?**

Yes, simply create more webhooks in Jira.
