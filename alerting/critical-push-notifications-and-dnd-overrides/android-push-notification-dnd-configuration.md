---
description: >-
  This guide explains how to configure your push notification preferences for
  Android devices.
---

# Android Push Notification Configuration

{% hint style="success" %}
Note: this guide is meant for Android users only.
{% endhint %}

## Prerequisite

Make sure that you have installed and logged into the ilert mobile app on your device. Which will automatically generate and store a push token for your device in your ilert account.

Under your **profile** settings (in web or mobile app) navigate to **Notification settings** and select Android push notifications for any desired notification option.

## Overriding DND settings for your device

* open the **Navigation** in your app (top left icon)
* tap on the cog icon (top right in navigation) to open the **Settings** menu
* tap on Push notification settings
* select a custom sound (if desired) for **High** and **low priority** notifications (make sure that the radio button in the sound list is selected, just playing back the sound wont change your settings)
* ensure you have enabled the toggle for **Critical alerts for high priority**

### Enabling DND for sound channels

Now onto the tough part, in Android you will have to enable DND additional per sound channel. Sadly Android Applications are not always allowed to configure these directly.

* open your devices **Settings**
* go to **Apps & notifications**
* then on **App info**
* search for **iLert** in the list and tap on it
* tap on **Notifications**
* tap on the **sound channel e.g. merrychristmas** for the audio that you have selected in the ilert app for your high and low priority notifications - or do it for all in the list
* ensure the top selection is set on **Alerting** and not on _Silent_
* tap on **Advanced**
* enable the toggle for **Override Do Not Disturb** (probably also ensure the rest of the options is enabled to, but that should be their default state)

{% hint style="warning" %}
Note: these settings are only offering overrides for the specific DND (do not disturb mode) in Android. If you switch your Android phone to silent mode (**Calls and notifications are muted**) overrides will not work and you will not hear a sound.
{% endhint %}
