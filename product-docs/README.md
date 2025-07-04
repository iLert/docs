---
description: >-
  Get started with ilert - the complete incident management platform for
  reliable alerting, on-call management, and status pages.
---

# Welcome to ilert

ilert is a complete **incident management platform** that provides **reliable alerting**, **on-call management**, and **status pages** to help DevOps teams, SREs, and IT administrators respond to incidents faster and more effectively.

## 🚀 Quick Start (5 minutes)

1. **Sign up** at [app.ilert.com](https://app.ilert.com/signup)
2. **Create your first alert source** - connect your monitoring tool
3. **Set up an escalation policy** - define who gets notified
4. **Configure notifications** - choose your preferred channels
5. **Test the integration** - send a test alert

[**Start your free trial →**](https://app.ilert.com/signup)

## ✨ Key Features

* **🔔 Reliable Alerting**: Never miss critical incidents with SMS, phone calls, push notifications, Slack, Teams, and more
* **👥 On-Call Management**: Automated escalations, schedules, and coverage requests to ensure the right person is always notified
* **📱 Mobile App**: Full incident response capabilities on iOS and Android for on-the-go incident management
* **🌐 Status Pages**: Communicate incidents to stakeholders and customers with professional status pages
* **🔗 100+ Integrations**: Connect with your existing monitoring, ticketing, and collaboration tools
* **🤖 AI-First**: Smart alert grouping, automated root cause analysis and post mortem creation to reduce noise and improve response times

## 📚 Documentation Sections

| Section                                                                                | Description                                        |
| -------------------------------------------------------------------------------------- | -------------------------------------------------- |
| [**Getting Started**](../getting-started/faq/)                                         | Quick setup guides and FAQs                        |
| [**Alerting**](../alerting/alert-sources.md)                                           | Configure alert sources and reliable notifications |
| [**On-Call Management**](../on-call-management-and-escalations/escalation-policies.md) | Set up schedules and escalation policies           |
| [**Integrations**](../integrations/types-of-integrations.md)                           | Connect your tools and workflows                   |
| [**Incident Communication**](../incident-comms-and-status-pages/getting-started.md)    | Communicate incidents to stakeholders              |
| [**Mobile App**](../mobile-app/getting-started-with-ilert-mobile-app.md)               | iOS and Android app documentation                  |
| [**API**](../rest-api/client-libraries/)                                               | REST API and client libraries                      |

## 🎯 Popular Use Cases

* **Infrastructure Monitoring**: Connect Prometheus, CloudWatch, or Datadog for reliable infrastructure alerting
* **Application Monitoring**: Integrate with Sentry, New Relic, or AppDynamics for application incident management
* **Uptime Monitoring**: Use Pingdom, UptimeRobot, or StatusCake for website and service monitoring
* **Security Alerts**: Connect AWS GuardDuty, Azure Sentinel, or CrowdStrike for security incident response
* **CI/CD Pipelines**: Monitor deployments with GitHub, GitLab, or ArgoCD for deployment incident management

***

## Core Concepts

ilert is a complete incident management platform that helps teams reduce response times to critical incidents by providing reliable alerting, automatic escalations, on-call schedules, and incident communication features. The platform extends your monitoring, ticketing tools, and other alert sources with comprehensive incident response capabilities, including [communicating with users and stakeholders,](../bincident-comms-and-status-pages/getting-started.md) updating status pages, or creating tickets in external incident management tools. The most important concepts are explained in the following sections.

## Alert

An alert is an event that requires immediate attention and needs to be resolved. Alerts are created by an alert source and immediately trigger the notification process using the alert source's escalation policy to ensure reliable incident response.

An alert can have the following states:

| `PENDING`  | The alert hasn't been acknowledged yet and will escalate until the alert is either acknowledged or resolved.      |
| ---------- | ----------------------------------------------------------------------------------------------------------------- |
| `ACCEPTED` | The user to whom the alert is assigned to is working on resolving the alert and the escalation process is halted. |
| `RESOLVED` | The alert is resolved and no more notifications are sent. A resolved alert cannot be opened again.                |

## Alert source (aka inbound integration)

An alert source represents the connection between your tools (usually a monitoring system, a ticketing tool, or an application) and ilert. We often refer to alert sources as **inbound integrations**.

{% content-ref url="../alerting/alert-sources.md" %}
[alert-sources.md](../alerting/alert-sources.md)
{% endcontent-ref %}

## Deployment events

The deployment events view gives you a live overview of all deployments related to your account. If a deployment event can be correlated to an alert, ilert will enrich your alert's context with the most relevant deployment information to improve incident response.

{% content-ref url="../alerting/deployment-events.md" %}
[deployment-events.md](../alerting/deployment-events.md)
{% endcontent-ref %}

## Connector and alert action (aka outbound integration)

Connectors and alert actions allow you to extend your incident response and communication to other tools. They allow you to either manually or automatically perform actions on alerts, such as

* Update your ilert status page
* Create a ticket in JIRA
* Post a message in Slack
* Post a webhook to a defined HTTP end point

A **connector** is created globally in ilert and contains all the information to connect with the target system (e.g. a URL, an API key or username and password, etc.). An **alert action** can be created at the team-level and assigned to alert sources. An alert action uses its connector to perform a concrete action. Example: Let's say we want to create an issue in JIRA for every alert in ilert. We need to create ...

* ... a JIRA **connector** that contains the URL of the JIRA server and the credentials to connect to it.
* ... an **alert action** that contains information such as whether to trigger the connection manually or automatically for every alert, the JIRA project ID and issue type, and any custom fields that we might want to set in the JIRA issue.

We often refer to connectors and alert actions as **outbound integrations**.

## Escalation policy

An escalation policy connects an alert source with the users that are responsible for this alert source. It defines which users or on-call schedules should be notified when an alert is created to ensure reliable incident response.

{% content-ref url="../on-call-management-and-escalations/escalation-policies.md" %}
[escalation-policies.md](../on-call-management-and-escalations/escalation-policies.md)
{% endcontent-ref %}

## On-call schedule

On-call schedules determine who will be notified when an alert is created based on the time of day. Only one user per schedule can be on-call at a time. You can reference an on-call schedule in an escalation policy.

{% content-ref url="../on-call-management-and-escalations/on-call-schedules/" %}
[on-call-schedules](../on-call-management-and-escalations/on-call-schedules/)
{% endcontent-ref %}

## Incident, Service and Status Page

Incidents are the main way to communicate with your users when you are experiencing user impacting issues with the services you provide to them. Services model business capabilities to which subscribers can subscribe to receive updates about incidents. Status pages are one way to help you inform users about outages and maintenances of one or more service. Any user in ilert can subscribe to incidents, services and status pages.

{% content-ref url="../broken-reference/" %}
[broken-reference](../broken-reference/)
{% endcontent-ref %}

## Notification

A notification is a message that is sent to a user to inform them about alerts, incidents or on-call shifts. Users manage how they want to be notified in their notification settings to ensure reliable incident response.

{% content-ref url="../alerting/notification-settings/" %}
[notification-settings](../alerting/notification-settings/)
{% endcontent-ref %}
