---
description: >-
  With the iLert Splunk integration, you can create alerts in iLert based on
  Splunk alerts.
---

# Splunk Integration

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Splunk alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Splunk" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_39.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in Splunk.

![](<../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_39 (1).png>)

## In Splunk <a href="#in-splunk" id="in-splunk"></a>

### Create a search <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Splunk and then to **Search & Reporting.** Create a search for which you’d like to create an alert.

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_42.png)

1. Click on **Save As** and then on **Alert** to add an alert

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_45.png)

1. On the modal window name the alert e.g. **iLert,** choose **Webhook** in the **When triggered** section and **\*\*paste the** Webhook URL **that you generated in iLert and click on** Save\*\*

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_48.png)

Finished! Your Splunk alerts will now create alerts in iLert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

No, unfortunately Splunk alerts do not fire resolve events.

**Can I connect Splunk with multiple alert sources from iLert?**

Yes, simply create more action sequences in Splunk.
