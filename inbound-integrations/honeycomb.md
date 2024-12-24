---
description: >-
  The ilert Honeycomb Integration helps you to easily connect ilert with
  Honeycomb.
---

# Honeycomb Integration

[Honeycomb](https://www.honeycomb.io/) is a tool for observability, designed to help developers understand and debug their software systems by providing real-time insights and detailed, queryable data about production environments.

## In ilert: Create a Honeycomb alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Honeycomb** in the search field, click the Honeycomb tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Honeycomb: Create a Webhook Trigger

1. On the sidebar click on **Account -> Team settings**.

<figure><img src="../.gitbook/assets/1 (7).png" alt="" width="188"><figcaption></figcaption></figure>

2. On the next page click on **Integrations**.

<figure><img src="../.gitbook/assets/2 (6).png" alt="" width="563"><figcaption></figcaption></figure>

3. Now scroll down and click on **Add Integration**.

<figure><img src="../.gitbook/assets/3 (5).png" alt="" width="563"><figcaption></figcaption></figure>

4. In the popup window: Change the **Provider** to Webhook and choose a desired **Name**. Now insert the ilert Honeycomb URL and api key from [the previous created alert source](honeycomb.md#in-ilert-create-a-honeycomb-alert-source) into **Webhook URL** and **Shared Secret**.
5. Click on **Add** to save the integration.

<figure><img src="../.gitbook/assets/4 (5).png" alt="" width="563"><figcaption></figcaption></figure>

6. Optionally: On the Trigger and SLO Recipients section, click on **Test**, to send a test webhook to ilert.

<figure><img src="../.gitbook/assets/5 (5).png" alt="" width="563"><figcaption></figcaption></figure>

7. Now on the sidebar, click on **Triggers**.

<figure><img src="../.gitbook/assets/6 (6).png" alt="" width="85"><figcaption></figcaption></figure>

8. Select a desired trigger template. (This documentation uses Latency)

<figure><img src="../.gitbook/assets/7 (4).png" alt="" width="563"><figcaption></figcaption></figure>

9. Select a dataset and click on **Next**.

<figure><img src="../.gitbook/assets/8 (3).png" alt="" width="563"><figcaption></figcaption></figure>

10. After configuring the trigger, scroll down to the **Recipients** section and click on **Add Recipient**.

<figure><img src="../.gitbook/assets/9 (3).png" alt="" width="563"><figcaption></figcaption></figure>

11. Select the previously created webhook as **Recipient** and click on **Add**.
12. Save the trigger.

<figure><img src="../.gitbook/assets/10 (2).png" alt="" width="563"><figcaption></figcaption></figure>

13. Optionally: In the triggers list click on the **Test** button to send a test webhook to ilert.

<figure><img src="../.gitbook/assets/11 (2).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/12 (1).png" alt="" width="563"><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as Honeycomb sends a notification with 'OK' status, corresponding alerts in ilert will be resolved automatically.
