---
description: >-
  The iLert Sysdig Inbound Integration helps you to easily connect iLert with
  Sysdig.
---

# Sysdig Inbound Integration

With the iLert Sysdig integration you can create incidents in iLert based on Sysdig event.

## In iLert <a id="in-ilert"></a>

### Create a Sysdig alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Sysdig" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%282%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Webhook in Sysdig.

![](../../.gitbook/assets/ilert%20%285%29.png)

## In Sysdig <a id="in-topdesk"></a>

### Create notification channel <a id="create-action-sequences"></a>

1. Go to Sysdig and then to **Settings.** Click on **Notification Channels** and then on **Add Notification Channel** to add a new notification channel for iLert

![](../../.gitbook/assets/notifications_-_settings_-_sysdig.png)

2. On the popup, choose **WebHook**

![](../../.gitbook/assets/banners_and_alerts_and_notifications_-_settings_-_sysdig.png)

3. On the next page, in the section **URL** field, paste the **Webhook URL** that you generated in iLert

![](../../.gitbook/assets/new_channel_-_notifications_-_settings_-_sysdig.png)

4. In the **Channel Name** section, enter a name eg. `iLert`

5. Make sure that **Enabled** and **Notify when Resolved** options are enabled

12. Click on **Save**

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes

**Will incidents in iLert be accepted automatically?**

No, unfortunately Sysdig accepted event is not compatible with iLert accepted event.

**Can I connect Sysdig with multiple alert sources from iLert?**

Yes, simply create more notification channels in Sysdig.

