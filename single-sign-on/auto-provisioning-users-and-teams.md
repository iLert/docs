---
description: >-
  Configuring iLert SSO to automatically setup users and teams on their first
  login.
---

# Auto provisioning users & teams

You may provide the following additional and **optional** SAML attributes on your **IdP** side when creating SAML2 responses for our SP.

In case of malformed values or states which are not allowed e.g.`role = ADMIN with teamRole = USER` the login and provision workflow will always try to recover the login by relying on fallback values.

### Auto provision user details

| Attribute keys | Values | Default | Info |
| :--- | :--- | :--- | :--- |
| firstName | String | parsed from Email \(claim\) |  |
| lastName | String | parsed from Email \(claim\) |  |
| position | String | None |  |
| department | String | None |  |
| role | STAKEHOLDER, GUEST, RESPONDER, USER, ADMIN | RESPONDER |  |
| mobileRegionCode | Region Code e.g. DE | None |  |
| mobileNumber | Phone Number without country e.g. 0221 123 123 | None | Requires mobileRegionCode to be set |

### Auto provision team details

| Attribute keys | Values | Default | Info |
| :--- | :--- | :--- | :--- |
| teamName | String |  |  |
| teamRole | STAKEHOLDER, RESPONDER, USER, ADMIN | RESPONDER  | if `role` is set, will default to role value |

If a team with the same name does not exist, it is created on the first login of this user. In any case the user will be added to the team.

{% hint style="info" %}
Auto provision will only execute if the user does not already exist, a simple login will not create and assign a team for example
{% endhint %}

