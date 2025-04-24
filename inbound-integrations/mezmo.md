---
description: >-
  Receive Mezmo's alerts via phone calls, push notifications, SMS and other
  channels with the help of ilert
---

# Mezmo Integration

[Mezmo](https://www.mezmo.com/) is a log management and observability platform designed to centralize and analyze application logs in real-time. By integrating Mezmo with ilert, users can benefit from seamless alerting and incident response capabilities based on their log data. This integration allows users to set up automatic alerts within ilert for critical log events detected by Mezmo.

## In ilert: Create a Mezmo alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Mezmo** in the search field, click the Mezmo tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/il-1 (1).png" alt="" width="563"><figcaption></figcaption></figure>

## In Mezmo: Create an alert Webhook

1. On the sidebar, click on the **Cog Wheel** icon.

<figure><img src="../.gitbook/assets/1 (2).png" alt=""><figcaption></figcaption></figure>

2. Now click on **Alerts**.

<figure><img src="../.gitbook/assets/2 (2).png" alt="" width="293"><figcaption></figcaption></figure>

3. Click on **Add Preset**.

<figure><img src="../.gitbook/assets/3 (3).png" alt=""><figcaption></figcaption></figure>

4. Choose **Webhook**.

<figure><img src="../.gitbook/assets/4 (2).png" alt=""><figcaption></figcaption></figure>

5. Enter a name for the webhook.
6. Change the **Method** to 'POST' and enter the alert source url previously generated in ilert into the URL field.

<figure><img src="../.gitbook/assets/5 (1) (2) (1).png" alt=""><figcaption></figcaption></figure>

7. On the sidebar, click on the **Views** icon.

<figure><img src="../.gitbook/assets/6 (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

8. On your desired view, click on **Edit alert**.

<figure><img src="../.gitbook/assets/7 (1) (2).png" alt=""><figcaption></figcaption></figure>

9. Select the newly created webhook and save the alert.

<figure><img src="../.gitbook/assets/8 (1).png" alt=""><figcaption></figcaption></figure>

## FAQ

**Will alerts in ilert be resolved automatically?**

No, unfortunately Mezmo is not compatible with ilert's resolve event.
