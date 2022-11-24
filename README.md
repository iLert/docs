---
description: >-
  ilert getting started guide. The most important concepts in ilert are
  explained on this page.
---

# Core concepts



ilert is a platform for alerting, on-call management and uptime monitoring. It helps teams to reduce response times to critical alerts by extending monitoring tools with reliable alerting, automatic escalations, on-call schedules and other features to support the incident response process, such as [informing stakeholders](broken-reference) or creating tickets in external incident management tools. The most important concepts are explained in the following sections.

## Alert

An alert is an issue that requires immediate attention and needs to be resolved. Alerts are created by an alert source and immediately trigger the notification process using the alert source's escalation policy.

An alert can have the following states:

| `PENDING`  | The alert hasn't been acknowledged yet and will escalate until the alert is either acknowledged or resolved.      |
| ---------- | ----------------------------------------------------------------------------------------------------------------- |
| `ACCEPTED` | The user to whom the alert is assigned to is working on resolving the alert and the escalation process is halted. |
| `RESOLVED` | The alert is resolved and no more notifications are sent. A resolved alert cannot be opened again.                |

## Alert source (aka inbound integration)

An alert source represents the connection between your tools (usually a monitoring system, a ticketing tool, or an application) and ilert. We often refer to alert sources as **inbound integrations**.

ilert provides the following inbound integration options:

| [**Tool integrations**](integrations/jira/)                      | These are pre-built integrations by ilert and work-out-of the box with your monitoring tools. If you're missing a tool, feel free to suggest an integration that you'd like to see in ilert. |
| ---------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [**Email integration**](integrations/email/)                     | Forward emails to an alert source's email addres to integrate with ilert.                                                                                                                    |
| [**Event API**](https://api.ilert.com/api-docs/)                 | Write your own integration using our easy-to-use Event API.                                                                                                                                  |
| **SMS integration**                                              | Send alerts to ilert via SMS.                                                                                                                                                                |
| [**Hearbeat monitoring**](getting-started/heartbeat-monitoring/) | A heartbeat alert source will automatically create an alert if it does not receive a heartbeat signal from your app at regular intervals.                                                    |

![](<.gitbook/assets/image (1) (1) (1).png>)

## Connectors and alert actions (aka outbound integrations)

Connectors and alert actions allow you to extend your alert response and communication to other tools. They allow you to either manually or automatically perform actions on alerts, such as

* Create ticket in JIRA
* Post a message in Slack
* Post a webhook to a defined HTTP end point
* Trigger a serverless function in AWS, GCP or Azure

A **connector** is created globally in ilert and usually contains all the information to connect with the target system (e.g. a URL, an API key or username and password, etc.). An **alert action** is created at the alert source level and uses its connector to perform a concrete action. Example: Let's say we want to create an issue in JIRA for every alert in ilert. We need to create ...

* ... a JIRA **connector** that contains the URL of the JIRA server and the credentials to connect to it.
* ... an **alert action** at the alert source level that contains information such as whether to trigger the connection manually or automatically for every alert, the JIRA project ID and issue type, and any custom fields that we might want to set in the JIRA issue.

We often refer to connectors and alert actions as **outbound integrations**.

## Escalation policy

An escalation policy connects an alert source with the users that are responsible for this alert source. It defines which users or on-call schedules should be notified when an alert is created.

## On-call schedule

On-call schedules determine who will be notified when an alert is created based on the time of day. Only one user per schedule can be on-call at a time. You can reference an on-call schedule in an escalation policy.

{% content-ref url="on-call-management-and-escalations/on-call-schedules/" %}
[on-call-schedules](on-call-management-and-escalations/on-call-schedules/)
{% endcontent-ref %}

## Services and Incidents

See our incident comms documentation.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

## Notifications

In ilert, each user defines in his profile how he will be notified of an alert. A user with admin rights can also maintain the notification settings for other users. ilert supports the following notification channels:

* E-mail
* SMS
* Phone calls
* iPhone and Android push notification

Notifications in ilert are bi-directional, that is, you can respond to a notification using the same channel on which you were notified (without logging into ilert).

You have the following response options:

1. Acknowledge the alert
2. Mark the alert as resolved
3. Escalation to the next user

You can find a list of caller IDs for sms and phone calls [here](getting-started/phone-numbers/#sms-alerts).

To set your notification preferences

1. Click on your name on then top right and select **My profile**
2. Go to the **Notification settings** tab
3. Change your notification preferences and click **Save**

![](<.gitbook/assets/Screenshot 2020-11-25 at 13.30.30.png>)
