---
description: Create alerts in ilert from Checkly checks
---

# Checkly Integration

## In ilert: Create a Checkly alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Checkly** in the search field, click on the Checkly tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Checkly: Add an ilert alerting channel

1.  Go to **Alerts** and click on **Add more channels**.\


    <figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 17.59.20.png" alt=""><figcaption></figcaption></figure>
2.  Browse to ilert in the list of channels and click on **Add channel**\


    <figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 18.00.43.png" alt=""><figcaption></figcaption></figure>
3.  Give the alert channel a name (e.g. ilert) and paste the **Checkly URL** from above in the URL field. Optionally change the notification events. Recovery notifications will resolve existing alerts in ilert that were created from checkly. **Do not edit the payload**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-06-01 at 18.05.49.png" alt=""><figcaption></figcaption></figure>
4. Click **Save ilert webhook**.

## FAQ <a href="#faq" id="faq"></a>

#### **Will alerts in ilert be resolved automatically?**

Yes, as soon as a check in checkly recovers, the associated alert in ilert will be resolved automatically. Make sure that the option **Send alert notifications when a check recovers** is enabled in the alert channel settings in Checkly.&#x20;

#### **Can I link Checkly to multiple alert sources in ilert?**

Yes, create an **alert channel** per alert source in Checkly.

#### **Can I also receive SSL certificate expiration alerts in ilert**

Yes. Simply enable the **Send alert notifications when an SSL certificate is due to expire in x days** in the alert channel settings in Checkly.

