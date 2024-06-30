---
description: The most important concepts in ilert are explained on this page.
---

# Core concepts

ilert is a platform for alerting, on-call management and status pages. It helps teams to reduce response times to critical alerts by extending monitoring, ticketing tools and other alert sources with reliable alerting, automatic escalations, on-call schedules and other features to support the incident response process, such as [communicating with users and stakeholders,](broken-reference) updating status pages or creating tickets in external incident management tools. The most important concepts are explained in the following sections.

## Alert

An alert is an issue that requires immediate attention and needs to be resolved. Alerts are created by an alert source and immediately trigger the notification process using the alert source's escalation policy.

An alert can have the following states:

| `PENDING`  | The alert hasn't been acknowledged yet and will escalate until the alert is either acknowledged or resolved.      |
| ---------- | ----------------------------------------------------------------------------------------------------------------- |
| `ACCEPTED` | The user to whom the alert is assigned to is working on resolving the alert and the escalation process is halted. |
| `RESOLVED` | The alert is resolved and no more notifications are sent. A resolved alert cannot be opened again.                |

## Alert source (aka inbound integration)

An alert source represents the connection between your tools (usually a monitoring system, a ticketing tool, or an application) and ilert. We often refer to alert sources as **inbound integrations**.

{% content-ref url="alerting/alert-sources.md" %}
[alert-sources.md](alerting/alert-sources.md)
{% endcontent-ref %}

## Connector and alert action (aka outbound integration)

Connectors and alert actions allow you to extend your alert response and communication to other tools. They allow you to either manually or automatically perform actions on alerts, such as

* Update your ilert status page
* Create a ticket in JIRA
* Post a message in Slack
* Post a webhook to a defined HTTP end point

A **connector** is created globally in ilert and contains all the information to connect with the target system (e.g. a URL, an API key or username and password, etc.). An **alert action** can be created at the team-level and assigned to alert sources. An alert action uses its connector to perform a concrete action. Example: Let's say we want to create an issue in JIRA for every alert in ilert. We need to create ...

* ... a JIRA **connector** that contains the URL of the JIRA server and the credentials to connect to it.
* ... an **alert action** that contains information such as whether to trigger the connection manually or automatically for every alert, the JIRA project ID and issue type, and any custom fields that we might want to set in the JIRA issue.

We often refer to connectors and alert actions as **outbound integrations**.

## Escalation policy

An escalation policy connects an alert source with the users that are responsible for this alert source. It defines which users or on-call schedules should be notified when an alert is created.

{% content-ref url="on-call-management-and-escalations/escalation-policies.md" %}
[escalation-policies.md](on-call-management-and-escalations/escalation-policies.md)
{% endcontent-ref %}

## On-call schedule

On-call schedules determine who will be notified when an alert is created based on the time of day. Only one user per schedule can be on-call at a time. You can reference an on-call schedule in an escalation policy.

{% content-ref url="on-call-management-and-escalations/on-call-schedules/" %}
[on-call-schedules](on-call-management-and-escalations/on-call-schedules/)
{% endcontent-ref %}

## Incident, Service and Status Page

Incidents are the main way to communicate with your users when you are experiencing user impacting issues with the services you provide to them. Services model business capabilities to which subscribers can subscribe to receive updates about incidents. Status pages are one way to help you inform users about outages and maintenances of one or more service. Any user in ilert can subscribe to incidents, services and status pages.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

## Notification

A notification is a message that is sent to a user to inform them about alerts, incidents or on-call shifts. Users manage how they want to be notified in their notification settings.

{% content-ref url="alerting/notification-settings/" %}
[notification-settings](alerting/notification-settings/)
{% endcontent-ref %}
