---
description: >-
  The ilert Telegram outbound integration helps you to send alert notifications
  to Telegram 1:1 chats and group chats.
---

# Telegram Integration

[Telegram](https://telegram.org/) is a cloud-based instant messaging app that allows users to send messages, photos, videos, and files to individuals or groups. It is known for its emphasis on privacy and security, offering end-to-end encryption for secret chats.

{% hint style="info" %}
To use our Telegram outbound integration, a valid phone number contact in the notification settings in ilert is required. Simply add a phone number by following [our notification settings guide](https://docs.ilert.com/alerting/notification-settings#add-notification-contacts-and-activate-supported-channels).
{% endhint %}

## In ilert: Activate Telegram in the notification settings <a href="#alarm-sources" id="alarm-sources"></a>

1. Click on the **avatar icon -> Notification settings**.

<figure><img src="../../.gitbook/assets/ilert-1.png" alt="" width="563"><figcaption></figcaption></figure>

2. In **Phone number contacts,** click on **Activate** next to Telegram.

<figure><img src="../../.gitbook/assets/ilert-2.png" alt="" width="563"><figcaption></figcaption></figure>

3. Copy the code that was generated in the pop-up or click on **Verify**.

<figure><img src="../../.gitbook/assets/ilert-3.png" alt="" width="563"><figcaption></figcaption></figure>

4. Now click on **Send Message**.

<figure><img src="../../.gitbook/assets/browser-1.png" alt="" width="563"><figcaption></figcaption></figure>

5. You will then be verified.
6. Send a test notification to test your connection by clicking on **Send test notification.**

<figure><img src="../../.gitbook/assets/ilert-4.png" alt="" width="563"><figcaption></figcaption></figure>

## Optional: Activate the ilert connection in Telegram manually <a href="#alarm-sources" id="alarm-sources"></a>

To manually activate your Telegram connection, follow these steps.

1. Search for '@ilert\_bot' and open a new chat.

<figure><img src="../../.gitbook/assets/telegram-4.png" alt="" width="563"><figcaption></figcaption></figure>

2. Enter the previously generated verification code into the Chat.

<figure><img src="../../.gitbook/assets/telegram-1.png" alt="" width="561"><figcaption></figcaption></figure>

## In Telegram: ilert alert action in Telegram groups <a href="#alarm-sources" id="alarm-sources"></a>

1. Add our '@ilert\_actions\_bot' into a group of choice.
2. If the '@ilert\_actions\_bot' got invited successfully, you will receive a message with a code starting with a dash("-"). Copy this code and proceed to the [next step](telegram.md#alarm-sources-3).

<figure><img src="../../.gitbook/assets/telegram-3.png" alt="" width="563"><figcaption></figcaption></figure>

## In ilert: Create a new Telegram alert action <a href="#alarm-sources" id="alarm-sources"></a>

1. Click on **Alert sources -> Alert actions**.

<figure><img src="../../.gitbook/assets/ilert-5.png" alt="" width="563"><figcaption></figcaption></figure>

2. Now click on **Create new alert action**.

<figure><img src="../../.gitbook/assets/ilert-6.png" alt="" width="563"><figcaption></figcaption></figure>

3. Search for **Telegram** in the alert actions wizard and select our Telegram integration.

<figure><img src="../../.gitbook/assets/ilert-7.png" alt="" width="563"><figcaption></figcaption></figure>

4. Enter a **Name** and proceed to the next step.

<figure><img src="../../.gitbook/assets/ilert-8.png" alt="" width="563"><figcaption></figcaption></figure>

5. Choose some alert event filters for your alert action and click on **Next**.

<figure><img src="../../.gitbook/assets/ilert-9.png" alt="" width="563"><figcaption></figcaption></figure>

6. Now enter the **code** from [this step](telegram.md#alarm-sources-3) that you have received from our ''@ilert\_actions\_bot" in your Telegram group and click on **Done** to finish the setup.

<figure><img src="../../.gitbook/assets/ilert-10.png" alt="" width="563"><figcaption></figcaption></figure>
