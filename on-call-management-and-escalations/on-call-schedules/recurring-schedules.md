# Recurring schedules

Recurring schedules are a flexible way to create complex recurring schedules with minimal effort.

## Create a recurring schedule

To create a recurring schedule, navigate to **On-call schedules,** click on **Create new on-call schedule,** and choose **Create recurring schedule** as the schedule type.

![](<../../.gitbook/assets/image (34).png>)

### Step 1: Add users

Add the users from the dropdown menu. Users will rotate in the order in which they are listed. You can change the order via drag and drop and remove a user by clicking the x icon.

![](<../../.gitbook/assets/image (35).png>)

### Step 2: Set on-call rotation

The **on-call rotation** determines when a shift should rotate from one user to the next user. Choose between daily and weekly rotations. For example, if you want your users to rotate every week, enter `1 week`, if you want them to rotate bi-weekly, enter `2 weeks`, and so on.

In the **Starts on** field, choose the start time of your schedule. Note that the start time will also determine the time when a user's on-call duty is handed over to the next user in the rotation.

### Step 3: Set on-call coverage (optional)

By default, the on-call coverage is 24 hours a day, 7 days a week, i.e., users are on-call all the time. If you want to restrict times on-call, e.g., to outside working hours only, you can do so in this step.

![](<../../.gitbook/assets/image (36).png>)

Restricting your on-call coverage will result in gaps in your schedule where no one is on call. If an alert occurs during a time with no coverage in your schedule, then the alert will be escalated immediately to the next escalation level without waiting for the escalation timeout. If no one is on-call on the entire escalation policy, no one will be notified.

## Creating complex schedules with schedule layers <a href="#schedule-layers" id="schedule-layers"></a>

A schedule layer is the configuration element that defines an on-call schedule or a segment thereof. A schedule layer consists of the following parameters:

1. **Users**: an ordered list of users that will rotate in the on-call schedule. You can add a single user multiple times. E.g., if a user should take twice as many shifts as others, you can add them twice.
2. **Rotation:** The amount of time (in days or weeks) after which on-call duty is rotated from one to the next.
3. **Starts on:** the start date and time of the layer.
4. **Ends on (optional):** An optional end date and time of the layer. A layer with no end date will schedule shifts indefinitely. Once an end date is set, no more shifts will be scheduled past the end date.
5. **Restrictions (optional):** Optional times of day (e.g., between 9am – 6pm) or times of week (e.g., Fri 6pm – Mon 9am) to restrict times on-call.
6. **Name (optional):** an optional name to help you better organize layers \*\*\*\*

![Anatomy of a schedule layer](<../../.gitbook/assets/Screen Shot 2022-01-27 at 11.30.44.png>)

You can combine layers to create more complex schedules by having multiple active layers at the same time.

{% hint style="info" %}
**Combining layers with overlapping shifts**

Layers at the bottom take precedence over layers at the top. The example below illustrates the effect of this.
{% endhint %}

![In layer 1, John is on-call the entire week. In layer 2, Peter is on-call on weekends. Because layer 2 is lower than layer 1, the shifts from layer 2 take precedence and are included in the final schedule, which results in John not being on-call on the weekend.](<../../.gitbook/assets/image (59) (1) (1).png>)

Let's look at a few examples to illustrate the power of schedule layers.

### Schedule Examples

#### Follow-the-sun-schedule

A follow-the-sun schedule lets you have 24/7 coverage without putting the burden on one site and distributes on-call across multiple timezones.

Our final schedule configuration will look as follows:

![](<../../.gitbook/assets/image (52) (1) (1).png>)

Here are the steps to create this schedule:

1. Pick a **timezone** for the schedule. The timezone applies to all layers and cannot be edited after creation. In the above example, we select "America/Los\_Angeles"
2. Create a layer for the US team:
   * Select the desired **users**, **rotation,** and **start time**. Note that the start time also denotes the handoff time between shifts. You can also pick a date in the past.
   * Restrict on-call to **specific times of the day**. In the above example, the US team is on-call every day from 9:00 AM - 9:00 PM
   * Optionally, enter a **name** for this layer by clicking on the pen icon in the header.
