---
description: >-
  The iLert Mattermost Integration helps you to easily connect iLert with
  Mattermost.
---

# Mattermost Intergration

**Admin permission required**

To set up the integration, you must have admin rights in iLert.

## In Mattermost <a id="add-to-channel"></a>

### Create an incoming webhook

1. Go to main menu and click **Integrations**

![](../.gitbook/assets/screenshot_07_02_21__16_44.png)

2. Click on **Incommin Webhooks**

![](../.gitbook/assets/screenshot_07_02_21__16_45.png)

3. On the next page click on the **Add incoming Webhook** button

![](../.gitbook/assets/screenshot_07_02_21__16_47.png)

4. On the next page, name the webhook e.g. **iLert**, choose **a channel** and click on **Save** button.

![](../.gitbook/assets/screenshot_07_02_21__16_49.png)

5. Your webhook has now been set up. You will need the URL from step 4 in iLert.

## In iLert <a id="create-alarm-source"></a>

### Create the Mattermost Connector and link it to the alert source

1. Click the gear icon → **Connectors**

![](../.gitbook/assets/mtiw5.png)

2. Click **Add Connector**

![](../.gitbook/assets/mtiw6.png)

3. Select **Mattermost** as **Type**. Assign a name for the connector, enter the URL from above and save it.

![](../.gitbook/assets/screenshot_07_02_21__16_53.png)

4. **Go to** the alert sources tab and open the alert source whose incidents you want to publish to Mattermost. Click **Connections → Add New Connection**.

![](../.gitbook/assets/mtiw8.png)

5. Select **Mattermost** as the **type**, select the connector created in step 3, and name it.

![](../.gitbook/assets/screenshot_07_02_21__16_54.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Mattermost channel.

![](../.gitbook/assets/screenshot_07_02_21__16_55.png)

## FAQ <a id="faq"></a>

**Can I link multiple Mattermost Spaces to an iLert account?**

Yes.

**Are updates to an incident published on the Mattermost channel?**

Yes, the following updates to an incident are currently being released:

* **Escalations** : An incident is assigned to another user through an automatic escalation.
* **Manual Assignments** : An incident is manually assigned to someone.
* **Actions** : An incident is accepted or resolved.

