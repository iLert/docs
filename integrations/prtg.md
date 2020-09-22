---
title: PRTG Network Monitor Integration
seoTitle: >-
  iLert: PRTG Network Monitor Integration for Alerting | Incident Response |
  Uptime
description: >-
  The iLert PRTG Network Monitor Integration helps you to easily connect iLert
  with PRTG Network Monitor.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# PRTG Network Monitor Integration

With PRTG integration, you can easily integrate PRTG with iLert and extend your existing PRTG monitoring with SMS, push and voice notifications as well as on-call schedules from iLert.

## In iLert: Create PRTG alert source <a id="create-alarm-source"></a>

1. Go to **Alert sources** and click on **Add a new alert source**

2. Enter a name for your alert source \(e.g. "PRTG"\) and select your desired escalation policy.

3. In the Integration Type field, select **PRTG Network Monitor** and click on Save

![](../.gitbook/assets/screenshot-2020-09-22-at-08.53.15.png)

5. On the next page,  **PRTG URL** and **PRTG Postdata** fields will be displayed.  You will need those two fields in the PRTG setup.

![](../.gitbook/assets/screenshot-2020-09-22-at-09.04.21.png)

## In PRTG: Create new notification <a id="create-notification"></a>

1. Got to notification settings

![](../.gitbook/assets/pg3.png)

2. Add a new notification

3. As notification method select **Execute HTTP ACTION**

4. Copy the **URL** and **Postdata** fields from the iLert alert source. The API key is included in Postdata.

![](../.gitbook/assets/pg4.png)

5. Click on **Save**

6. Next we will use the newly created iLert notification method in PRTG. To do this, switch to the root group in the device overview and select the "Notifications" tab.

![](../.gitbook/assets/pg5.png)

7. Create the following status triggers. **Note**: We recommend the option "repeat this every 5 minutes" in case your internet connection goes down.

![](../.gitbook/assets/pg6.png)

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as the condition of a sensor in PRTG is OK again, the associated incident is resolved in iLert.

**What if an alert is acknowledged in PRTG, is the associated incident also acknowledged in iLert?**

No, in PRTG it is unfortunately not possible to send notifications for acknowledgements.

**What if my internet connection is interrupted? Are the events generated in PRTG lost?**

No, events will not be lost if you enable the "repeat every x minutes" option in PRTG \(see above\). In addition, we recommend that you monitor your Internet connection with an external monitoring service \(e.g. using iLert's uptime monitoring\). You can send these alerts to iLert again.

**Can I link PRTG to multiple alert sources in iLert?**

Yes, create multiple iLert notifications in PRTG. You can then associate them with objects in the PRTG object hierarchy.

**The integration does not work. How do I find the mistake?**

If you can not find the error, please contact our support at [support@ilert.com](support@ilert.com).

