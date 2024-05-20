---
description: >-
  Configuring ilert SSO to automatically setup users and teams on their first
  login.
---

# Auto provisioning users & teams

You may provide the following additional and **optional** SAML attributes on your **IdP** side when creating SAML2 responses for our SP.

In case of malformed values or states which are not allowed e.g.`role = ADMIN with teamRole = USER` the login and provision workflow will always try to recover the login by relying on fallback values.

### Auto provision user details

| Attribute keys   | Values                                         | Default                   | Info                                |
| ---------------- | ---------------------------------------------- | ------------------------- | ----------------------------------- |
| firstName        | String                                         | parsed from Email (claim) |                                     |
| lastName         | String                                         | parsed from Email (claim) |                                     |
| position         | String                                         | None                      |                                     |
| department       | String                                         | None                      |                                     |
| role             | STAKEHOLDER, GUEST, RESPONDER, USER, ADMIN     | STAKEHOLDER               |                                     |
| mobileRegionCode | Region Code e.g. DE                            | None                      |                                     |
| mobileNumber     | Phone Number without country e.g. 0221 123 123 | None                      | Requires mobileRegionCode to be set |
| userProfileImage | absolute URL to image of user (500x500px)      | None                      |                                     |

### Auto provision team details

| Attribute keys | Values                              | Default   | Info |
| -------------- | ----------------------------------- | --------- | ---- |
| teamName       | String                              |           |      |
| teamRole       | STAKEHOLDER, RESPONDER, USER, ADMIN | RESPONDER |      |

If a team with the same name does not exist, it is created on the first login of this user. In any case the user will be added to the team.

{% hint style="info" %}
Auto provision will only execute if the user does not already exist, a simple login will not create and assign a team for example
{% endhint %}

### Preventing unwanted auto-provisionings in SAML setups

Besides managing access to e.g. LDAP groups on IdP side, ilert additionally offers a simple way to restrict auto-provisioning of certain users on the SdP side. The SAML settings offer the "**Check provision attribute**" field. By default this field is empty and it is in no way required to be set, however if you would like to prevent certain users from being auto-provisioned you can use the field.

<figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

It works by checking the provided SAML attribute field right before the auto provisioning, if you fill it e.g. with "`role`": when a user logs in through your IdP (for the first time), ilert will check if the SAML attribute "`role`" is present in the SAML response, if it is not, the user is redirected to an error page displaying the information that he/she should reach out to an account admin, otherwise the user is auto-provisioned and logged in.

{% hint style="info" %}
Note that role here is just an example, you may use any kind of SAML response attribute that you prefer to set. The value does not matter as well.
{% endhint %}

As an admin or account manager, this gives you an additional option to controll the auto provisioning flow and you can make sure users that want/need to be onboarded are properly setup with their requirements before e.g. making sure a certain user is auto-provisioned with the correct role and team before his first login.
