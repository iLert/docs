---
description: >-
  With the ilert Splunk integration, you can create alerts in ilert based on
  Splunk alerts.
---

# Splunk Integration

## In ilert: Create a Splunk alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Splunk** in the search field, click on the Splunk tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Splunk <a href="#in-splunk" id="in-splunk"></a>

### Create a search <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Splunk and then to **Search & Reporting.** Create a search for which you’d like to create an alert.

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_42.png)

2. Click on **Save As** and then on **Alert** to add an alert

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_45.png)

3. On the modal window name the alert e.g. **iLert,** choose **Webhook** in the **When triggered** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** Save\*\*

![](../.gitbook/assets/Screenshot\_08\_02\_21\_\_20\_48.png)

Finished! Your Splunk alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Splunk alerts do not fire resolve events.

**Can I connect Splunk with multiple alert sources from ilert?**

Yes, simply create more action sequences in Splunk.
