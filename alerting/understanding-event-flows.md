---
description: >-
  This page describes the platform's event flows and gives an overview of its
  architecture as well as information on grouping, deduplication, aggregation
  and suppression of alerts and notifications.
---

# 🏛 Understanding event flows

## Platform overview

<figure><img src="../.gitbook/assets/shapes at 23-12-05 17.03.21.png" alt=""><figcaption></figcaption></figure>

This global platform overview is a sketch that tries to showcase all flows and moving parts across alerting (formed around **events** and **alerts**) and incident communications (formed around **services** and **incidents**). Different parts are drilled down upon and shown in more focus below.

## Core flow: Event -> Alert -> Incident

<figure><img src="../.gitbook/assets/shapes at 23-12-05 16.19.21.png" alt=""><figcaption></figcaption></figure>

This illustration is an extraction of the core incoming event to outgoing notification flow from to top level overview above.

## Event, Alert and Notification aggregation

<figure><img src="../.gitbook/assets/shapes at 23-12-07 00.22.19.png" alt=""><figcaption></figcaption></figure>

This illustration maps the core flow between receiving events and sending notifications and shows where rate limits, aggregations and suppressions may apply.

If you want to know more about event (alert source) API rate limits take a look at: REST API -> Rate Limiting

A note on "alertKey" grouping: as stated in the graphic, alert grouping based on alertKeys is usually automatically handeled by the integration for the specific monitoring tool inside of ilert, however not all tools support event payloads that contain specific information required to group and identify alerts. To know if an integration supports automatic grouping keep an eye out for the "**Alert resolution**" or "**Alert acklowledgement**" feature either in the information modal of the **Alert source creation wizard** or in the **Alert source detail view** itself.

A note on "Grouping in time window" or "Allowing a single open/pending alert" this setting can be configured for every alert source and works in addition to grouping by "alertKey".

### Specific descriptions for the illustrated notification suppression\*

#### Voice calls:

* Only a single ongoing dial is supported per phone number across the platform at a single point in time, including a small buffer before and after the call - simply put: **an outbound voice call to the same phone number is supported approximately every 10 seconds**
* Each first call made starts a 180 second window, in which up to 2 additional calls can be made until every following call is aggregated until the end of the window, finally an aggregated information call is made informing about multiple alerts, if at least one of these alerts is not yet accepted - simply put: one call per minute per alert source per phone number.

#### SMS or email:

* Each first SMS or email sent starts a 180 second window, in which up to 2 additional notifications can be send until every following notification is aggregated until the end of the window, finally an aggregated information notifcation is sent informing about multiple alerts, if at least one of these alerts is not yet accepted - simply put: one SMS or email per minute per alert source per phone number or email address.

#### Push notifications or messengers:

* Each first notification sent starts a 240 second window, in which every following notification is dropped if its content is identical to one of the others already sent in the window.
* Each first notification sent starts a 60 second window, in which up to 19 following notifications are allowed until the rest is dropped - simply put: 20 unique notifications per minute (Note: that this is a global limit on the target and not on a per alert source basis)

#### General

Until 2020 notifications were not aggregated.

From 2020 - Dec 2023 all notifications were automatically aggregated in a 3 minute window, per target per alert source, that started with each first notification.

\*Specific suppressions and deduplications start on: 11.12.2023
