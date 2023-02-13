---
description: >-
  Until February 2023 contact methods as well as notification preferences were
  part of the user REST resource. They have now been moved into their own
  resources.
---

# API user preference migration 2023

### Why was this change introduced?

Our goal was to enable users to manage multiple contact methods and give them the opportunity to have full freedom in configuring their notification devices, as well as to differentiate between their account's email and notification email. This change also gave us the chance to deliver a complete overhaul of the UI experience in web and mobile apps and set the future path for even more upcoming notification methods.

### The old user resource request / response schema

```json
{
  "id": 0,
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "mobile": {
    "regionCode": "string",
    "number": "string"
  },
  "landline": {
    "regionCode": "string",
    "number": "string"
  },
  "timezone": "Europe/Berlin",
  "position": "string",
  "department": "string",
  "avatarUrl": "string",
  "language": "DE",
  "role": "STAKEHOLDER",
  "notificationPreferences": [
    {
      "delay": 0,
      "method": "EMAIL"
    }
  ],
  "lowPriorityNotificationPreferences": [
    {
      "delay": 0,
      "method": "EMAIL"
    }
  ],
  "onCallNotificationPreferences": [
    {
      "beforeMin": 0,
      "method": "EMAIL"
    }
  ],
  "subscribedAlertUpdateStates": [ "ACCEPTED" ],
  "subscribedAlertUpdateNotificationTypes": [ "EMAIL" ],
  "subscriptionNotificationTypes": [ "EMAIL" ],
  "shiftColor": "string"
}
```

### The new user resource request / response schema

```json
{
  "id": 0,
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "timezone": "Europe/Berlin",
  "position": "string",
  "department": "string",
  "avatarUrl": "string",
  "language": "DE",
  "role": "STAKEHOLDER",
  "shiftColor": "string"
}
```

### Moved resources

| Resource / field                            | Moved from | Moved to                                               |
| ------------------------------------------- | ---------- | ------------------------------------------------------ |
| user.email                                  | /api/users | /api/users/{id}/contacts/emails                        |
| user.mobile                                 | /api/users | /api/users/{id}/contacts/phone-numbers                 |
| user.landline                               | /api/users | /api/users/{id}/contacts/phone-numbers                 |
| user.notificationPreferences                | /api/users | /api/users/{id}/notification-preferences/alerts        |
| user.lowPriorityNotificationPreferences     | /api/users | /api/users/{id}/notification-preferences/alerts        |
| user.onCallNotificationPreferences          | /api/users | /api/users/{id}/notification-preferences/duties        |
| user.subscribedAlertUpdateStates            | /api/users | /api/users/{id}/notification-preferences/updates       |
| user.subscribedAlertUpdateNotificationTypes | /api/users | /api/users/{id}/notification-preferences/updates       |
| user.subscriptionNotificationTypes          | /api/users | /api/users/{id}/notification-preferences/subscriptions |

{% hint style="info" %}
Note that the email field still exists in the new user resource schema, that is because this email field still determines the user account's email that is used for logins or things like password recovery. The new email resource however is used to manage alert or incident specific notifications.
{% endhint %}

### How does the live migration work in particular?

* the migration status is tracked on a per user basis
* contact and preference resources were created automatically for every user based on the current user.\* fields
* when using the new UI in web or mobile (or the new APIs) with create or update operations the user is flagged, this will result in GET /users, /users/x, /users/current requests to no longer contain the old but the new schema for this particular user

{% hint style="warning" %}
When sending the old user schema in update (PUT) operations the user's contacts and preferences are reset to the state of the content of the user.\* fields (just like the second migration step described above). Additionally the flag is removed and the old schema is returned by GET resources again.
{% endhint %}

### What action do I have to take?

Unless you are using the API or Terraform to manage user notification preferences there is no action required.

If you are using custom workflows to create or update user preferences, your workflows should continue to work. However to prevent confusion of end-users wanting to make updates to their preferences using the new UI experience, we suggest removing the migrated fields from your user payload: `mobile, landline, notificationPreferences, lowPriorityNotificationPreferences, onCallNotificationPreferences, subscribedAlertUpdateStates, subscribedAlertUpdateNotificationTypes, susbcriptionNotificationTypes`

{% hint style="info" %}
Please make sure that your users have already started to use the new UI to manage their preferences, before removing the fields and running the updates - otherwise their preferences will be dropped.
{% endhint %}

In case you need support, feel free to [reach out](../../contact.md) any time.
