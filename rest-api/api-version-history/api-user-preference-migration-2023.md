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

Unless you are using the API or Terraform to manage user notification preferences there is no action required. Refer to the section [Migrating ilert-go and/or Terraform](api-user-preference-migration-2023.md#migrating-ilert-go-and-or-terraform) to follow a migrating guide for both ilert-go and Terraform.

If you are using custom workflows to create or update user preferences, your workflows should continue to work. However to prevent confusion of end-users wanting to make updates to their preferences using the new UI experience, we suggest removing the migrated fields from your user payload: `mobile, landline, notificationPreferences, lowPriorityNotificationPreferences, onCallNotificationPreferences, subscribedAlertUpdateStates, subscribedAlertUpdateNotificationTypes`

{% hint style="info" %}
Please make sure that your users have already started to use the new UI to manage their preferences, before removing the fields and running the updates - otherwise their preferences will be dropped.
{% endhint %}

In case you need support, feel free to [reach out](../../contact.md) any time.

### Migrating ilert-go and/or Terraform

Ilert-go and Terraform were both updated to a new major version.

| Client                                                                                 | Old version | New version |
| -------------------------------------------------------------------------------------- | ----------- | ----------- |
| [ilert-go](https://github.com/iLert/ilert-go)                                          | v2.6.0      | **v3.0.0**  |
| [terraform-provider-ilert](https://registry.terraform.io/providers/iLert/ilert/latest) | v1.11.4     | **v2.0.0**  |

While many inconsistency issues were addressed and quality of life improvements plus bug fixes were implemented, the user resource was updated accordingly and new resources for user notification preferences were introduced in both clients.

There are four possible cases for the migration:

| <ol><li>You did not create/manage a user via Terraform/ilert-go</li></ol>                                                             | You do not have to take any action.                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol start="2"><li>You have referenced a user. (e.g. data source in Terraform, accessed user object in ilert-go)</li></ol>             | <p>Be aware of the <a href="api-user-preference-migration-2023.md#moved-resources">moved resources</a>.<br>When none of the migrated fields (except <code>email</code>) are referenced or used, you do not have to take any action.</p>                                                                                                                                                                                                                                                                      |
| <ol start="3"><li>You have created/managed a user via Terraform/ilert-go <strong>without</strong> notification preferences.</li></ol> | <p><strong>Terraform:</strong> remove field <code>username</code> if used in user resource<br>(only references to the username are allowed)</p>                                                                                                                                                                                                                                                                                                                                                              |
| <ol start="4"><li>You have created/managed a user via Terraform/ilert-go <strong>with</strong> notification preferences.</li></ol>    | <p><strong>Terraform/ilert-go:</strong> remove all fields associated to notification settings (and field <code>username</code>from user in <strong>Terraform</strong>) <br><br>use <code>user_email_contact</code>or     <code>user_phone_number_contact</code>to define your emails or phone numbers<br><br>use <code>user_alert_preference</code>, <code>user_duty_preference</code>, <code>user_subscription_preference</code>, <code>user_update_preference</code> to define your notification rules</p> |

When all migration steps are done you can safely update your ilert-go/Terraform to the latest.

### Migration example for Terraform

The following example visualizes a transition of a pre-v2 user resource to the new user resource and notification settings resources.&#x20;

**Pre v2 script**

```
resource "ilert_user" "example" {
  email      = "example@example.com"
  username   = "example"
  first_name = "example"
  last_name  = "example"

  mobile {
    region_code = "DE"
    number      = "+4915123456789"
  }

  high_priority_notification_preference {
    method = "EMAIL"
    delay  = 0
  }

  low_priority_notification_preference {
    method = "EMAIL"
    delay  = 0
  }

  on_call_notification_preference {
    method     = "EMAIL"
    before_min = 60
  }
}
```

**New v2 script**

```
resource "ilert_user" "example" {
  email      = "example@example.com"
  first_name = "example"
  last_name  = "example"
}

resource "ilert_user_phone_number_contact" "example" {
  target      = "+4915123456789"
  region_code = "DE"
  user {
    id = ilert_user.example.id
  }
}

resource "ilert_user_email_contact" "example" {
  target = "example@example.com"
  user {
    id = ilert_user.example.id
  }
}

resource "ilert_user_alert_preference" "example_high" {
  method = "EMAIL"
  contact {
    id = ilert_user_email_contact.example.id
  }
  delay_min = 0
  type      = "HIGH_PRIORITY"
  user {
    id = ilert_user.example.id
  }
}

resource "ilert_user_alert_preference" "example_low" {
  method = "EMAIL"
  contact {
    id = ilert_user_email_contact.example.id
  }
  delay_min = 0
  type      = "LOW_PRIORITY"
  user {
    id = ilert_user.example.id
  }
}

resource "ilert_user_duty_preference" "example" {
  method = "EMAIL"
  contact {
    id = ilert_user_email_contact.example.id
  }
  before_min = 60
  type       = "ON_CALL"
  user {
    id = ilert_user.example.id
  }
}
```
