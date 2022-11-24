---
description: >-
  The ilert Sysdig Inbound Integration helps you to easily connect ilert with
  Sysdig.
---

# Sysdig Inbound Integration

With the ilert Sysdig integration you can create alerts in ilert based on Sysdig event.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Sysdig alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Sysdig" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/iLert (3).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Webhook in Sysdig.

![](<../../.gitbook/assets/iLert (4).png>)

## In Sysdig <a href="#in-topdesk" id="in-topdesk"></a>

### Create notification channel <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Sysdig and then to **Settings.** Click on **Notification Channels** and then on **Add Notification Channel** to add a new notification channel for ilert

![](../../.gitbook/assets/Notifications\_-\_Settings\_-\_Sysdig.png)

1. On the popup, choose **WebHook**

![](../../.gitbook/assets/Banners\_and\_Alerts\_and\_Notifications\_-\_Settings\_-\_Sysdig.png)

1. On the next page, in the section **URL** field, paste the **Webhook URL** that you generated in ilert

![](../../.gitbook/assets/New\_Channel\_-\_Notifications\_-\_Settings\_-\_Sysdig.png)

1. In the **Channel Name** section, enter a name eg. `iLert`
2. Make sure that **Enabled** and **Notify when Resolved** options are enabled
3. Click on **Save**

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes

**Will alerts in ilert be accepted automatically?**

No, unfortunately Sysdig accepted event is not compatible with ilert accepted event.

**Can I connect Sysdig with multiple alert sources from ilert?**

Yes, simply create more notification channels in Sysdig.
