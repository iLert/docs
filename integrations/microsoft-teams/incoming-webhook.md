---
title: Microsoft Teams Integration via Incoming Webhook
seoTitle: 'iLert: Microsoft Teams Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert Microsoft Teams Integration helps you to bring alerts into your
  channels without installing the app.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Microsoft Teams Integration via Incoming Webhook

{% hint style="warning" %}
If possible we suggest to use [iLert's Microsoft Teams Bot](chat.md) for the setup, this guide and integration is only suggested in case you do not want to grant any permissions to iLert
{% endhint %}

## In Microsoft Teams: Add an iLert Connector to a channel <a id="add-to-channel"></a>

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in iLert.
{% endhint %}

1. Select the channel in which you want to publish iLert Alerts and click **Connectors**
2. Type iLert in the search field and click **Configure**
3. Type the **connector Name** and click **Create**.
4. Copy the **connector URL** and click **Save**.
5. Your connector has now been set up. You will need the URL from step 4 in iLert.

## In iLert: Create the Microsoft Teams Connector and link it to the alert source <a id="create-alarm-source"></a>

1. Click the gear icon → **Connectors**
2. Click **Add Connector**
3. Select **Microsoft Teams** as **Type**. Assign a name for the connector, enter the URL from above and save it.
4. **Go to** the alert sources tab and open the alert source whose alerts you want to publish to Microsoft Teams. Click **Connections → Add New Connection**.
5. Select **Microsoft Teams** as the **type**, select the connector created in step 3, and name it.
6. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Microsoft Teams channel.

## FAQ <a id="faq"></a>

**Can I link multiple Microsoft Teams Spaces to an iLert account?**

Yes.

**Are updates to an alert published on the Microsoft Teams channel?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

