---
title: New Relic Integration
seoTitle: 'iLert: New Relic Integration for Alerting | Incident Response | Uptime'
date: '2018-12-29T05:02:05.000Z'
weight: 1
description: >-
  The iLert New Relic Integration helps you to easily connect iLert with New
  Relic.
---

# New Relic Integration

With New Relic Integration, you can easily integrate New Relic Alerts with iLert. So you can easily extend New Relic with SMS, Push and Voice alerts, as well as iLert rosters. Alerts are created in iLert and automatically closed when the problem is resolved. In addition, the alerts in iLert created by New Relic include bounce links to the respective Incident in New Relic.

## In iLert: Create New Relic alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. **Go to the alert sources tab** and click on the "Create new alert source" button
2. Assign name and select escalation chain
3. Select and save in the field Integration Type **New Relic**.

![](../../.gitbook/assets/nr1.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up in New Relic.

![](../../.gitbook/assets/nr2.png)

## In New Relic Alerts: Add Webhook notification channel <a href="#add-webhook" id="add-webhook"></a>

1. Go to the **Alerts → Notification channels** tab and click **New notification channel**.

![](../../.gitbook/assets/nr3.png)

1. Select **Channel Type** Webhook and insert the generated in iLert field **Base URL**.

![](../../.gitbook/assets/nr4\_png.png)

1. After you click on **Create channel** , you have the opportunity to test the integration. Click **Send a test notification**.

![](../../.gitbook/assets/nr5.png)

1. Check if an alert has been created in iLert.
2. After creating the **Notification Channel** in New Relic, add it to one or more **alert policies**. Go to the **Alert policies** tab and click **Add alert policy**.

![](../../.gitbook/assets/nr6.png)

1. The integration is now set up!

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an alert is closed in New Relic, the associated alert in iLert is automatically fixed.

**What if an alert is acknowledged in New Relic, is the associated alert also confirmed in iLert?**

Yes.

**Can I link New Relic to multiple alert sources in iLert?**

Yes, create a Notification Channel for each alert source in New Relic.
