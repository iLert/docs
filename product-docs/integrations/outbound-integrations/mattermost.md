---
description: >-
  The ilert Mattermost Integration helps you to bring ilert alerts into your
  Mattermost channels.
---

# Mattermost Integration

{% hint style="warning" %}
To set up this integration, you must have admin rights in ilert.
{% endhint %}

## In Mattermost: Create an incoming webhook <a href="#add-to-channel" id="add-to-channel"></a>

1. Go to the main menu and click **Integrations**

![](../../.gitbook/assets/Screenshot_07_02_21__16_44.png)

2. Click on **Incoming Webhooks**

![](../../.gitbook/assets/Screenshot_07_02_21__16_45.png)

3. On the next page click on the **Add incoming Webhook** button

![](../../.gitbook/assets/Screenshot_07_02_21__16_47.png)

4. On the next page, name the webhook e.g. **iLert**, choose **a channel** and click on the **Save** button.

![](../../.gitbook/assets/Screenshot_07_02_21__16_49.png)

5. Your webhook has now been set up. You will need the URL in the next step.

## In ilert: Create the Mattermost Connector and link it to your alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon and navigate to → **Connectors**

![](<../../.gitbook/assets/go_to_connectors (3).png>)

2. Click on **Add Connector**

![](<../../.gitbook/assets/create_connector_button (8).png>)

3. Select **Mattermost** as **Type**. Assign a name for the connector, enter the URL from above and save it.

![](../../.gitbook/assets/Screenshot_07_02_21__16_53.png)

4. **Go to** the alert sources tab and open the alert source whose alerts you want to publish to Mattermost. Click **Alert actions → Create alert action**.

![](<../../.gitbook/assets/new_incident_action (7) (1).png>)

5. Select **Mattermost** as the **type**, select the connector created in step 3 and give your connection a name.

![](<../../.gitbook/assets/iLert (31).png>)

6. Finished! You can now test the connection by clicking on the **Test this connection** button. A test message will be posted in the Mattermost channel.

![](<../../.gitbook/assets/iLert (88).png>)

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Mattermost Spaces to an ilert account?**

Yes.

**Are updates to an alert published in the Mattermost channel?**

Yes, the following updates to an alert are currently being published:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.
