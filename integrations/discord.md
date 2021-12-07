---
description: >-
  The iLert Discord Integration helps you to bring iLert alerts into your
  Discord channels
---

# Discord Integration

[Discord](https://discord.com) is the easiest way to talk over voice, video, and text. Talk, chat, hang out, and stay close with your friends and communities.

## In Discord <a href="#in-discord" id="in-discord"></a>

### Create a webhook <a href="#create-webhook" id="create-webhook"></a>

1. Go to **Discord** and select a server
2. Go to a **Text Channel**, then click on the **Edit Channel** button

![](../.gitbook/assets/screenshot\_2021-07-02\_at\_10\_56\_32.png)

1. On the page click on the **Integrations** menu and then on the **Create Webhook** button

![](<../.gitbook/assets/general\_-\_discord (1).png>)

1. On the next page, name the webhook, e.g. iLert, save the changes and copy the **Webhook URL**

![](../.gitbook/assets/general\_-\_discord.png)

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Discord Connector and Link to the alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon and then on the **Connectors** button

![](<../.gitbook/assets/go\_to\_connectors (4).png>)

1. Click on **Add Connector**

![](<../.gitbook/assets/create\_connector\_button (2).png>)

1. Select **Discord** as **type** and fill in all fields. Enter a name and paste the Webhook URL of your Discord server that you have created in the previous step.

![](<../.gitbook/assets/ilert (88).png>)

1. Go to the alert sources tab and open the alert source whose alerts you want to publish in Discord. Click on **Alert actions** and then on **Create alert action**.

![](<../.gitbook/assets/new\_incident\_action (12).png>)

1. Select **Discord** as the **type**, **\*\*select the connector created in step 3 and click on** Save\*\* button.

![](<../.gitbook/assets/ilert (87).png>)

1.  Finished! You can now test the connection by clicking on the button **Test this connection**. &#x20;

    A test ticket will be created in Discord.

![](<../.gitbook/assets/ilert (89).png>)

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Discord Accounts to an iLert account?**

Yes.

**Are updates to an alert published on the Discord Chat channel?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Discord Chat?**

Yes.
