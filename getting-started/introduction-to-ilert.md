---
title: Introduction to iLert
seoTitle: >-
  iLert: Introduction to iLert in general | Alerting | Incident Response |
  Uptime
description: >-
  iLert getting started guide. The most important concepts in iLert are
  explained on this page.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Introduction to iLert

## Incident <a id="incident"></a>

An incident is an issue that requires immediate attention and needs to be resolved. Incidents are reported by an alert source and immediately trigger the notification process using the alert source's escalation policy.

An incident can have the following states:

| Status | Description |
| :--- | :--- |
| PENDING | The incident hasn't been acknowledged yet and will escalate until the incident is either acknowledged or resolved. |
| ACCEPTED | The user to whom the incident is assigned is working on resolving the incident and the escalation process is halted. |
| RESOLVED | The incident is resolved and no more notifications are sent. A resolved Incident cannot be opened again. |

## Alert source <a id="alarm-source"></a>

An alert source represents the connection between your tools \(usually a monitoring system, a ticketing tool, or an application\) and iLert.

iLert provides the following inbound integration options:

* [**Tool integrations**](/integrations): these are pre-built integrations by iLert. If you're missing a tool, feel free to [suggest](/contact) an integration that you'd like to see in iLert.
* [**Email integration**](/integrations/email/): 
* Use our [**Event API**](https://api.ilert.com/api-docs/) directly
* **SMS integration**: Send alerts to iLert via SMS



## Escalation policy <a id="escalation-chain"></a>

An escalation policy connects an alert source with the users that are responsible for this alert source. It defines which users or on-call schedules should be notified when an incident is created.

## On-call schedule <a id="duty-roster"></a>

On-call schedules determine who will be notified when an incident is created based on the time of day. Only one user per schedule can be on-call at a time. You can reference an on-call schedule in an escalation policy.

## Notifications <a id="notifications"></a>

In iLert, each user defines in his profile how he will be notified of an incident. A user with admin rights can also maintain the notification settings for other users. iLert supports the following notification channels:

* E-mail
* SMS
* Phone calls
* iPhone and Android push notification

Notifications in iLert are bi-directional, that is, you can respond to a notification using the same channel on which you were notified \(without logging into iLert\).

You have the following response options:

1. Acknowledge the incident
2. Mark the incident as resolved
3. Escalation to the next user

You can find a list of caller IDs for sms and phone calls [here](/getting-started/resource-info).

