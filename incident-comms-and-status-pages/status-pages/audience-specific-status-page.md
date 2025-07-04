# Audience-specific status page

## Overview

An **audience-specific status page** is a private page accessible only to authenticated ilert users or stakeholder accounts. It dynamically presents services and metrics tailored to each user's team assignments, ensuring that everyone sees only the information relevant to them.

{% hint style="info" %}
An audience-specific page doesn't support authentication via IP or email whitelists.
{% endhint %}

### Use cases

Audience-specific status pages are ideal for providing tailored content to different user groups. Below are key scenarios where such pages are beneficial:

* **Internal employee status page:** Allow internal employees to view the status of services they have permission to access. This ensures that sensitive information remains secure while keeping your team informed about the services that matter to them.
* **Customer-specific status page:** Show status updates to customers based on the services they subscribe to. This personalized approach enhances customer satisfaction by providing relevant information.
* **Single-Tenant Hosting:** If you offer dedicated instances to each of your customers, you can display status information specific to each customer. This allows for a customized experience that reflects the unique environment of each client.

### Benefits

Creating audience-specific status pages enhances both security and usability by allowing you to:

* **Customize visibility**: Select which services and metrics are visible to specific users or groups. This ensures that users only see information relevant to them.
* **Enhance security**: Restrict access to sensitive information by making the status page private and accessible only to authenticated users.
* **Improve user experience**: Provide users with a tailored view of services and metrics, improving the relevance and usefulness of the information they receive.

## Managing the audience of your status page

After creating an audience-specific status page, you can manage which services and metrics are visible to different audiences (teams) in your organization. Follow these steps to configure your audience settings:

1.  **Add services and metrics**

    Navigate to the **Services and Metrics** tab in your status page settings. Here, add all the services and metrics that you want to include on your status page, regardless of the audience. This will serve as the complete list of items that can be displayed to any audience.
2.  **Configure audience visibility**

    Switch to the **Audience** tab to manage the visibility of services and metrics for each audience. In ilert, each audience corresponds to a team. Any team that owns one or more of the services or metrics you selected in Step 1 will appear as an audience in this tab, with the relevant items listed.

    *   **Making services or metrics Visible to an Audience**

        To control the visibility of a service or metric for a specific audience, use the toggle switch next to each item. Turning the switch on will make the service or metric visible to members of that audience (and also add it to the team); turning it off will hide it.&#x20;
    *   **Adding users to an audience**

        To add users to a team (audience), click on **Add users to this team** in the top-right corner of the audience section. This allows you to include specific users who should have access to the services and metrics designated for that audience. Note that this will also add the selected to the ilert team.

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-07 at 18.31.13.png" alt=""><figcaption></figcaption></figure>

## FAQ

#### Do I need to purchase full user licenses to view an audience-specific status page?

No, a [Stakeholder](../../user-administration/teams.md#team-roles) license is sufficient. Stakeholder licenses can be purchased in packages of 50, 100, 200, etc. Our enterprise plans also offer unlimited stakeholder users.&#x20;

#### How can I create a new audience?

Audiences are defined based on your [team-structure](../../user-administration/teams.md) in ilert. You can create as many teams as you like. You can also create teams specific to your audience-specific status or re-use your existing team structure. To add a team as an audience, click the **+ Add teams** button and select an existing team or create a new team.



## Frequently Asked Questions (FAQ)

#### Do I need to purchase full user licenses so that users can view an audience-specific status page?

No, a Stakeholder license is sufficient for users to access an audience-specific status page. Stakeholder licenses can be purchased in packages of 50, 100, 200, and so on.&#x20;

***

#### How can I create a new audience?

Audiences are defined based on your team structure in ilert. You can create as many teams as you need, either by reusing your existing team structure or by creating new teams specifically for your audience-specific status pages.

To add a team as an audience:

1. **Navigate to the Audience Tab:** Go to your status page settings and switch to the **Audience** tab.
2. **Add a New Team:** Click on the **+ Add Teams** button.
3. **Select or Create a Team:**
   * **Select an Existing Team:** Choose from the list of existing teams.
   * **Create a New Team:** If you need a new audience, you can create a new team directly from this interface.
4. **Configure Visibility:** After adding the team, you can manage which services and metrics are visible to this audience by toggling the switches next to each item.

By organizing your audiences through teams, you can tailor the content of your status pages to specific groups within your organization or customer base, ensuring that each audience sees only the information relevant to them.

