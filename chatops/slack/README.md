---
description: Post alerts to Slack or create alerts within a Slack channel
---

# Integration for Slack

Slack is a popular instant messaging service for team communication and collaboration. With the integration for Slack you can receive messages about alerts in Slack channels and respond within Slack or you can create alerts from within a Slack channel.

## Select your use case <a href="#in_slack" id="in_slack"></a>

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Receive and respond to alerts in Slack</strong></td><td>Receive and acknowledge alerts in a Slack channel of your choice.</td><td><a href="post-alerts-to-a-slack-channel.md">post-alerts-to-a-slack-channel.md</a></td></tr><tr><td><strong>Create alerts within a Slack channel</strong></td><td>Use Slack as an alert source and let Slack users create alerts from Slack.</td><td><a href="create-alerts-in-slack.md">create-alerts-in-slack.md</a></td></tr><tr><td><strong>Lookup who is on-call in Slack</strong></td><td>Lookup who is on-call right from Slack using our <code>/il-oncall</code> Slash command.</td><td><a href="lookup-who-is-on-call.md">lookup-who-is-on-call.md</a></td></tr><tr><td><strong>Create dedicated alert channels</strong></td><td>Create dedicated Slack channels from ilert to collaborate on major incidents.</td><td><a href="create-a-dedicated-slack-channel-for-an-existing-alert.md">create-a-dedicated-slack-channel-for-an-existing-alert.md</a></td></tr></tbody></table>

## Authorize your Slack workspace <a href="#in_ilert" id="in_ilert"></a>

{% hint style="info" %}
**Admin permission required**

You need to have global **Admin** privileges to set up the integration in ilert.
{% endhint %}

1\. Click on the gear icon ⚙ → **Connectors**

![](<../../.gitbook/assets/Notification_Center (6).png>)

2\. Click on the **Slack Workspace Integration**

![](<../../.gitbook/assets/iLert (106).png>)

3\. Click on the **Authorize** button

![](<../../.gitbook/assets/iLert (105).png>)

4\. You will be forwarded to Slack. If you are not already logged in to Slack, please log in and **allow ilert to access your Slack workspace**.

5\. You will be redirected to ilert. When you see a success message, you're done setting up. You can now add alert sources to a channel in Slack.

![](../../.gitbook/assets/sl4.png)

<details>

<summary>Re-authorizing your Slack Workspace</summary>

You **may** need to re-authorize the bot for your Slack workspace in case new features of the bot require additional permissions e.g. alert actions or automatic user mapping.

Click on the gear icon ⚙ → **Connectors**, then click on the **Slack Workspace Integration** and on the **"Re-authorize Slack"** button

<img src="../../.gitbook/assets/iLert (101).png" alt="" data-size="original">

</details>

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Slack Workspaces to one ilert account?**

No, only one Slack Workspace can be linked to an ilert account.

**Can multiple ilert accounts be linked to the same Slack workspace?**

No, a Slack workspace can only be linked to one ilert account at a time.&#x20;

