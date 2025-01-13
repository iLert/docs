---
description: >-
  The Kentix AlarmManager is the central Kentix alarm and management unit.
  MultiSensors are managed by the AlarmManager. The AlarmManager is installed in
  the server room or rack.
---

# Kentix AlarmManager

## In ilert: Create a Kentix AlarmManager alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Kentix AlarmManager** in the search field, click on the Kentix AlarmManager tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## Configuring Webhook in the AlarmManager

![](<../../.gitbook/assets/Screenshot 2020-07-31 at 19.15.10.png>)

Login to your AlarmManager (_default:_ [http://192.168.100.222](http://192.168.100.222) _admin:password_)

### Creating a Webhook

![](<../../.gitbook/assets/Screenshot 2020-07-31 at 19.16.46.png>)

On the side menu click on **Configuration** and choose the **Webhooks** tab.\
Click on the **plus icon** to create a new webhook.

![](<../../.gitbook/assets/Screenshot 2020-07-31 at 19.18.40.png>)

Fill out all required fields as shown in the screenshot, paste your copied url from your ilert Kentix AlarmManager alert source, as well as the provided data payload template below:

```
{
    "time": "$TIME$",
    "building": "$BUILDING_NAME$",
    "alarmzone": "$ALARMZONE_NAME$",
    "alarmzone-state": "$ALARMZONE_STATE$",
    "device": "$DEVICE_NAME$",
    "address": "$DEVICE_ADDRESS$",
    "temperature": "$TEMPERATURE_VALUE$",
    "temperature-alarm": "$TEMPERATURE_ALARM$",
    "humidity": "$HUMIDITY_VALUE$",
    "humidity-alarm": "$HUMIDITY_ALARM$",
    "dewpoint": "$DEWPOINT_VALUE$",
    "dewpoint-alarm": "$DEWPOINT_ALARM$",
    "fire": "$CO_VALUE$",
    "fire-alarm": "$CO_ALARM$",
    "intrusion": "$MOTION_VALUE$",
    "intrusion-alarm": "$MOTION_ALARM$",
    "vibration": "$VIBRATION_VALUE$",
    "vibration-alarm": "$VIBRATION_ALARM$",
    "input1": "$INPUT_VALUE[1]$",
    "input1-alarm": "$INPUT_ALARM[1]$",
    "input2": "$INPUT_VALUE[2]$",
    "input2-alarm": "$INPUT_ALARM[2]$",
    "connection": "$CONNECTION_VALUE$",
    "connection-alarm": "$CONNECTION_ALARM$",
    "latency": "$LATENCY_VALUE$",
    "latency-alarm": "$LATENCY_ALARM$",
    "extpower": "$EXTPOWER_VALUE$",
    "extpower-alarm": "$EXTPOWER_ALARM$"
}
```

Click on the save icon in the top right.

### Assigning Webhook to Alarmzone

![](<../../.gitbook/assets/Screenshot 2020-07-31 at 19.19.39.png>)

Navigate to the root **dashboard** view (top left item in sidebar), choose the Alarmzone which you want to connecto to your ilert alert source. Click on the **cog** and and select **Edit**.

![](<../../.gitbook/assets/Screenshot 2020-08-18 at 15.14.12.png>)

Scroll all the way down to the Alarmzone's **Webhooks** configuration.\
And click on the **plus icon** to create a new assignment.

![](<../../.gitbook/assets/screenshot-2020-08-18-at-15.14.17 (1).png>)

It is important to choose **Alarmstate change** as alarm assignment otherwise the connection wont work properly.

## A word on the Kentix device <-> ilert alert relation

Each ilert alert source is connected to a Kentix AlarmManager Webhook.\
Which in fact are assigned to Alarmzones. You might created multiple alert sources and assign them to as many Alarmzones as you like.

Each device in a alarmzone will create its own alert for its alarms.\
However ilert will not create a new alert per alarm type if an ongoing alert of the same device is already open, instead the additional alarms are appended to the existing alert.

When all alarms of the device fall back to normal state, ilert will automatically resolve the opened alert.

![](<../../.gitbook/assets/Screenshot 2020-08-18 at 17.18.47.png>)
