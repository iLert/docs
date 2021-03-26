---
title: Microsoft Teams Integration via Incoming Webhook
seoTitle: 'iLert: Microsoft Teams Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert Microsoft Teams Integration helps you to easily connect iLert with
  Microsoft Teams.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Microsoft Teams Integration via Incoming Webhook

## In Microsoft Teams: Add an iLert Connector to a channel <a id="add-to-channel"></a>

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in iLert.
{% endhint %}

1. Select the channel in which you want to publish iLert Incidents and click **Connectors**

![](../../.gitbook/assets/mtiw1.png)

2. Type iLert in the search field and click **Configure**

![](../../.gitbook/assets/mtiw2.png)

3. Type the **connector Name** and click **Create**.

![](../../.gitbook/assets/mtiw3.png)

4. Copy the **connector URL** and click **Save**.

![](../../.gitbook/assets/mtiw4.png)

5. Your connector has now been set up. You will need the URL from step 4 in iLert.

## In iLert: Create the Microsoft Teams Connector and link it to the alert source <a id="create-alarm-source"></a>

1. Click the gear icon → **Connectors**

![](../../.gitbook/assets/mtiw5.png)

2. Click **Add Connector**

![](../../.gitbook/assets/mtiw6.png)

3. Select **Microsoft Teams** as **Type**. Assign a name for the connector, enter the URL from above and save it.

![](../../.gitbook/assets/mtiw7.png)

4. **Go to** the alert sources tab and open the alert source whose incidents you want to publish to Microsoft Teams. Click **Connections → Add New Connection**.

![](../../.gitbook/assets/mtiw8.png)

5. Select **Microsoft Teams** as the **type**, select the connector created in step 3, and name it.

![](../../.gitbook/assets/mtiw9.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Microsoft Teams channel.

![](../../.gitbook/assets/mtiw10.png)

## FAQ <a id="faq"></a>

**Can I link multiple Microsoft Teams Spaces to an iLert account?**

Yes.

**Are updates to an incident published on the Microsoft Teams channel?**

Yes, the following updates to an incident are currently being released:

* **Escalations** : An incident is assigned to another user through an automatic escalation.
* **Manual Assignments** : An incident is manually assigned to someone.
* **Actions** : An incident is accepted or resolved.

