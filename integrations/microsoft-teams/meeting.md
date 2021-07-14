---
description: Create Microsoft Teams Meeting from iLert incidents.
---

# Microsoft Teams Integration Meeting

[Microsoft Teams](https://www.microsoft.com/en-ww/microsoft-teams/group-chat-software) is the hub for team collaboration in Microsoft 365 that integrates the people, content, and tools your team needs to be more engaged and effective.

## In iLert <a id="create-alarm-source"></a>

### Create the Microsoft Teams Meeting Connector and link it to the alert source

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in iLert.
{% endhint %}

1. ****Click the gear icon and then click on the **Connectors** link

![](../../.gitbook/assets/screenshot_16_03_21__15_46.png)

2. Click the **Add Connector** button

![](../../.gitbook/assets/screenshot_16_03_21__15_48.png)

3. On the next page, choose **Microsoft Teams Meeting** as type, name the connector and click on the save button to authorize iLert App with your Microsoft Teams account.

![](../../.gitbook/assets/ilert%20%2845%29.png)

4. On the next page, agree with the requested permissions and click on the **Authorize** button

5. Go to the alert sources tab and open the alert source whose incidents you want to create Microsoft Teams Meeting. Click on the **Incident actions** tab and then on the **Add new incident action** button

![](../../.gitbook/assets/screenshot_16_03_21__16_04.png)

6. On the next page choose **Microsoft Teams Meeting** as the type, choose the connector created in step 3, name it, choose **Trigger mode** and click on the **Save** button.

![](../../.gitbook/assets/ilert%20%2837%29.png)

7. Finished! Now a Microsoft Teams Meeting will be created  for each incident in automatic trigger mode or via manual incident action.

![](../../.gitbook/assets/ilert%20%2840%29.png)

## FAQ <a id="faq"></a>

**Can I link multiple Microsoft Teams Accounts to an iLert account?**

Yes.

**How can I uninstall the iLert App from my Microsoft Teams account?**

1. Login to your Microsoft Teams Account and navigate to your team 
2. Click on the **More options** menu and then on the **Manage team** option
3. Click on the **Apps** tab
4. Find the **iLert** app
5. Click on the **Uninstall** button

