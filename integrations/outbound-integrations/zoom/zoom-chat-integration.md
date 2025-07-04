# Zoom Chat Integration

## In ilert: Create the Zoom Chat Connector and link it to the alert source <a href="#in-ilert" id="in-ilert"></a>

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in ilert.
{% endhint %}

1\. Click the gear icon and then click on the **Connectors** link

<figure><img src="../../../.gitbook/assets/Screenshot_16_03_21__15_46 (1).png" alt=""><figcaption></figcaption></figure>

2. Click the **Add Connector** button

<figure><img src="../../../.gitbook/assets/Screenshot_16_03_21__15_48 (1).png" alt=""><figcaption></figcaption></figure>

3. On the next page, choose **Zoom Chat** as type, name the connector and click on the save button to authorize ilert App with your Zoom account.

<figure><img src="../../../.gitbook/assets/Screenshot_16_03_21__16_18 (1).png" alt=""><figcaption></figcaption></figure>

4. On the next page, agree with the requested permissions and click on the **Authorize** button

<figure><img src="../../../.gitbook/assets/Screenshot_16_03_21__15_53 (1).png" alt=""><figcaption></figcaption></figure>

5. Go to the alert sources tab and open the alert source whose alerts you want to create Zoom Meeting. Click on the **Alert actions** tab and then on the **Add new alert action** button

<figure><img src="../../../.gitbook/assets/Screenshot_16_03_21__16_04 (1).png" alt=""><figcaption></figcaption></figure>

6. On the next page choose **Zoom Chat** as the type, choose the connector created in step 3, name it\*\*,\*\* choose **alert events** to publish and click on the **Save** button.

<figure><img src="../../../.gitbook/assets/Screenshot_16_03_21__16_27 (1).png" alt=""><figcaption></figcaption></figure>

7. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Zoom Chat channel.

<figure><img src="../../../.gitbook/assets/Zoom (2) (1).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Zoom Accounts to an ilert account?**

Yes.

**Are updates to an alert published on the Zoom Chat channel?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Zoom Chat?**

Yes.

**How can I uninstall the ilert App from my Zoom account?**

1. Login to your Zoom Account and navigate to the Zoom App Marketplace
2. Click on the **Manage** link and then on the **Installed Apps** link (alternatively you may also search for the **iLert** app)
3. Click on the **iLert** app
4. Click on the **Uninstall** button
