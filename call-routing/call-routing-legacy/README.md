# Call routing (legacy)

{% hint style="info" %}
### Legacy call routing

This documentation covers the legacy version of our call routing feature. It is only available to customers who purchased the call routing add-on before May 2024.
{% endhint %}

### General settings

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-10 at 13.51.55.png" alt=""><figcaption></figcaption></figure>

* **Name:** The name of the call routing number will be read out to the on-call responder when ilert tries to connect a caller with an on-call responder, e.g. "This is **Emergency Hotline**. You have a caller on hold. Press any key or say continue to connect."
* **Language:** We will use the language to read your greeting message.
*   **Only read this greeting...:** ilert dynamically creates the IVR menu based on your routing configuration. Enable this option if you want to customize the IVR and not use the names of the escalation policies. A preview for the entire greeting is generated for you up front.\


    ![](<../../.gitbook/assets/Screenshot 2021-10-28 at 09.23.45.png>)
* **Hold music:** You may optionally [upload a custom audio file](uploading-custom-audio-responses.md) for your greeting and hold music.

### Routing configuration

When calling your number, your callers will be able to choose a routing target using **voice** or **digit** input. A routing target is an escalation policy and by default, ilert will call every user in the target escalation policy (either directly or from a nested on-call schedule) one after another, while waiting for an agent to accept the incoming call.

When picking up the call, the agent may decide to accept or decline the call. If the agent does not pick up the call or declines, ilert will automatically call the next user in the policy.

{% hint style="info" %}
**Escalation timeouts in the escalation policy will be ignored**

Please note that escalation timeouts in escalation policies are skipped for policies that are used as routing options - as a call always happens in real time. If an agent declines a call, the next agent in the policy will be called immediately, withouth waiting for the configured escalation timeout to elapse.
{% endhint %}

#### Randomly selecting the user to call

If you would like to randomly distribute incoming calls to a group of people, you can include multiple responders on an escalation rule.

<figure><img src="../../.gitbook/assets/Screen Shot 2022-09-02 at 10.44.08.png" alt=""><figcaption></figcaption></figure>

In the above configuration, ilert will first randomly select someone from the first escalation rule (Andreas, Cathy or Roman), if that selected person doesn't accept the call, ilert will proceed with the second escalation rule, which is the user on-call according to the SRE Team Secondary schedule.

### Voicemail setup

If no user is left and no voicemail has been configured (see below) the caller will hear a message that no one is currently available and the call will be ended. The alert that has been created for this incoming call will be escalated once again to the targeted escalation policy using regular alert notification and escalation rules.

![](<../../.gitbook/assets/image (10).png>)

Yet if a voicemail is present instead, the caller will be redirected to the voicemail. In case she leaves a voicemail, the voicemail will be attached to the alert of the incoming call and escalated once again to the targeted escalation.

## Advanced configuration

* [Routing calls based on support hours](routing-calls-based-on-support-hours.md)
* [Handling automated incoming voice calls](voicemail-only-mode.md)
* [Managing call routing alerts](managing-call-routing-incidents.md)
* [Adding webhooks and outbound chat messages](adding-webhooks-and-outbound-chat-messages.md)
* [Uploading custom audio responses](uploading-custom-audio-responses.md)
