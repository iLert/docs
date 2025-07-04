---
description: Receive and respond to ilert alerts in Webex.
---

# Webex

[Webex](https://www.webex.com/) is the leading enterprise solution for video conferencing, online meetings, screen share, and webinars.

## In ilert: Create the Webex Connector and link it to the alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click the **gear icon** and then click on the **Connectors** link

![](../../.gitbook/assets/Screenshot_16_03_21__15_46.png)

2. Click the **Create Connector** button

![](../../.gitbook/assets/Screenshot_16_03_21__15_48.png)

3. On the next page, choose **Webex** as type, name the connector and click on the save button to authorize ilert App with your Webex account.

![](../../.gitbook/assets/Screenshot_19_03_21__07_50.png)

4. On the next page, agree with the requested permissions and click on the **Authorize** button
5. Go to **Services -> Alert sources** and open the alert source whose alerts you want to post to Webex. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../../.gitbook/assets/Screenshot_16_03_21__16_04.png)

6. On the next page choose **Webex** as the type, choose the connector created in step 3, name it,  choose **alert events** and the team to publish and click on the **Save** button.

![](../../.gitbook/assets/Screenshot_19_03_21__07_54.png)

7. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Webex space.

![](../../.gitbook/assets/Screenshot_19_03_21__07_21.png)

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Cisco Accounts to an ilert account?**

Yes.

**Are updates to an alert published on the Webex space?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Webex?**

Yes.
