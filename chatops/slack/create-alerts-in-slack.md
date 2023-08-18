---
description: Use Slack as an alert source
---

# Create alerts in Slack

{% hint style="info" %}
**Connect your Slack workspace with ilert first**

Before you proceed, please make sure that a global admin has connected your Slack workspace with your ilert account (as described in our [integration for Slack guide](./))
{% endhint %}

Our integration for Slack lets you create alerts directly within Slack and streamlines your incident management process, making it even easier for your team and stakeholders to report incidents.

### Overview

There are two ways to configure the alert creation feature in Slack:

1. **Restrict to Slack users with an ilert account**: This mode doesn't require any additional configuration other than installing our Slack app (as described in the [integration for Slack guide](./)).&#x20;
2. **Allow any Slack user to create an alert:** This method requires the creation of a dedicated Slack alert source in ilert and allows you to control the Slack channels where users will be able to create an alert, to which escalation policy the alert is routed to and what [notification priority](../../alerting/alert-sources.md#customise-your-alerts-with-notification-priority) is used.&#x20;

### Option 1: Restrict to Slack users with an ilert account

Once you have our Slack app installed in your Slack workspace, any Slack user with an ilert account can create an alert from any channel by invoking the the `/il-alert` slash command.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

The user's permissions in ilert will be taken into account. Therefore, they will only see alert sources and escalation policies to which they have access to.&#x20;

### Option 2: A**llow any Slack user to create an alert**

You can let any Slack user (even if they don't have an ilert account) create an alert from Slack. In order to control which teams they will be able to alert and control notification priority, you need to create a dedicated Slack alert source in ilert.

1. Go to Alert sources --> Alert sources and click on **Create new alert source**
2. Select **Slack** as the alert source type, give it a name, e.g. _Slack alerts from channel xyz_, select an escalation policy and click on **Create**.
3.  In the next screen, click on the **Slack settings** tab to configure

    * the Slack channels from where Slack users should be able to create alerts
    * and the escalation policies that users can select from





    <figure><img src="../../.gitbook/assets/Screenshot 2023-06-21 at 12.00.44.png" alt=""><figcaption></figcaption></figure>
4. Now any Slack user in your workspace will be able to create alerts from the configured channels. They will be limited to the pre-configured escalation policies and the alert creation will take into account whatever is configured in the alert source (e.g. notification priority and other alert actions). To create a new alert, use the following command in any of the configured channel&#x20;

```
/il-alert
```

<div align="center">

<figure><img src="../../.gitbook/assets/image (1) (6).png" alt="" width="375"><figcaption></figcaption></figure>

</div>

## FAQ

#### **I have received following error messages:** There is no Slack alert source configured for this channel in ilert, which is required to enable alert creation for Slack users without an ilert account.

If an unauthorized user tries to create a new alert from Slack, the ilert bot for Slack requires the channel to be set in a Slack alert source in ilert. To fix this issue please follow the steps in [Option 2](create-alerts-in-slack.md#option-2-allow-any-slack-user-to-create-an-alert).

If your ilert bot for Slack has no permission. Please [reauthorize](./#re-authorizing-your-slack-workspace) your bot.\
