---
title: Discord Integration
seoTitle: 'iLert: Discord for Alerting | Incident Response | Uptime'
description: >-
  The iLert Discord Integration helps you to bring iLert alerts into your
  Discord channels
date: '2020-04-23T05:02:05.000Z'
weight: 1
---

# Discord Integration

[Discord](https://discord.com/) is the easiest way to talk over voice, video, and text. Talk, chat, hang out, and stay close with your friends and communities.

## In Discord <a id="in-discord"></a>

### Create a webhook <a id="create-webhook"></a>

1. Go to **Discord** and select a server
2. Go to a **Text Channel**, then click on the **Edit Channel** button

![](../.gitbook/assets/screenshot_2021-07-02_at_10_56_32.png)

1. On the page click on the **Integrations** menu and then on the **Create Webhook** button

![](../.gitbook/assets/general_-_discord%20%281%29.png)

1. On the next page, name the webhook, e.g. iLert, save the changes and copy the **Webhook URL**

![](../.gitbook/assets/general_-_discord.png)

## In iLert <a id="in-ilert"></a>

### Create a Discord Connector and Link to the alert source <a id="create-alarm-source"></a>

1. Click on the gear icon and then on the **Connectors** button

![](../.gitbook/assets/go_to_connectors%20%284%29.png)

1. Click on **Add Connector**

![](../.gitbook/assets/create_connector_button%20%282%29.png)

1. Select **Discord** as **type** and fill in all fields. Enter a name and paste the Webhook URL of your Discord server that you have created in the previous step.

![](../.gitbook/assets/ilert%20%2888%29.png)

1. Go to the alert sources tab and open the alert source whose alerts you want to publish in Discord. Click on **Alert actions** and then on **Create alert action**.

![](../.gitbook/assets/new_incident_action%20%2812%29.png)

1. Select **Discord** as the **type**, **\*\*select the connector created in step 3 and click on** Save\*\* button.

![](../.gitbook/assets/ilert%20%2887%29.png)

1. Finished! You can now test the connection by clicking on the button **Test this connection**.  

   A test ticket will be created in Discord.

![](../.gitbook/assets/ilert%20%2889%29.png)

## FAQ <a id="faq"></a>

**Can I link multiple Discord Accounts to an iLert account?**

Yes.

**Are updates to an alert published on the Discord Chat channel?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Discord Chat?**

Yes.

