---
description: >-
  iLert's flexible role management allows you to easily setup access for your
  users.
---

# User roles and permissions

## Available roles

A user in iLert can have one of the following roles:

* [Stakeholder](user-roles-and-permissions.md#stakeholder)
* [Guest](user-roles-and-permissions.md#guest)
* [Responder](user-roles-and-permissions.md#responder)
* [User](user-roles-and-permissions.md#user)
* [Admin](user-roles-and-permissions.md#admin)
* [Account Owner](user-roles-and-permissions.md#account-owner)

### Stakeholder

Stakeholders will only be able to see the alerts to which they have been added as a subscriber and won't be able to see any other data, such as other alerts, alert sources, escalation policies, etc. Additionally, they can't login to the web application. Instead, they can use the iLert mobile app to get insights into current alerts that they are subscribed to and manage their profile and notification settings. This role is only available as part of our Premium plan.

### Guest

Guests users have access to the application, however they cannot see any resources or users unless they are added as member of a team, which gives them \(depending on their team role\) the permission to see or even edit the resources of the specific team.

### Responder

Responders can use the web ui and mobile app to manage alerts just like **Users**, however they have no permission to create or modify any objects, such as alert sources, schedules, or escalation policies. Besides taking actions on alerts, Responders can add themselves as overrides to schedules.

### User

Users can create or modify entities like alert sources or on-call schedules, however they cannot create or modify \(or invite\) other users \(of any role\), as well as change account setttings. Users are also not able to create or modify Teams. Although users may edit public resources globally, they may not change the ownership of resource \(team context\).

### Team Admin

**Users** may not create or modify teams. But an **Admin** may grant a User, as member of a team, the right to modify certain team. A Team Admin is therefore actually not a role in itself, it is an additional permission that may be granted to a **User** on a team basis**.**

### Admin

An Admin is a **User** with elevated priviliges. He may not access or modify the account settings. However he can create and modify **Users** as well as **Teams**, he may also change the role of **Users** and can create and edit connectors**.** An **Admin** has the right to add and remove team ownerships to/from resources.

### Account Owner

An account owner has the same privileges as an **Admin**, with the addition of being able to access and modify the account settings as well as subscription and billing settings. Only the account owner himself is able to transfer the Account Owner role to another **User**. There can only be a single account owner per account. 

## Role permissions

The table below gives an overview of the role permissions.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Operation</b>
      </th>
      <th style="text-align:center"><b>Stakeholder</b>
      </th>
      <th style="text-align:left">Guest</th>
      <th style="text-align:center"><b>Responder</b>
      </th>
      <th style="text-align:center"><b>User</b>
      </th>
      <th style="text-align:center"><b>Admin</b>
      </th>
      <th style="text-align:center"><b>Account Owner</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Access web app</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Use mobile app</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">View reports*</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Modify profile settings</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:left">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Subscribe to alerts</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Manage alerts</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">View objects, e.g. schedules and escalation policies</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Add him/herself as override to a schedule</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Add (anyone) as overrides to schedules</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Modify objects, e.g. schedules and escalation policies</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Manage teams</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Manage users</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Manage account</p>
        <p>settings and subscription</p>
      </td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Add or remove team ownerships to/from resources</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:left">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x274C;</td>
      <td style="text-align:center">&#x2705;</td>
      <td style="text-align:center">&#x2705;</td>
    </tr>
  </tbody>
</table>

\*_The actual data that is shown in reports will depend on the permissions of the current user.  
If the user has no access to a schedule for example, he will not see the on-call-duty data of this schedule when browsing reports. \(_[_Read more here_](teams.md#report-visibility)_\)_

## Change a user's role

{% hint style="warning" %}
This requires admin or account owner privileges
{% endhint %}

To change a user's role

1. Click on the cog-icon in the navigation bar and select **Users & teams**
2. Click the **Edit** link for the user you would like to change.
3. In the **Basic information** section, select the user's role from the dropdown menu:

![](../.gitbook/assets/screenshot-2020-10-21-at-18.12.57.png)

