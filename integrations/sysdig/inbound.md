---
description: >-
  The ilert Sysdig Inbound Integration helps you to easily connect ilert with
  Sysdig.
---

# Sysdig Inbound Integration

With the ilert Sysdig integration you can create alerts in ilert based on Sysdig event.

## In ilert: Create a Sysdig alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Sysdig** in the search field, click on the Sysdig tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Sysdig <a href="#in-topdesk" id="in-topdesk"></a>

### Create notification channel <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Sysdig and then to **Settings.** Click on **Notification Channels** and then on **Add Notification Channel** to add a new notification channel for ilert

![](../../.gitbook/assets/Notifications\_-\_Settings\_-\_Sysdig.png)

2. On the popup, choose **WebHook**

![](../../.gitbook/assets/Banners\_and\_Alerts\_and\_Notifications\_-\_Settings\_-\_Sysdig.png)

3. On the next page, in the section **URL** field, paste the **Webhook URL** that you generated in ilert

![](../../.gitbook/assets/New\_Channel\_-\_Notifications\_-\_Settings\_-\_Sysdig.png)

4. In the **Channel Name** section, enter a name eg. `iLert`
5. Make sure that **Enabled** and **Notify when Resolved** options are enabled
6. Click on **Save**

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes

**Will alerts in ilert be accepted automatically?**

No, unfortunately Sysdig accepted event is not compatible with ilert accepted event.

**Can I connect Sysdig with multiple alert sources from ilert?**

Yes, simply create more notification channels in Sysdig.
