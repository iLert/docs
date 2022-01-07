---
title: Stakeholder engagement
seoTitle: 'iLert: Stakeholder Engagement | Effective Incident Communication'
description: Effective communication with stakeholders during incidents
date: '2020-05-05T05:02:05.000Z'
weight: 3
---

# Stakeholder engagement

## Overview <a href="#overview" id="overview"></a>

With iLert's Stakeholder Engagement feature, you can keep stakeholders informed during an ongoing alert with minimal effort while focusing your time on alert resolution.

Use cases for stakeholders may include

* **Internal stakeholders** within your organization, e.g. executives, the marketing team, customer support team, or other departments
*   **External stakeholders** outside your organization, e.g. if you're an IT service provider and want to keep your

    customers in the loop about an ongoing alert.

Stakeholders will only be able to see the alerts to which they've subscribed to and won't be able to see any other data, such as other alerts, alert sources, escalation policies, etc.

## Group stakeholders into teams <a href="#2" id="2"></a>

We recommend grouping stakeholders into teams. That way, you can subscribe an entire team to an alert instead of adding every user one by one. E.g., you could create teams by department or business service, which also makes it easier for alert responders to decide who to inform about an ongoing alert.

To manage teams, click on the cog icon and go to _Users and teams_. Note that you need to have the admin role to manage teams.

![](../.gitbook/assets/teams.png)

## Subscribe a stakeholder to an alert <a href="#3" id="3"></a>

Stakeholders - or any other iLert user - can be subscribed to alert by any alert responder within the web interface or the mobile app.

Before you add a stakeholder to an alert, make sure to change the alert summary text so that stakeholders will be able to understand the impact of the alert. On the alert page, click on _Manage stakeholders of this incident_.

![](../.gitbook/assets/manage\_stakeholder.png)

After being added to an alert, stakeholders will immediately receive a notification using their preferred contact methods and will receive additional notifications for any of the following events:

* a status update is posted on the alert with the checkbox _Send as update to stakeholders_ enabled
* when the alert is resolved

![](../.gitbook/assets/status\_update.png)

## FAQ

### Where do stakeholder set their contact details and notification methods?

Stakeholders can log into our mobile app and change their contact details and methods. Any admin can also change the settings for a stakeholder.

### What data will stakeholders be able to see?

Stakeholders will only see the alerts to which they have been added as stakeholders. They won't be able to see any other alerts and objects, such as alert sources, escalation policies, etc.

Mobile app screenshots when logged in as stakeholder:

![Navigation menu](../.gitbook/assets/sh\_menu.png)

![Incident view](../.gitbook/assets/sh\_mobile\_view\_incident.png)

### Is there a way to automatically notify stakeholders about ongoing alerts?

Yes. You can add our **Subscribe stakeholders** alert action and configure it to trigger automatically. See [here](https://docs.ilert.com/integrations/stakeholder-subscription) for more information.
