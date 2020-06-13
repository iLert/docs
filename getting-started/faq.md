# FAQ

## What is iLert?

iLert is a software for alerting, on-call management and uptime monitoring and helps dev and ops teams to increase the uptime of critical services. Core features of iLert include

* **Reliable alerting** via voice, SMS, push notifications, Slack and more and frictionless acknowledgement, allowing you acknowledge an incident on the same channel where you reveived the alert \(e.g. by replying to an SMS\).
* **On-call management & escalations**: easily manage on-call duty with on-call schedules and automatic escalations.
* **Uptime & performance monitoring:** monitor your website, server, or API using various checks such as HTTP, ICMP ping or TCP.
* **Call routing:** route incoming calls using on-call schedules and escalation policies to the right on-call person.

iLert integrates with monitoring, ticketing, chat, and collaboration tools.

## Which monitoring tools does iLert support?

Please have a look at our integrations sections. If you're missing an integration, please contact us at support@ilert.com and we will make it available. Alternatively, you can use our [email integration](../integrations/email.md)

## How is the integration of iLert with my existing monitoring tools carried out?

Each alert source within iLert has its own email address \(for example, nagios@example.ilertnow.com\). When the monitoring system sends an email to this address, iLert immediately creates an incident and initiates the alerting process.

In addition, we make available plugins for certain monitoring systems \(currently Nagios and Icinga\) that enable close interoperability with iLert. For example, with Nagios, this enables the handling of not just PROBLEM events but also RECOVERY and ACKNOWLEDGEMENT events. This means that whenever an incident is taken on or fixed by Nagios, this development is automatically reflected in iLert.

## I don't want to be notified of every single alert in my monitoring system. Does iLert have some sort of filtering mechanism?

Yes, iLert has filtering mechanisms. For each individual alarm source, it is possible to define which alerts should be ignored, or which should be bundled into a common incident. For example, alerts can be automatically deduplicated or filtered according to specific words.

## What communication channels does iLert support?

iLert is capable of sending alerts via email, SMS, voice messaging, and push notifications to iPhone and Android.

## Do I need to have a phone line available in order to use iLert?

No. iLert is offered as a pure Software as a Service solution and has no specific hardware or software assumptions nor requirements. This means you do not need to have a phone line, server, or any other component in order to use the software.

## Does iLert support issue-specific notifications and escalation?

Yes, the notification behaviour can be customized for each specific alarm cause. It is possible to define separate notification rules for each source of alarm. There is no limit to how many alarm sources can be set up.

## Our monitoring system is already capable of sending SMS messages when issues are encountered. Does this make iLert redundant?

Merely sending SMS messages constitutes a "send and forget" strategy, and does not represent a reliable method of communication. iLert follows up on the delivery of each single message and reacts automatically when the recipient does not respond. This could be in the form of, for example, a telephone call following an unanswered email, or the forwarding of an alert to the next point of contact in the escalation chain.

## How can I send an alert to iLert when our email server or internet connection is down?

We recommend having the email server and internet connection monitored by a separate external service. The alerts from this service can then, in turn, be forwarded to iLert.

## What measures have been taken to ensure continuous uptime for iLert?

iLert's infrastructure is distributed across three data centers which are independent from each other and at different physical locations. All data is replicated between both centers in real-time. Each component is structurally redundant such that the failure of a single component does not jeopardize the functioning of iLert. This is also the case with our phone and SMS providers. We work with 3 providers for each communication method. We also conduct daily backups. Should you have further questions on this topic, please get in touch with us.

