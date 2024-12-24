---
title: SMS Integration
seoTitle: 'iLert: SMS for Alerting | Incident Response | Uptime'
date: '2020-04-24T05:02:05.000Z'
weight: 1
description: The ilert SMS Integration helps you to easily consume SMS messages
---

# SMS Integration

Our SMS alert source integration lets you create alerts in ilert from incoming SMS messages. This feature allows you to send SMS messages directly to a dedicated number provisioned in your ilert account, which then automatically converts these messages into alerts. Here's how to set up and start using the SMS alert source in ilert.

### Prerequisites

Before you begin, you need to have the following:

* An active ilert account with access to the [Scale plan](https://www.ilert.com/pricing) or higher.
* The SMS alert source add-on purchased and active on your account.

### Instructions

**1. Purchase the SMS Alert Source Add-on**

To enable SMS alerts, first ensure that you have purchased the SMS alert source add-on available in your plan. This add-on is necessary to activate the feature and provision a mobile number specifically for your SMS alerts.

**2. Provision a Mobile Phone Number**

Once the add-on is active, contact ilert support at **support@ilert.com** to request the provisioning of a dedicated mobile phone number for your account. This number will be used exclusively to receive SMS messages that will trigger alerts in ilert.

**3. Configure Your Alert Source**

After your number has been provisioned, you'll need to configure your SMS alert source in ilert:

* **Log in** to your ilert account.
* Navigate to **Alert sources** and chose the SMS alert source that was created by our support
* **Configure the settings** for your SMS alert source:
  * **Name**: Give your alert source a descriptive name to identify it easily.
  * **Escalation policy**: Assign an escalation policy that defines how alerts from this source should be handled.
  * **Notification priority:** select a notification priority
* **Save** your settings.

**4. Test Your Setup**

To ensure everything is working as expected:

* Send a test SMS to the dedicated number.
* Check if an alert is created in ilert.
