---
description: Create alerts in ilert from Uptime Kuma notifications
---

# Uptime Kuma Integration

## In ilert: Create Uptime Kuma alert source

1. Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

<figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>

2. Search for **Uptime Kuma** in the search field, click on the Uptime Kuma tile and click on **Next**.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>

3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Uptime Kuma: Add ilert Webhook

1. Select any monitor you want to send notifications from.

<figure><img src="../.gitbook/assets/3 (2).png" alt=""><figcaption></figcaption></figure>

2. Click on **Edit**

<figure><img src="../.gitbook/assets/4 (2).png" alt=""><figcaption></figcaption></figure>

3. Now click on **Setup Notification**

<figure><img src="../.gitbook/assets/5 (2).png" alt=""><figcaption></figcaption></figure>

4. Choose **Webhook** in the Notification Type field
5. Add a **Friendly Name** for your the notification
6. In Post URL add the [previous](uptime-kuma.md#in-ilert-create-uptime-kuma-alert-source) created **Uptime Kuma URL**
7. Choose **application/json** as Content Type

<figure><img src="../.gitbook/assets/6 (3).png" alt="" width="375"><figcaption></figcaption></figure>

8. Optional: click on **Test** to test the notification

<figure><img src="../.gitbook/assets/7 (2).png" alt="" width="350"><figcaption></figcaption></figure>

9. Click on **Save** to finish the Setup

## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the monitor in Uptime Kuma sends an "OK" notification, the associated alert is automatically resolved in ilert.
