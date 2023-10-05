---
description: Lookup who is on-call right from Slack using our /il-oncall Slash command.
---

# Lookup who is on-call

{% hint style="info" %}
**Connect your Slack workspace with ilert first**

Before you proceed, please make sure that a global admin has connected your Slack workspace with your ilert account (as described in our [integration for Slack guide](./))
{% endhint %}

### Overview

The `/il-oncall` Slash command lets you lookup who is on-call from any Slack channel. There are two ways to configure the on-call lookup feature in Slack:

1. **Restrict lookup to Slack users with an ilert account**: This mode doesn't require any additional configuration other than installing our Slack app (as described in the [integration for Slack guide](./)).&#x20;
2. **Allow any Slack user to lookup who is on-call:** This method requires the creation of a dedicated Slack alert source in ilert and allows you to control the Slack channels where users will be able to lookup who is on-call. One way to use this feature is for example to configure the lookup for every team channel and letting any Slack user use the `/il-oncall` command to lookup the on-call responder for that team, without having to know the names of the escalation policy for that team.

### Option 1: Restrict to Slack users with an ilert account

Once you have our Slack app installed in your Slack workspace, any Slack user with an ilert account can lookup the on-call responder for any escalation policy or alert source by invoking the the `/il-oncall` slash command.

<figure><img src="../../.gitbook/assets/image (75).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (78).png" alt="" width="563"><figcaption></figcaption></figure>

The user's permissions in ilert will be taken into account. Therefore, they will only see alert sources and escalation policies to which they have access to.&#x20;

### Option 2: A**llow any Slack user to lookup who is on-call**

You can let any Slack user (even if they don't have an ilert account) lookup who is on-call from within a Slack channel. You need to create a dedicated Slack alert source in ilert in order to control where the lookup is available and which escalation policies should be used for the lookup.&#x20;

1. Go to Alert sources --> Alert sources and click on **Create new alert source**
2. Select **Slack** as the alert source type, give it a name, e.g. _Slack alerts from channel xyz_, select an escalation policy and click on **Create**.
3.  In the next screen, click on the **Slack settings** tab to configure

    * the Slack channels from where Slack users should be able lookup who is on-call
    * and the escalation policies that will be used for the lookup



    <figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>
4. Save your changes.
5. Now any Slack user in your workspace will be able to lookup who is on-call from the configured channels. The lookup will be limited to the pre-configured escalation policies. To lookup who is on-call, use the following the slash command in the configured Slack channel

```
/il-oncall
```

<figure><img src="../../.gitbook/assets/pika-1692781954797-2x (1).png" alt=""><figcaption></figcaption></figure>
