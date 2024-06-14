---
description: Configure how ilert should notify you.
---

# Notification settings

Each user defines in their profile how they will be notified about alerts, incidents and on-call shifts. To manage your notification settings, click on your avatar in the top right and go to **notification settings**.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-24 at 17.08.08.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
A user with admin rights can also change the notification settings for other users.&#x20;
{% endhint %}

Before you can receive notifications from ilert, your need to:

1. Add notification contacts (such as an email address or phone number) and activate support channels (e.g. SMS, WhatsApp)
2. Define notification rules, e.g. "for every high prio alert, first send me an SMS and call me after 5 minutes, if I do not respond to the alert".

### Add notification contacts and activate supported channels

ilert lets you add email addresses, phone numbers and push notification devices that you can use to setup notification channels.

{% hint style="info" %}
ilert creates one email contact based on your login email by default. Push notification devices will appear automatically once you login to ilert via one of our mobile apps for Android or iOS.
{% endhint %}

To add a notification contact, click on the **Add email** or **Add phone number** link.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-24 at 17.19.26.png" alt=""><figcaption></figcaption></figure>

Once you have added a notification contact, a list of supported notification channels will appear. Before you can send notifications to a contact through a channel, you need to activate the respective notification channel.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-24 at 17.24.57 (1).png" alt=""><figcaption></figcaption></figure>

When you activate a notification channel, ilert will ask you for a verification code that will be sent to the respective channel.

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Activating a phone number via SMS will also activate phone call notifications.
{% endhint %}

The process for activating a notification channel differs from channel to channel. Please follow the instructions provided during activation. ilert supports the following notification channels:

* Email
* SMS
* Phone calls
* iOS and Android push notification
* WhatsApp
* Telegram

Once activation was successful, you are able to test the notification channel by clicking on the **Send test notification** link.\
\
![](<../../.gitbook/assets/image (60).png>)

### Define notification rules

There are 5 different types of notification rules to configure:

<table data-header-hidden><thead><tr><th width="221">Category</th><th></th></tr></thead><tbody><tr><td>High priority alerts</td><td>notifies, when a high priority alert is assigned to the user (initially on alert creation, or when added as responder)</td></tr><tr><td>Low priority alerts</td><td>notifies, when a low priority alert is assigned to the user (initially on alert creation, or when added as responder)</td></tr><tr><td>Alert status updates</td><td>notifies, when user is already assigned to an alert and the alert status changes (e.g. another user accepts the alert)</td></tr><tr><td>Incident notifications</td><td>notifies, when user is added to an incident as a subscriber (initially on incident creation, or when added manually)</td></tr><tr><td>On-call notifications</td><td>notifies at the given point of time before the user is being on-call</td></tr></tbody></table>



To define notification rules

1.  Choose a notification type (e.g. **High priority alerts**), expand the section and click on **Add notification rule**\


    <figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>
2. Configure the notification rule by selecting a contact and channel  and click on **Save**.

For alert notification rules, you will be able to set delays between notifications, like the following:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Above rules will first notify you via Push (on all push devices), then (after 3 minutes) ilert will send you an SMS, unless you respond to the alert within 3 minutes. In this case, it will not notify you via SMS.

Alert notifications in ilert are bi-directional, that is, you can respond to a notification using the same channel on which you were notified (without logging into ilert), e.g. by replying to an SMS.

You have the following response options:

1. Acknowledge the alert
2. Mark the alert as resolved
3. Escalation to the next user in the alert's escalation policy
