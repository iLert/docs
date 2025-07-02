---
description: Create Microsoft Teams Meeting from ilert alerts.
---

# Microsoft Teams Meeting Integration

[Microsoft Teams](https://www.microsoft.com/en-ww/microsoft-teams/group-chat-software) is the hub for team collaboration in Microsoft 365 that integrates the people, content, and tools your team needs to be more engaged and effective.

## In Microsoft Teams <a href="#in-microsoft-teams" id="in-microsoft-teams"></a>

### Install the ilert bot application

{% hint style="info" %}
**Admin permission required**

To install the bot application, you must have admin rights in Microsoft Teams.
{% endhint %}

1. Open the application in Microsoft Teams: [https://teams.microsoft.com/l/app/8f3b287d-df09-44e2-93b3-35e0dfa90756](https://teams.microsoft.com/l/app/8f3b287d-df09-44e2-93b3-35e0dfa90756)
2. Add the ilert bot to a team

![](../../.gitbook/assets/General__Demo____Microsoft_Teams.png)

1. Choose a team and channel name and click on the **Set up a bot** button

![](<../../.gitbook/assets/General__Demo____Microsoft_Teams (1).png>)

1. You should have received a welcome message in the previously selected channel, if you do not see the message or you want to reconnect use the `@iLert connect` command to bring it up again. Click on the **Connect** button in the message, this will take you to ilert's login page to finish your connection.

![](<../../.gitbook/assets/General__Demo____Microsoft_Teams (2).png>)

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in ilert.
{% endhint %}

1. Login to the ilert account which you want to connect to Microsoft Teams and ilert will automatically setup the connection for you - _depending on your login state in Microsoft 365 you will have to login to Microsoft again, afterwards you will be automatically taken back to ilert_ and you should see a success message with your newly created connector.

![](<../../.gitbook/assets/iLert (97).png>)

## In ilert <a href="#in-ilert" id="in-ilert"></a>

Now that the initial connection between your Microsoft Teams and ilert accounts has been set up, you may choose alert sources for which you want to configure meeting actions.

### Link the Microsoft Teams Connector to the alert source

1. **\*\*Go to the alert sources tab and open the alert source for which you want to configure the meeting action. Click on the** Alert actions **tab and then on the** Add new alert action\*\* button

![](../../.gitbook/assets/Screenshot_16_03_21__16_04.png)

1. On the next page choose **Microsoft Teams** as the type, choose the connector created before, name your action\*\*,\*\* choose **Meeting** as Teams Action, choose **Your team**, then choose **Your channel** and click on the **Save** button.

![](<../../.gitbook/assets/iLert (99).png>)

1. Finished! A Microsoft Teams Meeting alert action will now be available on each alert that is created by your alert source. Triggering the action (use **...** in the top right actions bar) will add a **Join Meeting Link** to the alert in ilert as well as post a message into your configured Microsoft Teams channel with the meeting's details.

![](<../../.gitbook/assets/iLert (100).png>)

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Microsoft Teams Accounts to an ilert account?**

Yes.

**How can I uninstall the ilert App from my Microsoft Teams account?**

1. Login to your Microsoft Teams Account and navigate to your team
2. Click on the **More options** menu and then on the **Manage team** option
3. Click on the **Apps** tab
4. Find the **iLert** app
5. Click on the **Uninstall** button
