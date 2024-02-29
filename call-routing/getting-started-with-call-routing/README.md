---
description: Reach the right on-call responder immediately by calling a phone number
---

# Getting started with call routing

## **What is Call Routing?**

Call routing is an add-on in ilert, designed to ensure incoming phone calls and voicemails are efficiently directed to the appropriate on-call responder. Calls are routed via ilert's intricate on-call schedules and escalation policies. With call routing, you are assigned a static, dedicated phone number (either local or toll-free, subject to availability). This number then intelligently and dynamically routes calls or voicemails to the current on-call responder in ilert.

## Prerequisites

To access and utilize call routing, you must be on the Professional plan or a higher tier. Once you have purchased the call routing add-on, contact ilert support at support@ilert.com to activate a phone number in your account.

## Phone number availability

We offer local phone numbers around the world. Please click on a continent below to see  supported countries. For countries not listed below, please reach out to support@ilert.com to ask for availability.

<details>

<summary><strong>North America</strong></summary>

* United States
* Canada
* Barbados
* Dominican Republic
* El Salvador
* Jamaica
* Mexico
* Panama
* Puerto Rico

</details>

<details>

<summary>South America</summary>

* Argentina
* Chile
* Colombia
* Ecuador
* Grenada
* Brazil

</details>

<details>

<summary>Europe</summary>

* Austria
* Belgium
* Bosnia and Herzegovina
* Bulgaria
* Croatia
* Cyprus
* Czech Republic&#x20;
* Estonia
* France
* Germany
* Greece
* Hungary
* Ireland
* Italy
* Romania
* Slovenia
* Spain
* Switzerland
* Sweden
* United Kingdom
* Denmark
* Finland
* Netherlands
* Norway
* Poland

</details>

<details>

<summary>Asia</summary>

* Indonesia
* Israel
* Japan
* Macau
* Philippines
* Thailand

</details>

<details>

<summary>Oceania</summary>

* Australia
* New Zealand

</details>

<details>

<summary><strong>Africa &#x26; Middle East</strong></summary>

* Benin
* Ghana
* Kenya
* Mali
* Mauritius
* South Africa
* Sudan
* Tunisia
* Uganda

</details>

{% hint style="info" %}
**Phone number availability is subject to regulation**

Due to country-specific regulations, phone number provisioning may require identity documentation and location validation. Contact support@ilert.com to check availability in your desired locality.
{% endhint %}

## Configuration

Once a call routing number was provisioned from ilert support, you'll find your call routing numbers in the navigation bar at the top under **Alert sources** --> **Call routing**.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-10 at 13.48.38.png" alt=""><figcaption></figcaption></figure>

Clicking on a call routing number will open its configuration page, where you can configure the following:

1. **General settings** such as name, language, greeting message and hold music
2. **Routing configuration:** the IVR menu, [time-based routing](routing-calls-based-on-support-hours.md) and voicemail.
3. **Alert resolution behavior**

### General settings

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-10 at 13.51.55.png" alt=""><figcaption></figcaption></figure>

* **Name:** The name of the call routing number will be read out to the on-call responder when ilert tries to connect a caller with an on-call responder, e.g. "This is **Emergency Hotline**. You have a caller on hold. Press any key or say continue to connect."
* **Language:** We will use the language to read your greeting message.
*   **Only read this greeting...:** ilert dynamically creates the IVR menu based on your routing configuration. Enable this option if you want to customize the IVR and not use the names of the escalation policies. A preview for the entire greeting is generated for you up front.\


    ![](<../../.gitbook/assets/Screenshot 2021-10-28 at 09.23.45.png>)
* **Hold music:** You may optionally [upload a custom audio file](../uploading-custom-audio-responses.md) for your greeting and hold music.

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
