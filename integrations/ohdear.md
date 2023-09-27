---
description: >-
  Oh Dear is a tool that monitors uptime, SSL certificates, broken links,
  scheduled tasks, DNS and more and it will send out notifications when
  something's wrong
---

# Oh Dear Integration

## In ilert: Create an Oh Dear alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Oh Dear** in the search field, click on the Oh Dear tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Oh Dear

1. Click the Profile on top Right, and then click **Team Notifications**

![](../.gitbook/assets/ohdear\_notifications.png)

2. Click on **Webhooks** on the left, put the **Oh Dear URL** that we got in ilert earlier in **Webhook URL** and press **Update** button

![](../.gitbook/assets/ohdear\_webhook.png)

3. On any Incident an Alert event will be created on ilert
4. For more information about the webhook on Oh Dear please refer here: [https://ohdear.app/docs/integrations/webhooks/introduction](https://ohdear.app/docs/integrations/webhooks/introduction)
