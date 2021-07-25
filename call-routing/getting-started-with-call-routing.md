---
description: Reach the right on-call responder immediately by calling a phone number
---

# Getting started with call routing

You can find your call routing numbers in your account in the call routing services section.

![](../.gitbook/assets/image%20%2818%29.png)

{% hint style="info" %}
**How to get a call routing number?**

Each call routing number has a unique phone number that will be set up for you by our support. You may have multiple call routing numbers from different countries and cities. Please contact our support at support@ilert.com and we will provision a phone number that fits best to your local needs.
{% endhint %}

### General settings

Once we have added a phone number to your account, you can configure its IVR menu, routing options, voicemail settings and more.

![](../.gitbook/assets/image%20%2815%29.png)

The general settings area allows you to configure a **name** as well as the **language** and **greeting** of your call routing number. The **name** will be read out to your on-call staff whenever they receive a call. 

The greeting that a caller of your number hears when they are calling is by default a combination of your provided **greeting** and the automatically generated **IVR menu**, that consists of the different routing options which you have chosen. A preview is always generated for you up front.

![](../.gitbook/assets/image%20%2817%29.png)

You may choose the option `Only read this greeting..` to fully customise the greeting to your liking and disable the automated addition of the IVR menu. This is useful if you don't want to include the names of your escalation policies in the IVR menu.

### Routing configuration

When calling your number, your callers will be able to choose a route using **voice** or **digit** input to choose the routing target where they want to be routed to. Per default iLert will take every user in the target escalation policy \(either directly or from a nested on-call schedule\) and call them one after another, while waiting for an agent to accept the incoming call.

When picking up the call, the agent may decide to accept or decline the call. If the agent does not pick up the call or declines, iLert will automatically call the next user in the policy.

We offer an additional setting for Premium and Enterprise customers called `Simultaneous calling` which will call all agents in the escalation policy in parallel, connecting the caller to the first agent that picks up and accepts.

{% hint style="info" %}
Please note that escalation times in escalation policies are skipped for policies that are used as routing options - as a call always happens in real time. If an agent declines a call, the next agent in the policy will be called immediately.
{% endhint %}

### Voicemail setup

If no user is left and no voicemail has been configured \(see below\) the caller will hear a message that no one is currently available and the call will be ended. The incident that has been created for this incoming call will be escalated once again to the targeted escalation policy using regular incident notification and escalation rules.

![](../.gitbook/assets/image%20%2811%29.png)

Yet if a voicemail is present instead, the caller will be redirected to the voicemail. In case she leaves a voicemail, the voicemail will be attached to the incident of the incoming call and escalated once again to the targeted escalation.

### Advanced configuration

* [Routing calls based on support hours](routing-calls-based-on-support-hours/)
* [Handling automated incoming voice calls](handling-calls-from-automated-voice-calls.md)
* [Managing call routing incidents](managing-call-routing-incidents.md)
* [Adding webhooks and outbound chat messages](adding-webhooks-and-outbound-chat-messages.md)





