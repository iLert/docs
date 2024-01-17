---
description: Use Microsoft Teams as an alert source
---

# Create alerts in Microsoft Teams



{% hint style="info" %}
Connect your Microsoft Teams workspace with ilert first

Before you proceed, please make sure that a global admin has connected your Microsoft Teams workspace with your ilert account (as described in our [integration for Microsoft Teams guide](chat/#install-the-ilert-bot-application))
{% endhint %}

Our integration for Microsoft Teams lets you create alerts directly within Microsoft Teams and streamlines your incident management process, making it even easier for your team and stakeholders to report incidents.

### Overview

There are two ways to configure the alert creation feature in Microsoft Teams:

1. **Restrict to Microsoft Teams users with an ilert account**: This mode doesn't require any additional configuration other than installing our Microsoft Teams app (as described in the [integration for Microsoft Teams guide](chat/))
2. **Allow any Microsoft Teams user to create an alert:** This method requires the creation of a dedicated Microsoft Teams alert source in ilert and allows you to control the Microsoft Teams channels where users will be able to create an alert, to which escalation policy the alert is routed to and what [notification priority](../../alerting/alert-sources.md#customise-your-alerts-with-notification-priority) is used.

### Option 1: Restrict to Microsoft Teams users with an ilert account

Once you have our Microsoft Teams app installed in your Microsoft Teams workspace, any Microsoft Teams user with an ilert account can create an alert from any channel by mentioning the ilert bot with `@iLert alert`.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 09.06.00.png" alt=""><figcaption></figcaption></figure>

Enter an **Alert summary** and click on the **Continue** button.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 09.09.12.png" alt=""><figcaption></figcaption></figure>

The user's permissions in ilert will be taken into account. Therefore, they will only see alert sources and escalation policies to which they have access to.

### Option 2: Allow any Microsoft Teams user to create an alert

You can let any Microsoft Teams user (even if they don't have an ilert account) create an alert from Microsoft Teams. In order to control which teams they will be able to alert and control notification priority, you need to create a dedicated Microsoft Teams alert source in ilert.

1. Go to Alert sources --> Alert sources and click on **Create new alert source**
2. Select **Microsoft Teams** as the alert source type, give it a name, e.g. _Microsoft Teams alerts from channel xyz_, select an escalation policy and click on **Create**.
3. In the next screen, click on the **Microsoft Teams settings** tab to configure
   * the Microsoft Teams channels from where Microsoft Teams users should be able to create alerts
   * and the escalation policies that users can select from



<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 09.16.12.png" alt=""><figcaption></figcaption></figure>

4. Now any Microsoft Teams user in your workspace will be able to create alerts from the configured channels. They will be limited to the pre-configured escalation policies and the alert creation will take into account whatever is configured in the alert source (e.g. notification priority and other alert actions). To create a new alert, mention the ilert bot with the following command in any of the configured channel

```
@iLert alert
```

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 09.06.00.png" alt=""><figcaption></figcaption></figure>

5. Enter an **Alert summary** and click on the **Continue** button.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 09.07.10.png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.youtube.com/watch?v=OcVYZpqM0iw" %}
Check out our step-by-step tutorial on Youtube
{% endembed %}

## FAQ

#### **I have received following error messages:** There is no Microsoft Teams alert source configured for this channel in ilert, which is required to enable alert creation for Microsoft Teams users without an ilert account.

If an unauthorized user tries to create a new alert from Microsoft Teams, the ilert bot for Microsoft Teams requires the channel to be set in a Microsoft Teams alert source in ilert. To fix this issue please follow the steps in [Option 2](create-alerts-in-microsoft-teams.md#option-2-allow-any-microsoft-teams-user-to-create-an-alert).

If your ilert bot for Microsoft Teams bot has no permission. Please reauthorize your bot.
