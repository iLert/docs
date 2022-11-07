---
description: Reach the right on-call responder immediately by calling a phone number
---

# Getting started with call routing

You can find your call routing numbers in the navigation bar at the top under **Alert sources** --> **Call routing**.

<figure><img src="../.gitbook/assets/image (16) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**How to get a call routing number?**

Each call routing number has a unique phone number that will be set up for you by our support. You may have multiple call routing numbers from different countries and cities. Please contact our support at support@ilert.com and we will provision a phone number that fits best to your local needs.
{% endhint %}

## General settings

Once we have added a phone number to your account, you can configure its IVR menu, routing options, voicemail settings and more.

![](<../.gitbook/assets/image (8) (1).png>)

The general settings area allows you to configure a **name** as well as the **language** and **greeting** of your call routing number. The **name** will be read out to your on-call staff whenever they receive a call.

The greeting that a caller of your number hears when they are calling is by default a combination of your provided **greeting** and the automatically generated **IVR menu**, that consists of the different routing options which you have chosen. A preview for the entire greeting is generated for you up front.&#x20;

![](<../.gitbook/assets/Screenshot 2021-10-28 at 09.23.45.png>)

You may choose the option `Only read this greeting..` to fully customise the greeting to your liking and disable the automated addition of the IVR menu. This is useful if you don't want to include the names of your escalation policies in the IVR menu. You may also [upload a custom audio file](uploading-custom-audio-responses.md) for your greeting and hold music.

## Routing configuration

When calling your number, your callers will be able to choose a routing target using **voice** or **digit** input. A routing target is an escalation policy and by default, iLert will call every user in the target escalation policy (either directly or from a nested on-call schedule) one after another, while waiting for an agent to accept the incoming call.

When picking up the call, the agent may decide to accept or decline the call. If the agent does not pick up the call or declines, iLert will automatically call the next user in the policy.

{% hint style="info" %}
**Escalation timeouts in the escalation policy will be ignored**

Please note that escalation timeouts in escalation policies are skipped for policies that are used as routing options - as a call always happens in real time. If an agent declines a call, the next agent in the policy will be called immediately, withouth waiting for the configured escalation timeout to elapse.
{% endhint %}

### Randomly selecting the user to call

If you would like to randomly distribute incoming calls to a group of people, you can include multiple responders on an escalation rule.&#x20;

<figure><img src="../.gitbook/assets/Screen Shot 2022-09-02 at 10.44.08.png" alt=""><figcaption></figcaption></figure>

In the above configuration, iLert will first randomly select someone from the first escalation rule (Andreas, Cathy or Roman), if that selected person doesn't accept the call, iLert will proceed with the second escalation rule, which is the user on-call according to the SRE Team Secondary schedule.

## Voicemail setup

If no user is left and no voicemail has been configured (see below) the caller will hear a message that no one is currently available and the call will be ended. The alert that has been created for this incoming call will be escalated once again to the targeted escalation policy using regular alert notification and escalation rules.

![](<../.gitbook/assets/image (10).png>)

Yet if a voicemail is present instead, the caller will be redirected to the voicemail. In case she leaves a voicemail, the voicemail will be attached to the alert of the incoming call and escalated once again to the targeted escalation.

## Advanced configuration

* [Routing calls based on support hours](routing-calls-based-on-support-hours.md)
* [Handling automated incoming voice calls](voicemail-only-mode.md)
* [Managing call routing alerts](managing-call-routing-incidents.md)
* [Adding webhooks and outbound chat messages](adding-webhooks-and-outbound-chat-messages.md)
