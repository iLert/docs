---
description: >-
  iLert's flexible role management allows you to easily setup access for your
  user / employees.
---

# User roles and permissions

## Available roles

Currently you may choose from the following roles

* Stakeholder
* Responder
* User
* Team Admin\*
* Admin
* Account Owner

## Roles explained briefly

### Stakeholder

Stakeholders can be subscribed to incidents and incident updates \(published comments by responders\), however they have no access to create or modify entites. Additionally they do not login to the web ui, instead they can use the iLert mobile app to get insights into current incidents that they are subscribed to and manage their profile and notification settings. These users are manged via an additional quota and may be purchased additionally.

### Responder

Responders can use the web ui and mobile app to manage incidents just like **Users**, however they have no permission to create or modify entities. Besides taking actions on incidents, Responders may override schedules in context of their own assignment.

### User

Users may create or modify entities like Alertsources or On-call Schedules, however they may not create or modify \(or invite\) other Users \(of any role\), as well as change account setttings. Users are also not able to create or modify Teams.

### Team Admin

**Users** may not create or modify teams. But an **Admin** may grant a User, as member of a team, the right to modify certain team. A Team Admin is therefore actually not a role in itself, it is an additional permission that may be granted to a **User** on a team basis**.**

### Admin

An Admin is a **User** with elevated priviliges. He may not access or modify the account settings. However he can create and modify **Users** as well as **Teams**, he may also change the role of **Users**.

### Account Owner

There can only be a single account owner per account. He has the same priviliges as an **Admin**, with the addition of being able to access and modify the account settings as well as subscription settings. Only the account owner himself is able to transfer the Account Owner role to another **User**.

## Role permissions

The table below gives an overview of the role permissions.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Operation</th>
      <th style="text-align:left">Stakeholder</th>
      <th style="text-align:left">Responder</th>
      <th style="text-align:left">User</th>
      <th style="text-align:left">Team Admin</th>
      <th style="text-align:left">Admin</th>
      <th style="text-align:left">Account Owner</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Access Web UI</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Use Mobile App</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Modify Profile Settings</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Subscribe to Incidents</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Manage Incidents</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">View Entities</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Override</p>
        <p>Schedules (Own)</p>
      </td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Override Schedules</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Modify Entities</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Modify Team(s)</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Manage Teams</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Manage Users</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Manage Account</p>
        <p>Settings / Subscription</p>
      </td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
    </tr>
  </tbody>
</table>



{% hint style="info" %}
If you need help with the roles or are looking for different permission [feel free to get in touch](../contact.md)
{% endhint %}

