---
description: >-
  Keep your alert sources quiet and service subscribers informed during
  maintenance.
---

# Maintenance windows

ilert's Maintenance Windows feature allows users to schedule downtime for alert sources and services. This ensures that on-call responders won't receive alerts from alert sources during maintenance and service, and status page subscribers will be informed about planned and ongoing service maintenance.

## Overview

* **Alert Sources**: When placed in maintenance mode, they will not trigger any alerts.
* **Services**: If a service is put into maintenance mode, its status will be updated across all associated status pages.
* **Maintenance notifications**: Optionally inform service and status page subscribers about the maintenance in advance and / or at the start / end of the maintenance.
* **Templates**: Incorporate incident templates in your maintenance messages for consistent communication.

## Setting up a Maintenance Window

1. Navigate to Alert sources --> **Maintenance windows** from the navigation bar. Maintenance windows are also reachable from the **Incident comms / Status pages** menu.
2. Click on **Schedule maintenance**.
3. Provide a short summary and optionally message for your maintenance. You may also apply a [template](maintenance-windows.md#using-incident-templates) to fill this information.
4. Define the **Start** and **End** time for the maintenance window.
5. Select the **Alert sources** and **Services** you wish to put into maintenance mode.
6. (For services only) Set your **notification preferences** on when to notify service and status pages subscribers
   * **Notify Immediately**: Subscribers are informed as soon as the maintenance window is created.
   * **Notify at Start**: Subscribers receive a notification at the beginning of the maintenance window.
   * **Notify at End**: Subscribers are informed once the maintenance period concludes.
7. Click **Schedule maintenance window**.

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>



### Notifications

Keeping subscribers informed is pivotal for maintaining trust. With ilert's flexible notification settings, you can ensure that your subscribers are always in the loop about any scheduled downtimes:

* **Immediate Notification**: This is beneficial for any urgent maintenance windows or for those that you want to give your subscribers ample time to prepare for.
* **Start Notification**: A gentle reminder that a scheduled downtime is commencing.
* **End Notification**: Inform subscribers once the service is back online.

### Using incident templates

For teams that have established incident communication templates, ilert allows you to use these templates when drafting your maintenance messages. This ensures that your messages maintain a consistent tone and format, further establishing trust and clarity with your subscribers.

## Maintenance mode and status pages

For services in maintenance mode, their status will be reflected on all associated status pages. This transparency ensures that stakeholders and customers are informed about the service's downtime, ensuring there are no surprises.

## Conclusion

The Maintenance Windows feature in ilert ensures that necessary downtimes don’t interfere with your operations. By setting up maintenance windows, keeping subscribers informed, and using consistent messaging, you can maintain smooth operations and keep stakeholder trust intact.
