---
title: Pingdom Integration
seoTitle: 'iLert: Pingdom Integration for Alerting | Incident Response | Uptime'
description: The iLert Pingdom Integration helps you to easily connect iLert with Pingdom.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Pingdom Integration

With Pingdom integration, you can easily integrate Pingdom into iLert. The integration uses the [webhooks](https://help.pingdom.com/hc/en-us/articles/207081599) from Pingdom. Thus, you can easily extend pingdom with SMS, push and voice messaging, as well as rosters from iLert.

## In iLert: Create Pingdom alert source <a id="create-alarm-source"></a>

1. Switch to the tab "alert sources" and click on the button "Create new alert source"
2. Assign name and select escalation chain
3. In the field Integration type select "Pingdom" and save.
4. The Pingdom Webhook URL shown on the next page is required in Pingdom

## In Pingdom: Create new integration <a id="create-integration"></a>

1. Click on "Integrations" in the Pingdom Dashboard and click on "Integrations" on the right side of the menu
2. On the following page, click on the button "Add integration". In the pop-up dialog, select the integration type "Webhook" and assign a name \(eg iLert\). In the "URL" field, copy the Webhook URL from the alert source set up in iLert and click on "Save integration".
3. The integration can now be used in pingdom checks. Switch to a pingdom check and click on "Edit". Activate the iLert Webhook integration and click on "Modify check".

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as the state of a check in Pingdom is OK again, the incident in iLert will be fixed.

**Can I link Pingdom to multiple alert sources in iLert?**

Yes, create a webhook in Pingdom per alert source. You can then choose for each check in Pingdom which webhook you want to use for alerting.

