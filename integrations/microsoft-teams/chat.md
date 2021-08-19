---
description: >-
  The iLert Microsoft Teams Chat Integration helps you to bring incidents into
  your channels, acknowledge or resolve incidents without leaving the chat.
---

# Microsoft Teams Chat Integration

[Microsoft Teams](https://www.microsoft.com/en-ww/microsoft-teams/group-chat-software) is the hub for team collaboration in Microsoft 365 that integrates the people, content, and tools your team needs to be more engaged and effective.

## In Microsoft Teams <a id="in-microsoft-teams"></a>

### Install the iLert bot application

{% hint style="info" %}
**Admin permission required**

To install the bot application, you must have admin rights in Microsoft Teams.
{% endhint %}

1. Open the application in Microsoft Teams: [https://teams.microsoft.com/l/app/8f3b287d-df09-44e2-93b3-35e0dfa90756](https://teams.microsoft.com/l/app/8f3b287d-df09-44e2-93b3-35e0dfa90756)

2. Add the iLert bot to a team

![](../../.gitbook/assets/general__demo____microsoft_teams%20%281%29.png)

3. Choose a team and channel name and click on the **Set up a bot** button

![](../../.gitbook/assets/general__demo____microsoft_teams%20%282%29.png)

4. On the welcome message click on the **Connect** button or use `@iLert connect` command to connect your iLert account with Microsoft Teams

![](../../.gitbook/assets/general__demo____microsoft_teams.png)

5. Login to your iLert account and the Microsoft Teams connect will be created automatically

![](../../.gitbook/assets/ilert%20%2898%29.png)

## In iLert <a id="in-ilert"></a>

### Link the Microsoft Teams Chat Connector to the alert source <a id="link-the-microsoft-teams-chat-connector-to-the-alert-source"></a>

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in iLert.
{% endhint %}

1. ****Go to the alert sources tab and open the alert source whose incidents you want to post into Microsoft Teams channel. Click on the **Incident actions** tab and then on the **Add new incident action** button

![](../../.gitbook/assets/screenshot_16_03_21__16_04.png)

2. On the next page choose **Microsoft Teams** as the type, choose the connector created before, name it**,** choose **Chat** as Teams Action, choose **Your team**, then choose **Your channel** and click on the **Save** button.

![](../../.gitbook/assets/ilert%20%2897%29.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted on the Microsoft Teams channel.

![](../../.gitbook/assets/general__roman____microsoft_teams.png)

## FAQ <a id="faq"></a>

**Can I link multiple Microsoft Teams Accounts to an iLert account?**

Yes.

**Are updates to an incident published on the Microsoft Teams Chat channel?**

Yes, the following updates to an incident are currently being released:

* **Escalations** : An incident is assigned to another user through an automatic escalation.
* **Manual Assignments** : An incident is manually assigned to someone.
* **Actions** : An incident is accepted or resolved.

**Can I choose which updates to an incident will be published in Microsoft Teams Chat?**

Yes.

**How can I uninstall the iLert App from my Microsoft Teams account?**

1. Login to your Microsoft Teams Account and navigate to your team 
2. Click on the **More options** menu and then on the **Manage team** option
3. Click on the **Apps** tab
4. Find the **iLert** app
5. Click on the **Uninstall** button

