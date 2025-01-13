# FAQ

## What is ilert?

ilert is a software for alerting, on-call management and incident comms and helps dev and ops teams to increase the uptime of critical services. Core features of ilert include

* **Reliable alerting** via voice, SMS, push notifications, Slack and more and frictionless acknowledgement, allowing you acknowledge an alert on the same channel where you reveived the alert (e.g. by replying to an SMS).
* **On-call management & escalations**: easily manage on-call duty with on-call schedules and automatic escalations.
* **Call routing:** route incoming calls using on-call schedules and escalation policies to the right on-call person.
* **Incident comms & status pages:** effectively communicate incidents to stakeholders and external users
* **Heartbeat monitoring:** monitor connectivity between your infrastructure and ilert.

ilert integrates with monitoring, ticketing, chat and collaboration tools.

## Which monitoring tools does ilert support?

Please have a look at our [integrations](../../integrations/inbound-integrations/) sections. If you're missing an integration, please contact us at support@ilert.com and we will make it available. Alternatively, you can use our [email integration](../../integrations/inbound-integrations/email/) in the meantime.

## Which alerting channels does ilert support?

ilert supports bi-directional alerting via

* **SMS**: ilert supports sending SMS alerts worldwide. For many countries, SMS alerts are sent from a local number. See [here](../../alerting/phone-numbers/#sms-alerts) for details.
* **Phone calls**: ilert supports international voice calls and converts the alert summary text into speech using text-to-speech technology.
* **Emails**
* **Push notifications** on iOS and Android
* **WhatsApp**
* **Telegram**
* **Chat tools** such as Slack and Microsoft Teams

## Do I need to have a phone line available in order to use ilert?

No. ilert is offered as a Software as a Service solution and has no specific hardware or software requirements. This means you do not need to have a phone line, server, or any other component in order to use ilert.

## How can I send alerts to ilert when our email server or internet connection is down?

We offer several options to prepare for a situation like this:

* Create an SMS alert source in ilert and send alerts to ilert via SMS using a hardware SMS gateway
* Create a [heartbeat alert source](../../alerting/heartbeat-monitoring/) in ilert to monitor the connectivity between your network and ilert.
* Monitor your internet connection using an external monitoring system and send alerts to ilert.

## How can I change the account owner?

The account owner can manage account level settings such as your subscription, billing address, and SSO. Only one user can be the account owner and only the account owner can change the account owner.

{% hint style="info" %}
Once you change the account owner, you will be logged out immediately and cannot change the account settings.
{% endhint %}

To change the account owner, go to **Account settings** and click on the **change** account owner link.

![](<../../.gitbook/assets/Screenshot 2021-04-26 at 16.02.28 (1).png>)

## How can I update the payment method?

To update the payment method, log in as the account owner and go to **Account settings** --> **Subscription** and click on **Update** next to your payment method and enter your new payment information.

![](<../../.gitbook/assets/Screenshot 2020-03-12 at 14.51.44.png>)

## Where can I download my invoices?

The download your invoices, log in as the account owner and go to **Account settings** --> **Invoices.**
