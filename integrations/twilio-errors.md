---
description: Create alerts in ilert from Twilio Errors
---

# Twilio Errors Integration

## In ilert: Create a Twilio Errors alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Twilio Errors** in the search field, click on the Twilio Errors tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Twilio: Add ilert Webhook

1. Navigate to **Monitor -> Logs -> Errors -> Webhook** and enter the [previous](twilio-errors.md#in-ilert-create-twilio-errors-alert-source) generated URL into the **Webhook URL** field.

<figure><img src="../.gitbook/assets/3 (1).png" alt=""><figcaption></figcaption></figure>

2. Click on **Save** to finish the Setup

## FAQ

**Will alerts in ilert be resolved automatically?**

No, unfortunately Twilio Errors is not compatible with ilert's resolve event.
