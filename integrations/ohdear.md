---
description: >-
  Oh Dear is a tool that monitors uptime, SSL certificates, broken links,
  scheduled tasks, DNS and more and it will send out notifications when
  something's wrong
---

# Oh Dear Integration

## In ilert

* Go to the "**Alert sources**" tab and click "**Create new alert source**"
* Enter a name and select your desired escalation policy.
* Select "**Oh Dear**" as the **Integration Type** and click **Save**.
* On the next page, an **Oh Dear URL** is generated. You will need the URL for the webhook configuration

## In Oh Dear

1. Click the Profile on top Right, and then click **Team Notifications**

![](../.gitbook/assets/ohdear\_notifications.png)

2. Click on **Webhooks** on the left, put the **Oh Dear URL** that we got in ilert earlier in **Webhook URL** and press **Update** button

![](../.gitbook/assets/ohdear\_webhook.png)

3. On any Incident an Alert event will be created on ilert
4. For more information about the webhook on Oh Dear please refer here: [https://ohdear.app/docs/integrations/webhooks/introduction](https://ohdear.app/docs/integrations/webhooks/introduction)
