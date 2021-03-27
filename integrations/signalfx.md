---
description: >-
  With the iLert SignalFx integration, you can create incidents in iLert based
  on SignalFx alerts.
---

# SignalFx Integration

SignalFx enables real-time cloud monitoring and observability for infrastructure, microservices, and applications by collecting and analyzing metrics and traces across every component in your cloud environment. Built on a massively-scalable streaming architecture, SignalFx applies advanced analytics and data science-directed troubleshooting to let operators find the root cause of issues in seconds.

## In iLert <a id="in-ilert"></a>

### Create a SignalFx alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "SignalFx" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/ilert%20%2831%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in SignalFx.

![](../.gitbook/assets/ilert%20%2832%29.png)

## In SignalFx <a id="in-splunk"></a>

### Create a search <a id="create-action-sequences"></a>

1. Go to SignalFx and then to **Alerts.** Create a detector or edit an existing detector for triggering incidents.

![](../.gitbook/assets/detectors.png)

2. Choose the rule that you would like to apply, then click **Edit.** In the **Alert recipients** section, click **Add Recipient,** select **Webhook -&gt; Custom...**

![](../.gitbook/assets/detector_-_my_detector.png)

3. On the modal window paste the **Webhook URL** that you generated in iLert and click on **Update**

![](../.gitbook/assets/detector_-_my_detector%20%281%29.png)

Finished! Your SignalFx alerts will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an alert with "ok" has been resolved in SignalFx, the associated incident in iLert will be resolved automatically.

**Can I connect SignalFx with multiple alert sources from iLert?**

Yes, simply add more recipients in SignalFx alert rule.

