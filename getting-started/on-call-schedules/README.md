---
description: Maximize accountability and transparency with on-call schedules
---

# On-call schedules

Use schedules to dynamically determine to whom an alert will be assigned to based on the time of the day. A few things to know about schedules:

* Only one user per schedule can be on-call at a time.
* Schedules are used in escalation policy. The members of a schedule will only be notified about inidents, if the schedule is part of an escalation policy.
* To preserve the history of a schedule, any changes to schedules apply to current and future dates only. Shifts that are in the past cannot be deleted or modified.
* Schedules can be embedded into any calendar application that supports the iCal format.

## Create / modify a schedule

{% hint style="info" %}
**User role permissions required**

* [User role permissions](../user-roles-and-permissions.md) are required to create or modify a schedule. 
* Stakeholder users cannot be added to a schedule.
{% endhint %}

iLert offers two types of schedules - **recurring and static schedules**, which differ in the way a schedule is created and maintained. The schedule type cannot be changed after its creation.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><a href="recurring-schedules.md">Recurring schedule</a>
      </th>
      <th style="text-align:left"><a href="static-schedules.md">Static schedule</a>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../../.gitbook/assets/image (28).png" alt/>
        </p>
        <p></p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../../.gitbook/assets/image (32).png" alt/>
        </p>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Use if shifts are recurring.</li>
          <li>Example: every team member is on-call for a week.</li>
          <li>Shifts are created automatically</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Use if you can&#x2019;t plan your schedule beyond a specific time frame
            and want to schedule them manually on a regular basis.</li>
          <li>Shifts are created manually by dragging and dropping users onto the calendar</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

{% page-ref page="recurring-schedules.md" %}

{% page-ref page="static-schedules.md" %}

## Overrides

{% hint style="info" %}
**Responder role permissions required**

Overrides can be added by users with **Responder** role privileges. A responder can only add herself as an override. Users with **User** privileges can add any user as an override.
{% endhint %}

Overrides are one-time changes to a schedule. Example uses of overrides include

*  when a user becomes sick, goes on vacation, or would like to swap a shift with another user
* scheduling different shifts for holidays

The main benefits of overrides are that they are easy to add, they do not change the underlying structure of the schedule, they only require Responder role permission, and they can be added via the mobile app.

To schedule an override in the web app

1. Navigate to a schedule
2. Click on the **Schedule override** button or click on click on a shift in the timeline view
3. In the **Schedule override** dialog, select the user to you want to add as an override

![](../../.gitbook/assets/image%20%2827%29.png)

Overrides can be deleted and overriden by another override. To delete an override, click on the override shift on the timeline, and then on the red **x** icon:

![](../../.gitbook/assets/image%20%2826%29.png)

To add an override in the mobile app, open the **Who is on-call?** screen and tap on **Override shift** on the shift you want to override. 

<table>
  <thead>
    <tr>
      <th style="text-align:center">
        <p></p>
        <p>
          <img src="../../.gitbook/assets/image (31).png" alt/>
        </p>
      </th>
      <th style="text-align:center">
        <p></p>
        <p>
          <img src="../../.gitbook/assets/image (34).png" alt/>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

## FAQ

#### What happens if there is a gap in a schedule?

If an alert occurs during a time with no coverage in your schedule, then the alert will be escalated immediately to the next escalation level, without waiting for the escalation timeout. If no one is on-call on the entire escalation policy, no one will be notified. 

#### Can I choose my own shift colour?

No, shift colours are automatically assigned to a user and are permanent. 

