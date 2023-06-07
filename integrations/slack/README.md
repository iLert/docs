---
title: Slack Integration
seoTitle: 'iLert: Slack Integration for Alerting | Incident Response | Uptime'
date: '2018-12-29T05:02:05.000Z'
weight: 1
description: The ilert Slack Integration helps you to easily connect ilert with Slack.
---

# Slack Integration

Slack is a popular instant messaging service for team communication and collaboration. With the Slack integration you receive messages about alerts in Slack channels and can accept and resolve alerts within Slack.

## In ilert: Authorize your Slack workspace <a href="#in_ilert" id="in_ilert"></a>

{% hint style="info" %}
**Admin permission required**

You need to have global **Admin** privileges to set up the integration in ilert.
{% endhint %}

1\. Click on the gear icon ⚙ → **Connectors**

![](<../../.gitbook/assets/Notification\_Center (6).png>)

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

## Select your use case <a href="#in_slack" id="in_slack"></a>

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td></td><td><strong>Post alerts to a Slack channel</strong></td><td></td><td></td></tr><tr><td></td><td><strong>Create alerts within a Slack channel</strong></td><td></td><td><a href="create-alerts-in-slack.md">create-alerts-in-slack.md</a></td></tr></tbody></table>

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Slack Workspaces to one ilert account?**

No, only one Slack Workspace can be linked to an ilert account.

