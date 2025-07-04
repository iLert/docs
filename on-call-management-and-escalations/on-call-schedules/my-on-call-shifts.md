---
description: See all your shifts in a single view
---

# My on-call shifts

The **My on-call shifts** page allows users to see their shifts across all on-call schedules and escalation policies in a single view. Moreover,  a user can easily create overrides across multiple schedules.

### Definition of "being on-call"

A user is considered to be on-call if they are part of an escalation policy (either directly or indirectly through an on-call schedule). This escalation policy must be used by at least one alert source.&#x20;

{% hint style="info" %}
Escalation policies that aren't used by any alert source do not affect your on-call status and won't show up in this view.
{% endhint %}

If a user is on-call by being directly included in the escalation policy, then on-call entries will show up as "always on-call" starting from the date when the escalation policy was last updated until infinity. If a user is on-call by being included through the membership of an on-call schedule, then on-call entries will be shown as shifts from the on-call schedule.

### My on-call shifts page

<figure><img src="../../.gitbook/assets/image (1) (4).png" alt=""><figcaption></figcaption></figure>

* **My on-call calendar**: shows the shifts for the selected escalation policy levels. The date picker on the left lets you quickly navigate between months and jump to a specific date. Moreover, it highlights days for which you are on-call with an orange dot.
* **My escalation policies** selector lets you select the escalation levels that you wish to see on-call entries for. Note that escalation policies are only included in the list; if you are a member and they are used by at least one alert source. Your selection preference will be remembered.
* **Timezone** selector lets you change the time zone in which you view the on-call entries. By default, the timezone of your user profile is taken.
* **Take on-call** lets you take someone else's on-call
* **Override my shifts** lets you override your shifts from multiple schedules at once.&#x20;
* **Export as calendar** lets you embed your on-call shifts in any calendar application.&#x20;

### Scheduling overrides

There are two ways to schedule overrides:

* by taking someone else's on-call - adding yourself as an override to another shift
* by overriding your shifts  - adding someone else as an override to your shift

#### Take someone else's on-call

Taking someone else's on-call lets you add yourself as an override for someone else's on-call.

To take someone else's on-call

1. Click on the **Take on-call** button
2. Select the user whose shifts you want to take over
3. Select the date range for when you want to take over shifts
4. All shifts from the selected user between the selected date range will be shown grouped by schedule. You can optionally deselect individual shifts that you don't want to take over. Moreover, you can choose to partially override a particular shift. Click the :pencil2: icon at the right to partially override the shift.
5. Click on the **Take on-call** button

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-24 at 22.34.08.png" alt=""><figcaption></figcaption></figure>

#### Override your shifts

You can override your shifts

* by selection the dates in the calendar with your mouse
* by clicking on the **Override my shifts** button

A pop-up will appear showing you the shifts that will be affected by the override. You may change your end and start date and the affected shifts before finally scheduling any overrides.

<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
* Overrides that are created from the **My on-call shifts** page can only be deleted individually by going to each on-call schedule.
* Overrides only apply for on-call schedules and don't replace you in escalation policies.
{% endhint %}

### Exporting your on-call shifts as calendar events

You can subscribe to your on-call shifts by copying the calendar subscription link into your calendar app (Google Calendar, Apple Calendar, Outlook, etc.). The calendar subscription will include all your current and future on-call shifts.

![](<../../.gitbook/assets/Screenshot 2021-08-04 at 17.26.55.png>)

