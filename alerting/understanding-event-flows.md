---
description: >-
  This page describes the ilert's event progression and gives an overview of its
  architecture as well as information on grouping, deduplication, aggregation,
  and suppression of alerts and notifications.
---

# Understanding event progression

## Platform overview

<figure><img src="../.gitbook/assets/shapes at 23-12-05 17.03.21.png" alt=""><figcaption></figcaption></figure>

This global platform overview is a sketch that tries to showcase all streams and moving parts across alerting (formed around **events** and **alerts**) and incident communications (formed around **services** and **incidents**). Different parts are drilled down upon and shown in more focus below.

## Core progression: Event **→** Alert **→** Incident

<figure><img src="../.gitbook/assets/shapes at 23-12-05 16.19.21.png" alt=""><figcaption></figcaption></figure>

This illustration is an extraction of the core incoming event to outgoing notification stream from the top-level overview above.

## Event, alert, and notification aggregation

<figure><img src="../.gitbook/assets/shapes at 23-12-07 00.22.19.png" alt=""><figcaption></figcaption></figure>

This illustration maps the core stream between receiving events and sending notifications and shows where rate limits, aggregations, and suppressions may apply.

If you want to know more about event (alert source) API rate limits, take a look at: REST API **→** Rate Limiting.

A note on "alertKey" grouping: as stated in the graphic, alert grouping based on alertKeys is usually automatically handled by the integration for the specific monitoring tool inside of ilert. However, not all tools support event payloads that contain specific information required to group and identify alerts. To know if an integration supports automatic grouping, keep an eye out for the "**Alert resolution**" or "**Alert acknowledgement**" feature either in the information modal of the **Alert source creation wizard** or in the **Alert source detail view** itself.

A note on "**Grouping in time window**" or "**Allowing a single open/pending alert**": this setting can be configured for every alert source and works in addition to grouping by "alertKey".

### Specific descriptions for the illustrated notification suppression\*

#### Voice calls:

* Only a single ongoing dial is supported per phone number across the platform at a single point in time, including a small buffer before and after the call. **Simply put,** **an outbound voice call to the same phone number is supported approximately every 10 seconds.**
* Each first call made starts a 180-second window, in which up to 2 additional calls can be made until every following call is aggregated until the end of the window. Finally, an aggregated information call is made informing about multiple alerts, if at least one of these alerts is not yet accepted. **Simply put, one call per minute per alert source per phone number**.

#### SMS or email:

* Each first SMS or email sent starts a 180-second window, in which up to 2 additional notifications can be sent until every following notification is aggregated until the end of the window. Finally, an aggregated information notification is sent informing about multiple alerts, if at least one of these alerts is not yet accepted. **Simply put:** **one SMS or email per minute per alert source per phone number or email address.**

#### Push notifications or messengers:

* Each first notification sent starts a 240-second window, in which every following notification is dropped if its content is identical to one of the others already sent in the window.
* Each first notification sent starts a 60-second window, in which up to 19 following notifications are allowed until the rest is dropped. S**imply put, 20 unique notifications per minute** (_Note: that this is a global limit on the target and not on a per alert source basis_)

{% hint style="success" %}
ilert never simply "drops" a notification due to rate limiting or suppression, you will always see an entry for the notification (no matter its state) in the related alert's timeline.
{% endhint %}

#### Suppression availability

Until 2020, notifications were not aggregated.

From 2020 to December 2023, all notifications were automatically aggregated in a 3-minute window, per target per alert source, that started with each first notification.

Specific suppressions and deduplications as listed in this doc have been in use since December 11, 2023.
