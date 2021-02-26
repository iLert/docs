---
description: Setting up your call routing number to fit your hotline needs.
---

# Getting started with call routing

You can find your call routing numbers in your account in the call routing services section.

![](../.gitbook/assets/image%20%2818%29.png)

{% hint style="success" %}
Each call routing number has a unqiue phone number that will be set up for you by your account manager. You may have mulitple call routing numbers, we support different countries and try to provide you with a number that fits best to your local needs.
{% endhint %}

### General settings

When your number has been added to your account, you may configure it to your liking.

![](../.gitbook/assets/image%20%2815%29.png)

The general settings area allows you to configure a **name** \(that will be read out to your on-call staff, or as we call them **agents**, whenever they receive a call\) as well as the **language** and **greeting** of your call routing number.

The greeting that a caller of your number hears when they are calling is by default a combination of your provided **greeting** and the automatically generated **IVR menu**, that consists of the different routing options which you have chosen. A preview is always generated for you up front.

![](../.gitbook/assets/image%20%2817%29.png)

You may choose the option `Only read this greeting..` to fully customise the greeting to your liking and disable the auomated addition of the IVR menu.

### Routing configuration

When calling your number, your callers will be able to choose a route using **vocal** or **digit** input to choose the routing target where they want to be routed to. Per default iLert will take every user in the target escalation policy \(either directly or from a nested on-call schedule\) and call them one after another, while waiting for an agent to accept the incoming call.

When picking up the call, the agent may decide to accept or decline the call. If the agent does not pick up the call or declines, iLert will automatically call the next user in the policy.

We offer an additional setting for Premium and Enterprise customers called `Simultaneous calling` which will call all agents in the escalation policy in parallel, connecting the caller to the first agent that picks up and accepts.

{% hint style="info" %}
Please note that escalation times in escalation policies are skipped for policies that are used as routing options - as a call always happens in real time. If an agent declines a call, the next agent in the policy will be called asap.
{% endhint %}

### Voicemail setup

If no user is left and no voicemail has been configured \(see below\) the caller will hear a message that no one is currently available and the call we be ended. The incident that has been created for this incoming call will be escalated once again to the targeted escalation policy.

![](../.gitbook/assets/image%20%2811%29.png)

Yet if a voicemail is present instead, the caller will be redirected to the voicemail. In case he leaves a voicemail, the voicemail will be attached to the incident of the incoming call and escalated once again to the targeted escalation.

### Whats next?

You may also like the advanced configuration options for call routing numbers:

* [Routing calls based on support hours](routing-calls-based-on-support-hours/)
* [Handling automated incoming voice calls](handling-calls-from-automated-voice-calls.md)
* [Managing call routing incidents](managing-call-routing-incidents.md)
* [Adding webhooks and outbound chat messages](adding-webhooks-and-outbound-chat-messages.md)





