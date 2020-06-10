---
title: Instana Integration
seoTitle: 'iLert: Instana Integration for Alerting | Incident Response | Uptime'
description: The iLert Instana Integration helps you to easily connect iLert with Instana.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Instana Integration

[Instana](https://www.instana.com/) is an application performance monitoring software for microservice applications. With the iLert Instana Integration, you can receive Instana alerts through iLert and easily extend Instana with SMS, Push, Voice, and iLert on-call-scheduling.

## In iLert: Create Instana alert source <a id="create-alarm-source"></a>

1. Go to the **Alert sources** tab and click on **Create new alert source**
2. Enter a name and select your desired escalation policy
3. Select "Instana" as the **Integration type**
4. The URL shown on the next page is the HTTP endpoint for the Webhook in Instana and will be needed below.

## In Instana: Create webhook integration <a id="create-webhook-integration"></a>

1. Open the Management Portal by clicking on Profile → Management Portal
2. Go to  the **Integration** tab and click on **WEBHOOK**.
3. In the **Notify on** field, select the event types for which you want alerts from iLert.
4. In the **Webhook URL** field, copy the URL from the alert source set up in iLert and click on **Save**.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

For incidents and issues in Instana: Yes, as soon as the state of an incident or issue is CLOSED in Instana, the incident in iLert will be resolved.

For Change and On / Offline Events: Every Change and On / Offline event generates a new Incident in iLert.

