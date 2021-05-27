---
description: Receive and respond to iLert incidents in DingTalk.
---

# DingTalk Integration

[DingTalk](https://www.dingtalk.com) is an intelligent working platform created by Alibaba Group to support tens of millions of enterprises to achieve higher working efficiency with the new digitalized working method.

## In DingTalk <a id="in-dingtalk"></a>

### Add an iLert Robot to a group

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in iLert.
{% endhint %}

1. Go to DingTalk, select the group in which you want to publish iLert Incidents and click the **Context Menu** **-&gt;** **Group Assistant**

![](../.gitbook/assets/dingtalk.png)

2. Than click on the **Add Robot** button

![](../.gitbook/assets/dingtalk%20%281%29.png)

3. On the modal window click on the **Custom** tile

![](../.gitbook/assets/screenshot_27_05_21__14_49.png)

4. On the next modal window click on the **Add** button

![](../.gitbook/assets/screenshot_27_05_21__14_52.png)

5. On the next modal window, name the robot e.g. iLert, in the **Security Settings** section enable the **Additional Signature** option, check the **Terms of Service** and click on the **Finished** button

![](../.gitbook/assets/screenshot_27_05_21__14_58.png)

6. On the next modal window click on the **Finished** button

![](../.gitbook/assets/screenshot_27_05_21__15_03.png)

7. On the next modal window click on context menu **"..."** button next to the iLert robot 

![](../.gitbook/assets/screenshot_27_05_21__15_24.png)

8. On the next modal window copy the **webhook URL** and the **Additional Signature**, you will need it from step 3 in iLert.

![](../.gitbook/assets/screenshot_27_05_21__15_27.png)

## In iLert <a id="in-ilert"></a>

### Create the DingTalk Connector and link it to the alert source

1. ****Click the gear icon and then click on the **Connectors** link

![](../.gitbook/assets/screenshot_16_03_21__15_46.png)

2. Click the **Create Connector** button

![](../.gitbook/assets/screenshot_16_03_21__15_48.png)

3. On the next page, choose **DingTalk** as type, name the connector and click on the **Save** button.

![](../.gitbook/assets/ilert%20%2882%29.png)

5. Go to **Services -&gt; Alert sources** and open the alert source whose incidents you want to post to DingTalk. Click on the **Incident actions** tab and then on the **Add new incident action** button

![](../.gitbook/assets/screenshot_16_03_21__16_04.png)

6. On the next page choose **DingTalk** as the type, choose the connector created in step 3, name it**,** choose **incident events** to publish and click on the **Save** button.

![](../.gitbook/assets/ilert%20%2884%29.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the DingTalk group.

![](../.gitbook/assets/dingtalk%20%282%29.png)

## FAQ <a id="faq"></a>

**Can I link multiple DingTalk Accounts to an iLert account?**

Yes.

**Are updates to an incident published on the DingTalk group?**

Yes, the following updates to an incident are currently being released:

* **Escalations** : An incident is assigned to another user through an automatic escalation.
* **Manual Assignments** : An incident is manually assigned to someone.
* **Actions** : An incident is accepted or resolved.

**Can I choose which updates to an incident will be published in DingTalk?**

Yes.

