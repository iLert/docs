---
description: Receive and respond to ilert alerts in DingTalk.
---

# DingTalk Integration

[DingTalk](https://www.dingtalk.com) is an intelligent working platform created by Alibaba Group to support tens of millions of enterprises to achieve higher working efficiency with the new digitalized working method.

## In DingTalk: Add an ilert Robot to a group <a href="#in-dingtalk" id="in-dingtalk"></a>

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in ilert.
{% endhint %}

1. Go to DingTalk, select the group in which you want to publish ilert Alerts and click the **Context Menu** **->** **Group Assistant**

![](<../../.gitbook/assets/DingTalk (2).png>)

2. Than click on the **Add Robot** button

![](<../../.gitbook/assets/DingTalk (1).png>)

3. On the modal window click on the **Custom** tile

![](../../.gitbook/assets/Screenshot_27_05_21__14_49.png)

4. On the next modal window click on the **Add** button

![](../../.gitbook/assets/Screenshot_27_05_21__14_52.png)

5. On the next modal window, name the robot e.g. ilert, in the **Security Settings** section enable the **Additional Signature** option, check the **Terms of Service** and click on the **Finished** button

![](../../.gitbook/assets/Screenshot_27_05_21__14_58.png)

6. On the next modal window click on the **Finished** button

![](<../../.gitbook/assets/Screenshot_27_05_21__15_03 (1).png>)

7. On the next modal window click on context menu **"..."** button next to the ilert robot

![](../../.gitbook/assets/Screenshot_27_05_21__15_24.png)

8. On the next modal window copy the **webhook URL** and the **Additional Signature**, you will need it from step 3 in ilert.

![](../../.gitbook/assets/Screenshot_27_05_21__15_27.png)

## In ilert: Create the DingTalk Connector and link it to the alert source <a href="#in-ilert" id="in-ilert"></a>

1. **\*\*Click the gear icon and then click on the** Connectors\*\* link

![](../../.gitbook/assets/Screenshot_16_03_21__15_46.png)

2. Click the **Create Connector** button

![](../../.gitbook/assets/Screenshot_16_03_21__15_48.png)

3. On the next page, choose **DingTalk** as type, name the connector and click on the **Save** button.

![](<../../.gitbook/assets/iLert (96).png>)

4. Go to **Services -> Alert sources** and open the alert source whose alerts you want to post to DingTalk. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../../.gitbook/assets/Screenshot_16_03_21__16_04.png)

5. On the next page choose **DingTalk** as the type, choose the connector created in step 3, name it\*\*,\*\* choose **alert events** to publish and click on the **Save** button.

![](<../../.gitbook/assets/iLert (64).png>)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the DingTalk group.

![](../../.gitbook/assets/DingTalk.png)

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple DingTalk Accounts to an ilert account?**

Yes.

**Are updates to an alert published on the DingTalk group?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in DingTalk?**

Yes.
