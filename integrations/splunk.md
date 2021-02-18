---
description: >-
  With the iLert Splunk integration, you can create incidents in iLert based on
  Splunk alerts.
---

# Splunk Integration

## In iLert <a id="in-ilert"></a>

### Create a Splunk alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Splunk" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/screenshot_08_02_21__20_39.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in Splunk.

![](../.gitbook/assets/screenshot_08_02_21__20_39%20%281%29.png)

## In Splunk <a id="in-splunk"></a>

### Create a search <a id="create-action-sequences"></a>

1. Go to Splunk and then to **Search & Reporting.** Create a search for which you’d like to create an alert.

![](../.gitbook/assets/screenshot_08_02_21__20_42.png)

2. Click on **Save As** and then on **Alert** to add an alert

![](../.gitbook/assets/screenshot_08_02_21__20_45.png)

3. On the modal window name the alert e.g. **iLert,** choose **Webhook** in the **When triggered** section and ****paste the **Webhook URL** that you generated in iLert and click on **Save**

![](../.gitbook/assets/screenshot_08_02_21__20_48.png)

Finished! Your Splunk alerts will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

No, unfortunately Splunk alerts do not fire resolve events.

**Can I connect Splunk with multiple alert sources from iLert?**

Yes, simply create more action sequences in Splunk.

