# Token lifetimes, error codes, app verification, etc.

## iLert OAuth2 scopes



| Scope           | Description                              |                                                           |
| --------------- | ---------------------------------------- | --------------------------------------------------------- |
| profile         | Access to /api/users/current             |                                                           |
| offline\_access | Issues refresh tokens for PKCE only apps |                                                           |
| policy          | Access to /api/escalation-policies       |                                                           |
| schedule        | Access to /api/schedules                 |                                                           |
| source          | Access to /api/alert-sources             |                                                           |
| monitor         | Access to /api/uptime-monitors           |                                                           |
| action          | Access to /api/alert-actions             |                                                           |
| connector       | Access to /api/connectors                |                                                           |
| maintenance     | Access to /api/maintenance-windows       |                                                           |
| report          | Access to /api/reports                   |                                                           |
| template        | Access to /api/incident-templates        |                                                           |
| service         | Access to /api/services                  | also grants access to manage subscription of current user |
| status\_page    | Access to /api/status-pages              | also grants access to manage subscription of current user |
| team            | Access to /api/teams                     |                                                           |
| user            | Access to /api/users                     |                                                           |
| alert           | Access to /api/alerts                    |                                                           |
| incident        | Access to /api/incidents                 | also grants access to manage subscription of current user |

By default each scope grants **read** permissions to the described resource.\
You may request **write** (granting you read, create and edit permissions on the resource) as well as **delete** permissions (granting you read, create, edit and delete permissions on the resource).

**Examples**:

| service   | grants GET on /api/services                    |   |
| --------- | ---------------------------------------------- | - |
| service:r | same as service                                |   |
| service:w | grants GET, POST, PUT on /api/services         |   |
| service:d | grants GET, POST, PUT, DELETE on /api/services |   |

You may request multiple scopes by separating them with a space.

**Like so**: `profile service:w offline_access`

## OAuth2 endpoints overview



| Method | Url                                                                                                                |
| ------ | ------------------------------------------------------------------------------------------------------------------ |
| `GET`  | [https://app.ilert.com/api/developers/oauth2/authorize](https://app.ilert.com/api/developers/oauth2/authorize)     |
| `POST` | [https://api.ilert.com/api/developers/oauth2/token](https://api.ilert.com/api/developers/oauth2/token)             |
| `POST` | [https://api.ilert.com/api/developers/oauth2/token\_info](https://api.ilert.com/api/developers/oauth2/token\_info) |
| `POST` | [https://api.ilert.com/api/developers/oauth2/revoke](https://api.ilert.com/api/developers/oauth2/revoke)           |

## OAuth2 error codes overview



| Code                     | HTTP Status Code |
| ------------------------ | ---------------- |
| invalid\_request         | 400              |
| invalid\_scope           | 400              |
| access\_denied           | 400              |
| server\_error            | 500              |
| unsupported\_grant\_type | 400              |
| invalid\_grant           | 401              |

## OAuth2 lifetimes and numbers



| Type                            | Lifetime                                                            |   |
| ------------------------------- | ------------------------------------------------------------------- | - |
| code                            | 2 minutes                                                           |   |
| access\_token                   | 1 hour                                                              |   |
| refresh\_token                  | 1 year                                                              |   |
| refresh\_token per app per user | max. 10, if exceeded oldest refresh\_token is automatically revoked |   |
| refresh token requests          | do not refresh a token more than once per 5 minutes                 |   |
| request rate limits             | [usual request limits](../alertsource-throttle.md) apply            |   |

{% hint style="info" %}
If you are building a backend application and it is verified, your refresh\_token lifetime may be changed so that they never expire. Please [reach out to us](../../contact.md).
{% endhint %}

## App verification

{% hint style="success" %}
We would love to hear about and verify your applications, feel free to [reach out to us](../../contact.md), as soon as you are ready.
{% endhint %}

## Other info

{% hint style="warning" %}
Do not rely on a users email address without being sure it is verified, or your application might be open to attacks where the email address is mimiced on the authorization server.

Use the username or the user's id to verify account ownership in your app.
{% endhint %}

