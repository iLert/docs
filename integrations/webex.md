---
description: Receive and respond to iLert alerts in Cisco Webex.
---

# Cisco Webex

[Cisco Webex](https://www.webex.com/) is the leading enterprise solution for video conferencing, online meetings, screen share, and webinars.

## In iLert <a id="create-alarm-source"></a>

### Create the Cisco Webex Connector and link it to the alert source

1. **\*\*Click the gear icon and then click on the** Connectors\*\* link

![](../.gitbook/assets/screenshot_16_03_21__15_46.png)

1. Click the **Create Connector** button

![](../.gitbook/assets/screenshot_16_03_21__15_48.png)

1. On the next page, choose **Cisco Webex** as type, name the connector and click on the save button to authorize iLert App with your Webex account.

![](../.gitbook/assets/screenshot_19_03_21__07_50.png)

1. On the next page, agree with the requested permissions and click on the **Authorize** button
2. Go to **Services -&gt; Alert sources** and open the alert source whose alerts you want to post to Cisco Webex. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../.gitbook/assets/screenshot_16_03_21__16_04.png)

1. On the next page choose **Cisco Webex** as the type, choose the connector created in step 3, name it**,** choose **alert events** and **\*\*the** space **to publish and click on the** Save\*\* button.

![](../.gitbook/assets/screenshot_19_03_21__07_54.png)

1. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Cisco Webex space.

![](../.gitbook/assets/screenshot_19_03_21__07_21.png)

## FAQ <a id="faq"></a>

**Can I link multiple Cisco Accounts to an iLert account?**

Yes.

**Are updates to an alert published on the Cisco Webex space?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Cisco Webex?**

Yes.

