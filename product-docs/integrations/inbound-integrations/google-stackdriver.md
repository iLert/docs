---
description: >-
  With the ilert Google Cloud Monitoring integration, you can create alerts in
  ilert based on Google Cloud Alerts.
---

# Google Cloud Monitoring (formerly Stackdriver) Integration

With [Google Cloud Monitoring](https://cloud.google.com/monitoring) you can gain visibility into the performance, availability, and health of your applications and infrastructure.

## In ilert: Create a Google Cloud Monitoring alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Google Cloud Monitoring** in the search field, click on the Google Cloud Monitoring tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Google Cloud Console: Create Webhook Notification Channel <a href="#create-webhook-notification" id="create-webhook-notification"></a>

1. Go to Google Cloud Console and search for Monitoring

![](../../.gitbook/assets/Screenshot_27_09_21__17_12.png)

2. On the Monitoring page go to **Alerting** and click on the **Edit Notification channels** button

![](../../.gitbook/assets/Screenshot_27_09_21__17_15.png)

3. On the Notification Channels page click on the **Add New** button beside the Webhooks channels.

![](../../.gitbook/assets/Screenshot_27_09_21__17_17.png)

4. Assign a **Display Name** on the following modal (e.g. ilert) and in the field "Endpoint URL" paste the **Webhook URL** that you generated in ilert and click on the **Save** button.

![](../../.gitbook/assets/Screenshot_27_09_21__17_21.png)

5. After you've created the ilert webhook, you can use it as a notification in any Alerting Policy in Google Cloud Monitoring. The following screenshot will create a new Alerting Policy with ilert as the notification method.

![](../../.gitbook/assets/Screenshot_27_09_21__17_25.png)

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the state of an alert in Google Cloud Monitoring is `RESOLVED`, the associated alert in ilert is resolved.

**Can I link Google Cloud Monitoring to multiple alert sources in ilert?**

Yes, create a webhook for each alert source in Google Cloud Monitoring. You can then choose which Webhook to use for alerting for each Alerting Policy in Google Cloud.