3. Click on the **Add schedule layer** link to create another schedule layer for the EU team:
   * Select the desired **users**, **rotation,** and **start time**. Because shifts for the EU team start at 9:00 PM, we select 9:00 PM. Note that all times are local to the scheduled timezone "America/Los\_Angeles", i.e. 9:00 PM in "America/Los\_Angeles" is 6:00 AM in "Europe/Berlin" timezone.
   * Restrict on-call to **specific times of the day**. In the above example, the EU team is on-call every day from 9:00 PM - 9:00 AM.
   * Optionally enter a **name** for this layer.

Once you have created all the necessary layers, check the timeline at the bottom and verify that the final schedule is correct.

#### Schedule with different users on weekdays and weekends

In this example, we have one team that is on-call during weekdays and a separate team for the weekends. In our example, weekday shifts are between Monday 9:00 AM and Friday 5:00 PM, and weekend shifts start on Friday 5:00 PM until Monday 9:00 AM.

The final schedule configuration will look as follows:

![](<../../.gitbook/assets/image (50) (1) (1).png>)

The steps to create the schedule:

1. Pick a **timezone** for the schedule. The timezone applies to all layers and cannot be edited after creation. In the above example, we select "Europe/Berlin"
2. Create a layer for the users that are on-call on weekdays
   * Select the desired **users**, **rotation,** and **start time**. Note that the start time also denotes the handoff time between shifts. We select Monday 9:00 AM as the start time / shift handover-
   * Restrict on-call to **specific times of the week** and add "Mon 9:00 - Fri 17:00"
   * Optionally, enter a **name** for this layer by clicking on the pen icon in the header.
3. Click on the **Add schedule layer** link to create another schedule layer for the weekend shifts:
   * Select the desired **users**, **rotation,** and **start time**. Because shifts o the weekend start on Fridays 5:00 PM, we select Fri 5:00 PM for the start time.
   * Restrict on-call to **specific times of the week** and add "Fri 17:00 - Mon 09:00."
   * Optionally enter a **name** for this layer.

Once you have created all the necessary layers, check the timeline at the bottom and verify that the final schedule is correct.

### Create a recurring schedule with the help of AI

{% content-ref url="../../ilert-ai/using-ilert-ai-for-schedule-generation.md" %}
[using-ilert-ai-for-schedule-generation.md](../../ilert-ai/using-ilert-ai-for-schedule-generation.md)
{% endcontent-ref %}

You can also use a conversational interface and set up a recurring schedule. To do so, after choosing "**Create recurring schedules**," find the button "**Create schedule with ilert AI**" at the top right corner. Share your scheduling requirements, including your team members' names, rotation frequency, and times. When ready, click "**Generate**."

<figure><img src="../../.gitbook/assets/AI Schedule 03.gif" alt=""><figcaption></figcaption></figure>

### Editing existing recurring schedules

{% hint style="info" %}
**Are you looking for overrides?**

If you want to make a one-time change to a schedule, create an override instead. See [here](./#overrides) for more info.
{% endhint %}

Whenever you need to make structural changes to the way you organize on-call, you will need to edit your schedule in ilert. Examples include when a new team member joins the on-call rotation, an existing team member leaves the rotation, you want to change the rotation (e.g. from weekly to bi-weekly), etc.

To edit an existing schedule ...

1. Click **On-call scheduling** -> **On-call schedules** in the navigation bar.
2. Select the desired schedule by clicking on the pen icon. Make sure it's a recurring schedule.

You can now make the changes to the layer directly (e.g. add another team member) and select the date for the changes to take effect:

![](<../../.gitbook/assets/Screen Shot 2022-01-27 at 13.21.44.png>)

Alternatively, instead of editing a layer directly, you can also end a layer and start a new layer. You might find this method clearer and easier to transition from one schedule configuration to another. In the example below, we will add a new member to an existing rotation.

1. To end a layer, click on the stop icon in the top right of the layer and select an end date and time.
2. To create a new layer, click on **Add schedule layer** and make the desired changes to your new schedule layer.

![](<../../.gitbook/assets/Screen Shot 2022-01-27 at 13.30.45.png>)
