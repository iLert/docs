---
description: Connect your third party tools to ilert.
---

# Alert sources

An alert source represents the connection between your tools (usually a monitoring system, a ticketing tool, or an application) and ilert. We often refer to alert sources as **inbound integrations**.

ilert provides the following inbound integration options:

| [**Tool integrations**](broken-reference)                   | These are pre-built integrations by ilert and work-out-of the box with your monitoring tools. If you're missing a tool, feel free to [suggest](../contact.md) an integration that you'd like to see in ilert. |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [**Email integration**](../integrations/email/)             | Forward emails to an alert source's email address to integrate with ilert.                                                                                                                                    |
| [**Event API**](https://api.ilert.com/api-docs/#tag/Events) | Write your own integration using our easy-to-use Event API.                                                                                                                                                   |
| **SMS integration**                                         | Send alerts to ilert via SMS.                                                                                                                                                                                 |
| [**Heartbeat monitoring**](heartbeat-monitoring/)           | A heartbeat alert source will automatically create an alert if it does not receive a heartbeat signal from your app at regular intervals.                                                                     |

### Create an alert source

1.  Click on **Alert sources -> Alert sources -> Create a new alert source**\


    <figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>
2.  Choose a name, an escalation policy and your integration type and create the alert source. Refer to our integration documentations for detailed information on how to set up each integration properly.\


    ![](<../.gitbook/assets/image (1) (1) (1).png>)

### Customize your alerts with alert templates

ilert provides you with the ability to set up custom templates for alarm summaries and alarm details. You can freely customise the content of your alert by using preset fields and functions depending on your alert source.

{% hint style="warning" %}
Alert template configuration is available only when editing an alert source, not when creating it.
{% endhint %}

1. Click on **Alert sources -> Alert sources** and choose an alert source to edit
2. Navigate to section **Alert templates** and check the boxes for **Alert summary** and/or **Alert details**
3.  Select the **fields** you want to display for your alert. You are free to add text or symbols in between fields\


    <figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
4. Add field **functions** by clicking on the function icon next to a field to further edit the incoming fields\


You can also use an alert field as an [escalation policy routing key](../on-call-management-and-escalations/escalation-policies.md#routing-key-optional).

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

If an alert is now created from this alert source, its content will be adapted to your configuration.

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>
