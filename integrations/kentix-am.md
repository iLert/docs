---
description: >-
  The Kentix AlarmManager is the central Kentix alarm and management unit.
  MultiSensors are managed by the AlarmManager. The AlarmManager is installed in
  the server room or rack.
---

# Kentix AlarmManager

## Setup a new AlarmManager alert souce in iLert

![](<../.gitbook/assets/Screenshot 2020-08-19 at 10.13.37.png>)

Navigate to the alert sources tab in iLert and create a new alert source.

![](<../.gitbook/assets/Screenshot 2020-08-19 at 10.14.41.png>)

Select **Kentix AlarmManager** as integraiton type, configure according to your liking and save the new alert source.

![](<../.gitbook/assets/Screenshot 2020-08-19 at 10.15.46.png>)

Copy the provided url by the freshly created AlarmManager alert source, as we will need it later to create the a Webhook resource in the AlarmManager.

## Configuring Webhook in the AlarmManager

![](<../.gitbook/assets/Screenshot 2020-07-31 at 19.15.10.png>)

Login to your AlarmManager (_default: _[http://192.168.100.222](http://192.168.100.222)_ admin:password_)

### Creating a Webhook

![](<../.gitbook/assets/Screenshot 2020-07-31 at 19.16.46.png>)

On the side menu click on **Configuration** and choose the **Webhooks** tab.\
Click on the **plus icon** to create a new webhook.

![](<../.gitbook/assets/Screenshot 2020-07-31 at 19.18.40.png>)

Fill out all required fields as shown in the screenshot, paste your copied url from your iLert Kentix AlarmManager alert source, as well as the provided data payload template below:

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

![](<../.gitbook/assets/Screenshot 2020-07-31 at 19.19.39.png>)

Navigate to the root **dashboard** view (top left item in sidebar), choose the Alarmzone which you want to connecto to your iLert alert source. Click on the **cog** and and select **Edit**.

![](<../.gitbook/assets/Screenshot 2020-08-18 at 15.14.12.png>)

Scroll all the way down to the Alarmzone's **Webhooks** configuration.\
And click on the **plus icon** to create a new assignment.

![](<../.gitbook/assets/screenshot-2020-08-18-at-15.14.17 (1).png>)

It is important to choose **Alarmstate change** as alarm assignment otherwise the connection wont work properly.

## A word on the Kentix device <-> iLert alert relation

Each iLert alert source is connected to a Kentix AlarmManager Webhook.\
Which in fact are assigned to Alarmzones. You might created multiple alert sources and assign them to as many Alarmzones as you like.

Each device in a alarmzone will create its own alert for its alarms.\
However iLert will not create a new alert per alarm type if an ongoing alert of the same device is already open, instead the additional alarms are appended to the existing alert.

When all alarms of the device fall back to normal state, iLert will automatically resolve the opened alert.

![](<../.gitbook/assets/Screenshot 2020-08-18 at 17.18.47.png>)
