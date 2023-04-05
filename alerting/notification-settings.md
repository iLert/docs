---
description: Configure how ilert should notify you.
---

# Notification settings

In ilert, each user defines in their profile how they will be notified about an alert. A user with admin rights can also maintain the notification settings for other users. Right now ilert supports the following notification channels:

* Email
* SMS
* Phone calls
* iPhone and Android push notification
* WhatsApp
* Telegram

### Contacts

Before getting notifications from ilert you have to configure one or more notification channels, meaning contacts or push notification devices.

{% hint style="info" %}
ilert always creates one email contact based on your login email by default.
{% endhint %}

#### Setup a contact

1. Click your user icon on the top right and select **Notification settings**, navigate to section **Contact information**
2.  Click on **Add email** or **Add phone number** and enter an email or a phone number respectively\


    <figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>
3.  Choose a notification channel, click on **Activate** and follow the activation steps to enable the notification channel for this contact\


    <figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Push notification devices are registered automatically when first logging in to your account in the ilert mobile app.&#x20;
{% endhint %}

After the activation was successful you are able to test the notification channel by sending a test notification.\
\
![](<../.gitbook/assets/image (60).png>)

### Notifications

Notifications in ilert are bi-directional, that is, you can respond to a notification using the same channel on which you were notified (without logging into ilert).

You have the following response options:

1. Acknowledge the alert
2. Mark the alert as resolved
3. Escalation to the next user

You can find a list of caller IDs for sms and phone calls [here](phone-numbers/#sms-alerts).

#### Configure notifications

There are 5 different types of notifications to configure:

| High priority alerts   | notifies, when a high priority alert is assigned to the user (initially on alert creation, or when added as responder) |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Low priority alerts    | notifies, when a low priority alert is assigned to the user (initially on alert creation, or when added as responder)  |
| Alert status updates   | notifies, when user is already assigned to an alert and the alert status changes (e.g. another user accepts the alert) |
| Incident notifications | notifies, when user is added to an incident as a subscriber (initially on incident creation, or when added manually)   |
| On-call notifications  | notifies at the given point of time before the user is being on-call                                                   |

1. Click your user icon on the top right and select **Notification settings**, navigate to section **Notification rules**
2.  Choose a notification type, expand the section and click on **Add notification rule**\


    <figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>
3. Configure the notification rule and save your changes
