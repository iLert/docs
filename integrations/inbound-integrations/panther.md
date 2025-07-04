---
description: >-
  Learn how to integrate Panther with ilert to automatically forward security
  alerts and trigger real-time incident notifications via phone, SMS, push, and
  more.
---

# Panther Integration

[Panther](https://panther.com/) is a modern security information and event management (SIEM) platform that helps teams detect, investigate, and respond to threats at cloud scale. With the ilert integration, Panther can automatically send alerts to ilert, enabling real-time incident response through multi-channel notifications and on-call scheduling.

## In ilert: Create a Panther alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Panther** in the search field, click the Panther tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (1) (1).png" alt=""><figcaption></figcaption></figure>

## In Panther: Create an Alert Destination

1. On the sidebar, click on **Configure** -> **Alert Destinations**.

<figure><img src="../../.gitbook/assets/1 (1) (1).png" alt=""><figcaption></figcaption></figure>

2. Now select **Custom Webhook**.

<figure><img src="../../.gitbook/assets/2 (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

3. Enter a **Display Name**.
4. Enter the in ilert previous generated alert source url into the **Custom Webhook URL** field.
5. Click **Add Destination** to finish the setup.

<figure><img src="../../.gitbook/assets/3 (1) (1).png" alt=""><figcaption></figcaption></figure>

6. Optional: Send a test alert.

<figure><img src="../../.gitbook/assets/4 (1) (1).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Panther is not compatible with ilert's resolve event.
