---
description: >-
  Connect ilert and ThousandEyes and receive critical notifications via SMS,
  push, voice and messenger notifications
---

# Cisco ThousandEyes Integration

[ThousandEyes by Cisco](https://www.thousandeyes.com/) is a network intelligence platform that monitors the performance of internet-based networks and applications, helping businesses quickly detect and troubleshoot connectivity issues. By connecting it to ilert, users can receive real-time alerts on network disruptions, ensuring rapid response and minimal downtime for critical services.

## In ilert: Create a Cisco ThousandEyes alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Cisco ThousandEyes** in the search field, click the Cisco ThousandEyes tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/1 (37).png" alt=""><figcaption></figcaption></figure>

## In Cisco ThousandEyes: Create a Webhook

1. On the sidebar, click on **Integrations**.

<figure><img src="../../.gitbook/assets/2 (33).png" alt=""><figcaption></figcaption></figure>

2. Now click on the **New Integration** button.

<figure><img src="../../.gitbook/assets/3 (30).png" alt=""><figcaption></figcaption></figure>

3. Select **Custom Webhook**.

<figure><img src="../../.gitbook/assets/4 (24).png" alt=""><figcaption></figcaption></figure>

4. Enter a **Name** and the previously generated alert source **URL** into corresponding input fields.
5. Choose **Generic** in the **Preset Configurations** selection and click on **Test**.

<figure><img src="../../.gitbook/assets/5 (19).png" alt=""><figcaption></figcaption></figure>

6. To verify if the webhook is working, check the **Status**; it should show **Connected**.

<figure><img src="../../.gitbook/assets/6 (20).png" alt=""><figcaption></figcaption></figure>

7. Now open the three-dot menu and click on **Manage Alert Rules**.

<figure><img src="../../.gitbook/assets/7 (15).png" alt=""><figcaption></figcaption></figure>

8. Select the desired **Alert Rules** from which you want to receive notifications.
9. Click on **Save** to finish the setup.

<figure><img src="../../.gitbook/assets/8 (10).png" alt="" width="563"><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as Cisco ThousandEyes sends a notification with '1' status, corresponding alerts in ilert will be resolved automatically.
