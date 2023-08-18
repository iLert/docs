---
description: >-
  The ilert Microsoft Teams Chat Integration helps you to bring alerts into your
  channels, acknowledge or resolve alerts without leaving the chat.
---

# Microsoft Teams Chat Integration

[Microsoft Teams](https://www.microsoft.com/en-ww/microsoft-teams/group-chat-software) is the hub for team collaboration in Microsoft 365 that integrates the people, content, and tools your team needs to be more engaged and effective.

## In Microsoft Teams <a href="#in-microsoft-teams" id="in-microsoft-teams"></a>

### Install the ilert bot application

{% hint style="info" %}
**Admin permission required**

To install the bot application, you must have admin rights in Microsoft Teams.
{% endhint %}

1. Open the application in Microsoft Teams: [https://teams.microsoft.com/l/app/8f3b287d-df09-44e2-93b3-35e0dfa90756](https://teams.microsoft.com/l/app/8f3b287d-df09-44e2-93b3-35e0dfa90756)
2. Add the ilert bot to a team

![](../../../.gitbook/assets/General\_\_Demo\_\_\_\_Microsoft\_Teams.png)

1. Choose a team and channel name and click on the **Set up a bot** button

![](<../../../.gitbook/assets/General\_\_Demo\_\_\_\_Microsoft\_Teams (1).png>)

1. You should have received a welcome message in the previously selected channel, if you do not see the message or you want to reconnect use the `@iLert connect` command to bring it up again. Click on the **Connect** button in the message, this will take you to ilert's login page to finish your connection.

![](<../../../.gitbook/assets/General\_\_Demo\_\_\_\_Microsoft\_Teams (2).png>)

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in ilert.
{% endhint %}

1. Login to the ilert account which you want to connect to Microsoft Teams and ilert will automatically setup the connection for you - _depending on your login state in Microsoft 365 you will have to login to Microsoft again, afterwards you will be automatically taken back to iLert_ and you should see a success message with your newly created connector.

![](<../../../.gitbook/assets/iLert (97).png>)

## In ilert <a href="#in-ilert" id="in-ilert"></a>

Now that the initial connection between your Microsoft Teams and ilert accounts has been setup, you may choose alert sources which should send update messages to your Microsoft Teams channels - this is done by creating Alert Actions in ilert.

### Link the Microsoft Teams Chat Connector to the alert source <a href="#link-the-microsoft-teams-chat-connector-to-the-alert-source" id="link-the-microsoft-teams-chat-connector-to-the-alert-source"></a>

1. Go to the alert sources tab and open the alert source whose alert's updates you want to publish into Microsoft Teams channels. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../../../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_04.png)

1. On the next page choose **Microsoft Teams** as the type, choose the connector created before, name your action\*\*,\*\* choose **Chat** as Teams Action, choose **Your team**, then choose **Your channel** and click on the **Save** button.

![](<../../../.gitbook/assets/iLert (98).png>)

1. Finished! You can now test the connection by clicking on the button **Test this connection**. Thereafter, a test message will be posted in your Microsoft Teams channel.

![](../../../.gitbook/assets/General\_\_Roman\_\_\_\_Microsoft\_Teams.png)

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Microsoft Teams Accounts to an ilert account?**

Yes.

**Are updates to an alert published on the Microsoft Teams Chat channel?**

Yes, the following updates to an alert are currently being published:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.

**Can I choose which updates to an alert will be published in Microsoft Teams Chat?**

No.

**How can I uninstall the ilert App from my Microsoft Teams account?**

1. Login to your Microsoft Teams Account and navigate to your team
2. Click on the **More options** menu and then on the **Manage team** option
3. Click on the **Apps** tab
4. Find the **iLert** app
5. Click on the **Uninstall** button

**The ilert app does not see all team groups of my Microsoft Teams account, what can I do?**

The ilert app needs the `Group.ReadWrite.All` and `Team.ReadBasic.All` scopes to read the all team groups including legacy Skype groups. Please contact the Microsoft Teams admin who can give the permission for the ilert app. You can read more about the required scopes [here](https://docs.microsoft.com/en-us/graph/teams-list-all-teams).

**The ilert app does not see all channels of my team, what can I do?**

The ilert app needs the `Channel.ReadBasic.All` scope to read the team groups. Please contact the Microsoft Teams admin who can give the permission for the ilert app. You can read more about the required scope [here](https://docs.microsoft.com/en-us/graph/api/channel-list).

If you still don't see all the channels, then those are private channels that are protected, and you need to invite the bot to the channel.
