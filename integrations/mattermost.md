---
description: >-
  The iLert Mattermost Integration helps you to bring iLert incidents into your
  Mattermost channels.
---

# Mattermost Integration

{% hint style="warning" %}
To set up this integration, you must have admin rights in iLert.
{% endhint %}

## In Mattermost <a id="add-to-channel"></a>

### Create an incoming webhook

1. Go to the main menu and click **Integrations**

![](../.gitbook/assets/screenshot_07_02_21__16_44.png)

2. Click on **Incoming Webhooks**

![](../.gitbook/assets/screenshot_07_02_21__16_45.png)

3. On the next page click on the **Add incoming Webhook** button

![](../.gitbook/assets/screenshot_07_02_21__16_47.png)

4. On the next page, name the webhook e.g. **iLert**, choose **a channel** and click on the **Save** button.

![](../.gitbook/assets/screenshot_07_02_21__16_49.png)

5. Your webhook has now been set up. You will need the URL in the next step.

## In iLert <a id="create-alarm-source"></a>

### Create the Mattermost Connector and link it to your alert source

1. Click on the gear icon and navigate to → **Connectors**

![](../.gitbook/assets/go_to_connectors%20%283%29.png)

2. Click on **Add Connector**

![](../.gitbook/assets/create_connector_button.png)

3. Select **Mattermost** as **Type**. Assign a name for the connector, enter the URL from above and save it.

![](../.gitbook/assets/screenshot_07_02_21__16_53.png)

4. **Go to** the alert sources tab and open the alert source whose incidents you want to publish to Mattermost. Click **Incident actions → Create incident action**.

![](../.gitbook/assets/new_incident_action%20%287%29.png)

5. Select **Mattermost** as the **type**, select the connector created in step 3 and give your connection a name.

![](../.gitbook/assets/ilert%20%2874%29.png)

6. Finished! You can now test the connection by clicking on the **Test this connection** button.  
A test message will be posted in the Mattermost channel.

![](../.gitbook/assets/ilert%20%2875%29.png)

## FAQ <a id="faq"></a>

**Can I link multiple Mattermost Spaces to an iLert account?**

Yes.

**Are updates to an incident published in the Mattermost channel?**

Yes, the following updates to an incident are currently being published:

* **Escalations** : An incident is assigned to another user through an automatic escalation.
* **Manual Assignments** : An incident is manually assigned to someone.
* **Actions** : An incident is accepted or resolved.

