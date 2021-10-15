---
description: >-
  With the iLert Google Cloud Monitoring integration, you can create alerts in
  iLert based on Google Cloud Alerts.
---

# Google Cloud Monitoring (formerly Stackdriver) Integration

With [Google Cloud Monitoring](https://cloud.google.com/monitoring) you can gain visibility into the performance, availability, and health of your applications and infrastructure.

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create a Google Cloud Monitoring alert source

1. Switch to the tab "alert sources" and click on the button "Create new alert source"
2. Assign name and select escalation chain
3. Select and save in the Google Cloud Monitoring Integration Type field.

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_08.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Motification Channel in Google Cloud Console.

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_10.png)

## In Google Cloud Console <a href="create-webhook-notification" id="create-webhook-notification"></a>

### Create Webhook Notification Channel

1. Go to Google Cloud Console and search for Monitoring

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_12.png)

1. On the Monitoring page go to **Alerting** and click on the **Edit Notification channels** button

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_15.png)

1. On the Notification Channels page click on the **Add New** button beside the Webhooks channels.

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_17.png)

1. Assign a **Display Name** on the following modal (e.g. iLert) and in the field "Endpoint URL" paste the **Webhook URL** that you generated in iLert and click on the **Save** button.

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_21.png)

1. After you've created the iLert webhook, you can use it as a notification in any Alerting Policy in Google Cloud Monitoring. The following screenshot will create a new Alerting Policy with iLert as the notification method.

![](../.gitbook/assets/Screenshot\_27\_09\_21\__17\_25.png)

## FAQ <a href="faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as the state of an alert in Google Cloud Monitoring is `RESOLVED`, the associated alert in iLert is resolved.

**Can I link Google Cloud Monitoring to multiple alert sources in iLert?**

Yes, create a webhook for each alert source in Google Cloud Monitoring. You can then choose which Webhook to use for alerting for each Alerting Policy in Google Cloud.
