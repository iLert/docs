---
description: >-
  This guide explains how to configure your push notification preferences for
  Android devices.
---

# Android Push Notification DND Configuration

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
* select a custom sound (if desired) for **High** and **low priority** notifications (make sure that the radio button in the sound list is selected, just playing back the sound won't change your settings)
* ensure you have enabled the toggle for **Critical alerts for high priority**
* adjust **Critical alerts volume** to your needs

When enabling **Critical alerts for high priority** you may be prompted to allow the ilert app to override DND settings on your device. By clicking on **Go to settings** you will be redirected to the device settings page. Search for **ilert** and allow DND overrides for the app.

{% hint style="warning" %}
Note: when allowing DND overrides, the first notification received will **disable DND mode** and also set your system sound mode to **Sound,** without reverting it back to the previous state.
{% endhint %}

## FAQ

**Why is my DND mode turned off, and my device's sound mode set to Sound?**

To be able to deliver critical alerts, ilert ensures those notifications are always heard. Unfortunately, Android is quite limited in enabling this functionality and does not provide a possibility to revert sound/DND settings to previous states.
