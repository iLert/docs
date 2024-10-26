---
description: >-
  The ilert Microsoft Teams Integration helps you to easily connect ilert with
  Microsoft Teams.
---

# Microsoft Teams Integration

### Certification Overview <a href="#certification-overview" id="certification-overview"></a>

Our bot has undergone a rigorous certification process by Microsoft, ensuring it meets the high standards for security, privacy, and compliance set forth by Microsoft. This attestation confirms that our app adheres to best practices in software development and data handling.

For a deeper understanding of what certification means and why it matters, please refer to the [Microsoft Certification Documentation](https://docs.microsoft.com/en-us/microsoft-365/compliance/offering-certifications?view=o365-worldwide) for third-party apps and services.

### Scope Definitions <a href="#scope-definitions" id="scope-definitions"></a>

Below is a list and description of each scope used by our bot:

#### 1. `Calendars.ReadWrite` <a href="#id-1-calendarsreadwrite" id="id-1-calendarsreadwrite"></a>

* **Description:** Allows the bot to create, read, update, and delete events in user calendars.
* **Use Case:** This permission gives bot the opportunity to manage meetings that related to an alert or directly from within Microsoft Teams

#### 2. `Channel.Create` <a href="#id-2-channelcreate" id="id-2-channelcreate"></a>

* **Description:** Enables the bot to create new channels.
* **Use Case:** Create alert channels directly from alert details view or automatically via alert action.

#### 3. `Channel.ReadBasic.All` <a href="#id-3-channelreadbasicall" id="id-3-channelreadbasicall"></a>

* **Description:** Grants the ability to read basic properties of channels, including names and descriptions.
* **Use Case:** This scope is commonly used to allow the bot to provide a summary of available channels or guide users to the right channel.

#### 4. `ChannelMember.Read.All` <a href="#id-4-channelmemberreadall" id="id-4-channelmemberreadall"></a>

* **Description:** Allows reading the list of members in each channel.
* **Use Case:** Necessary for bot that actions based on channel membership e.g. alert acknolegment.

#### 5. `ChannelMember.ReadWrite.All` <a href="#id-5-channelmemberreadwriteall" id="id-5-channelmemberreadwriteall"></a>

* **Description:** Allows the bot to add or remove members from channels.
* **Use Case:** Necessary for bot to add users to the created channel that are working on an alert.

#### 6. `Chat.Create` <a href="#id-6-chatcreate" id="id-6-chatcreate"></a>

* **Description:** Permits the bot to create one-on-one or group chats.
* **Use Case:** Enable bots to initiate conversations based on alert actions.

#### 7. `Directory.Read.All` <a href="#id-7-directoryreadall" id="id-7-directoryreadall"></a>

* **Description:** Allows reading data in your organization's directory, such as users, groups, and apps.
* **Use Case:** Required for the bot to get basic information about a user who is active in ilert and microsoft teams, and then combine those activities together.

#### 8. `Group.ReadWrite.All` <a href="#id-8-groupreadwriteall" id="id-8-groupreadwriteall"></a>

* **Description:** Enables the bot to read and modify groups, including creating new groups or updating group settings.
* **Use Case:** Enables the bot to show information about groups in ilert management UI

9\. `Team.ReadBasic.All`

* **Description:** Provides access to read basic properties of teams, such as team name and description.
* **Use Case:** Enables the bot to show information about teams in ilert management UI

#### 10. `User.Read.All` <a href="#id-11-userreadall" id="id-11-userreadall"></a>

* **Description:** Allows reading basic profiles of all users in your organization.
* **Use Case:**  Required for the bot to get basic information about a user who is active in ilert and microsoft teams, and then combine those activities together.



The use of these scopes ensures that our bot can interact effectively with Microsoft Teams and its users, providing functionalities that enhance productivity and collaboration within the platform. The scopes are managed carefully to balance functionality with security and privacy concerns.
