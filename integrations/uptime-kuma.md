---
description: Create alerts in ilert from Uptime Kuma notifications
---

# Uptime Kuma Integration

## In ilert: Create Uptime Kuma alert source

1. Go to **Alert sources** and click on the **Create new alert source** button
2. Set a name for your Uptime Kuma source and select an escalation policy
3. Select **Uptime Kuma** in the Integration type field and save.

<figure><img src="../.gitbook/assets/1 (2).png" alt=""><figcaption></figcaption></figure>

4. On the next page a **Uptime Kuma URL** is generated. You will need this URL at the bottom of the setup in Uptime Kuma.

<figure><img src="../.gitbook/assets/2 (2).png" alt=""><figcaption></figcaption></figure>

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
