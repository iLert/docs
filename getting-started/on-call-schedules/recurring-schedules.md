# Recurring schedules

Recurring schedules are a flexible way to create complex recurring schedules with minimal effort.

## Create a recurruing schedule

To create a recurring schedule, navigate to **On-call schedules,** click on **Create new on-call schedule** and chose **Create recurring schedule** as the schedule type.

![](<../../.gitbook/assets/image (29).png>)

### Step 1: Add users

Add the users from the dropdown menu. Users will rotate in the order they are listed. You can change the order via drag and drop and remove a user by clicking on the x icon.

![](<../../.gitbook/assets/image (36).png>)

### Step 2: Set on-call rotation

The **on-call rotation** determines when a shift should rotate from one user to the next user. Chose between daily and weekly rotations. For example, if you want your users to rotate every week, enter `1 week`, if you want them to rotate bi-weekly, enter `2 weeks`, and so on.

In the **Starts on** field, chose the start time of your schedule. Note that the start time will also determine the time when a user's on-call duty is handed over to the next user in the rotation.

### Step 3: Set on-call coverage (optional)

By default, the on-call coverage is 24 hours a day, 7 days a week, i.e. users are on-call all the time. If you want to restrict times on-call, e.g. to outside working hours only, you can do so in this step.

![](<../../.gitbook/assets/image (33).png>)

Restricting your on-call coverage will result in gaps in your schedule, where no one is on call. If an alert occurs during a time with no coverage in your schedule, then the alert will be escalated immediately to the next escalation level, without waiting for the escalation timeout. If no one is on-call on the entire escalation policy, no one will be notified.&#x20;
