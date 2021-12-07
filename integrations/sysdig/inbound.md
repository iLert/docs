---
description: >-
  The iLert Sysdig Inbound Integration helps you to easily connect iLert with
  Sysdig.
---

# Sysdig Inbound Integration

With the iLert Sysdig integration you can create alerts in iLert based on Sysdig event.

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Sysdig alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Sysdig" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/ilert (2).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Webhook in Sysdig.

![](<../../.gitbook/assets/ilert (5).png>)

## In Sysdig <a href="#in-topdesk" id="in-topdesk"></a>

### Create notification channel <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Sysdig and then to **Settings.** Click on **Notification Channels** and then on **Add Notification Channel** to add a new notification channel for iLert

![](../../.gitbook/assets/notifications\_-\_settings\_-\_sysdig.png)

1. On the popup, choose **WebHook**

![](../../.gitbook/assets/banners\_and\_alerts\_and\_notifications\_-\_settings\_-\_sysdig.png)

1. On the next page, in the section **URL** field, paste the **Webhook URL** that you generated in iLert

![](../../.gitbook/assets/new\_channel\_-\_notifications\_-\_settings\_-\_sysdig.png)

1. In the **Channel Name** section, enter a name eg. `iLert`
2. Make sure that **Enabled** and **Notify when Resolved** options are enabled
3. Click on **Save**

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes

**Will alerts in iLert be accepted automatically?**

No, unfortunately Sysdig accepted event is not compatible with iLert accepted event.

**Can I connect Sysdig with multiple alert sources from iLert?**

Yes, simply create more notification channels in Sysdig.
