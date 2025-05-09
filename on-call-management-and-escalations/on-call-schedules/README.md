---
description: Maximize accountability and transparency with on-call schedules
---

# On-call schedules

Use schedules to dynamically determine to whom an alert will be assigned to based on the time of the day. A few things to know about schedules:

* Only one user per schedule can be on-call at a time.
* Schedules are used in escalation policies. The members of a schedule will only be notified about incidents, if the schedule is part of an escalation policy.
* To preserve the history of a schedule, any changes to schedules apply to current and future dates only. Shifts that are in the past cannot be deleted or modified.
* Schedules can be embedded into any calendar application that supports the iCal format.

## Create / modify a schedule

{% hint style="info" %}
**User role permissions required**

* [User role permissions](../../user-administration/user-roles-and-permissions.md) are required to create or modify a schedule.
* Stakeholder users cannot be added to a schedule.
{% endhint %}

ilert offers two types of schedules - **recurring and static schedules**, which differ in the way a schedule is created and maintained. The schedule type cannot be changed after its creation.

| [Recurring schedule](recurring-schedules.md)                                                                                                      | [Static schedule](static-schedules.md)                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <img src="../../.gitbook/assets/image (28).png" alt="" data-size="original">                                                                      | <img src="../../.gitbook/assets/image (27).png" alt="" data-size="original">                                                                                                                                                   |
| <ul><li>Use if shifts are recurring.</li><li>Example: every team member is on-call for a week.</li><li>Shifts are created automatically</li></ul> | <ul><li>Use if you can’t plan your schedule beyond a specific time frame and want to schedule them manually on a regular basis.</li><li>Shifts are created manually by dragging and dropping users onto the calendar</li></ul> |

{% content-ref url="recurring-schedules.md" %}
[recurring-schedules.md](recurring-schedules.md)
{% endcontent-ref %}

{% content-ref url="static-schedules.md" %}
[static-schedules.md](static-schedules.md)
{% endcontent-ref %}

## Overrides

{% hint style="info" %}
**Responder role permissions required**

Overrides can be added by users with **Responder** role privileges. A responder can only add themselves as an override. Users with **User** privileges can add any user as an override.
{% endhint %}

Overrides are one-time changes to a schedule. Example uses of overrides include

* when a user becomes sick, goes on vacation, or would like to swap a shift with another user
* scheduling different shifts for holidays

The main benefits of overrides are that they are easy to add, they do not change the underlying structure of the schedule, they only require Responder role permission, and they can be added via the mobile app.

### Adding overrides in the web app

To schedule an override in the web app

1. Navigate to a schedule detail view
2. Click on the **Schedule override** button or click on a shift in the timeline view
3. In the **Schedule override** dialog, select the user to you want to add as an override

![](<../../.gitbook/assets/image (30) (1).png>)

Overrides can be deleted and overridden by another override. To delete an override, click on the override shift on the timeline, and then on the red **x** icon:

![](<../../.gitbook/assets/image (31).png>)

You can also schedule overrides in the schedules list view by clicking on the **Override** button:

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-24 at 23.28.33.png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.youtube.com/watch?v=FNJv-zAcyAE" %}
Check out our step-by-step Youtube tutorial
{% endembed %}

### Adding overrides in the mobile app

To add an override in the mobile app, open the **Who is on-call?** screen and tap on **Override shift** on the shift you want to override.

| <img src="../../.gitbook/assets/image (32).png" alt="" data-size="original"> | <img src="../../.gitbook/assets/image (33).png" alt="" data-size="original"> |
| :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------: |



### On-call widget in the mobile app

The on-call widget in the navigation menu of the mobile app displays your current on-call status and quickly lets you take someone else's on-call.

<img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt="" data-size="original">

{% hint style="info" %}
The on-call status is based on the selected policy levels from the [My on-call shifts](my-on-call-shifts.md) view. Therefore, the status **Not on-call** means that you are not on-call in any of the selected policies, but you could be on-call in other policies. Click on the **Select policies** link to modify your policy selection
{% endhint %}

## FAQ

#### What happens if there is a gap in a schedule?

If an alert occurs during a time with no coverage in your schedule, then the alert will be escalated immediately to the next escalation level, without waiting for the escalation timeout. If no one is on-call on the entire escalation policy, no one will be notified.

#### Can I choose my own shift color?

Yes, you can change your shift color in your profile settings. Click on your avatar in the navigation bar --> Contact details.

<figure><img src="../../.gitbook/assets/image (2) (2) (1).png" alt=""><figcaption></figcaption></figure>
