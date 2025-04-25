---
description: Check who is on-call right from Microsoft Teams using @ilert oncall command.
---

# Look up who is on-call in Microsoft Teams

{% hint style="info" %}
**Connect your Microsoft Teams with ilert first.**

Before you proceed, please make sure that a global admin has connected your Microsoft Teams workspace with your ilert account (as described in our [Integration for Microsoft Teams guide](https://docs.ilert.com/chatops/microsoft-teams/chat#install-the-ilert-bot-application)).
{% endhint %}

The `@ilert oncall` command lets you look up who is on-call from any Microsoft Teams channel. There are two ways to configure the on-call lookup feature:

1. **Restrict lookup to Microsoft Teams users with an ilert account:** This mode doesn't require any additional configuration other than installing the ilert bot application (it is described in this article: [Microsoft Teams Integration](https://docs.ilert.com/chatops/microsoft-teams/chat)).
2. **Allow any Microsoft Teams user to use the on-call lookup feature:** This method requires the creation of a dedicated Microsoft Teams alert source in ilert and allows you to control the Microsoft Teams channels where users can check who is on-call.

### Option 1: Restrict to Microsoft Teams users with an ilert account

Once you have ilert Microsoft Teams app installed in your Microsoft Teams workspace, any Microsoft Teams user with an ilert account can look up who is on-call from any channel by mentioning the ilert bot with `@ilert oncall`.

<figure><img src="../../.gitbook/assets/01 ms teams oncall (1).png" alt=""><figcaption></figcaption></figure>

Push **Continue** button, then **Open Search Menu** in the popup menu, and choose between two options: on-call lookup for alert sources or for escalation policies. You will then see the on-call person's details.

<figure><img src="../../.gitbook/assets/02 ms teams oncall.png" alt=""><figcaption></figcaption></figure>

### Option 2: Allow any Microsoft Teams user to use on-call lookup

You can let any Microsoft Teams user (even if they don't have an ilert account) check who is on-call from Microsoft Teams. To do so, you need to create a dedicated Microsoft Teams alert source in ilert.

1. In upper menu of ilert interface, go to **Alert sources** --> **Alert sources** and click on **Create new alert source.**
2. Select **Microsoft Teams** as the alert source type, give it a name, select an escalation policy, and click on **Create** button.
3. In the next screen, click on the **Microsoft Teams settings** tab to configure Microsoft Teams team, where this alert source should be available, and where users should be able to look up who is on-call.

<figure><img src="../../.gitbook/assets/03 ms teams oncall.png" alt=""><figcaption></figcaption></figure>

Now, any Microsoft Teams user in your workspace will be able to use the on-call lookup feature from the configured channels.&#x20;

{% embed url="https://www.youtube.com/watch?v=_EzV_pEVvBc" %}
Check out our step-by-step tutorials on Youtube
{% endembed %}
