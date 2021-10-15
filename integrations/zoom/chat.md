---
description: >-
  The iLert Zoom Chat Integration helps you to bring iLert alerts into your Zoom
  channels, acknowledge or resolve alerts without leaving the chat.
---

# Zoom Chat Integration

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create the Zoom Chat Connector and link it to the alert source

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in iLert.
{% endhint %}

1. **\*\*Click the gear icon and then click on the **Connectors\*\* link

![](../../.gitbook/assets/Screenshot\_16\_03\_21\__15\_46.png)

1. Click the **Add Connector** button

![](../../.gitbook/assets/Screenshot\_16\_03\_21\__15\_48.png)

1. On the next page, choose **Zoom Chat** as type, name the connector and click on the save button to authorize iLert App with your Zoom account.

![](../../.gitbook/assets/Screenshot\_16\_03\_21\__16\_18.png)

1. On the next page, agree with the requested permissions and click on the **Authorize** button

![](../../.gitbook/assets/Screenshot\_16\_03\_21\__15\_53.png)

1. Go to the alert sources tab and open the alert source whose alerts you want to create Zoom Meeting. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../../.gitbook/assets/Screenshot\_16\_03\_21\__16\_04.png)

1. On the next page choose **Zoom Chat** as the type, choose the connector created in step 3, name it**,** choose **alert events** to publish and click on the **Save** button.

![](../../.gitbook/assets/Screenshot\_16\_03\_21\__16\_27.png)

1. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Zoom Chat channel.

![](<../../.gitbook/assets/Zoom (2).png>)

## FAQ <a href="faq" id="faq"></a>

**Can I link multiple Zoom Accounts to an iLert account?**

Yes.

**Are updates to an alert published on the Zoom Chat channel?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Zoom Chat?**

Yes.

**How can I uninstall the iLert App from my Zoom account?**

1. Login to your Zoom Account and navigate to the Zoom App Marketplace
2. Click on the **Manage** link and then on the **Installed Apps** link (alternatively you may also search for the **iLert** app)
3. Click on the **iLert** app
4. Click on the **Uninstall** button
