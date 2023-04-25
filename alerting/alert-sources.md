---
description: Integrate third party tools with ilert.
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

With alert templates, you can create you own template for the alert summary and alert details using preset fields from the integration.

{% hint style="info" %}
Alert template configuration is available only when editing an alert source, not when creating it.
{% endhint %}

1. Click on **Alert sources -> Alert sources** and choose an alert source to edit
2. Navigate to section **Alert templates** and check the boxes for **Alert summary** and/or **Alert details**
3.  Create your custom template by selecting the **fields** you want use and entering any static text. \
    The available fields are specific to the integration.\


    <figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Field colors and accessing raw fields**

* Blue fields are preset fields provided by ilert.
* Orange fields are extracted from past alerts in your account that were sent from the specific integration
* Grey fields lets you extract any raw fields from the JSON payload by typing the name of the custom field, e.g. `custom_field`. You malso access nested fields and arrays, e.g. `custom_field.array_field[5].nested_field`
{% endhint %}

#### Manipulate alert fields by applying functions

You can also use functions on dynamic fields to manipulate alert fields.

To apply a function, hover over the field and click on the `f(x)` icon.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-25 at 12.55.43.png" alt=""><figcaption></figcaption></figure>

### Extract escalation policy routing key using dynamic fields

With dynamic escalation policy routing, the escalation policy to be used will be determined based on the incoming alert, instead of always using the same escalation policy that is configured on the alert source.

To extract the escalation policy [routing key](../on-call-management-and-escalations/escalation-policies.md#routing-key-optional) from the alert payload, add a routing key template  under **Advanced settings --> Escalation policy routing**

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

In the above example, the field `Run location` (after it was transformed to lower case) from the alert payloadwill be used as the routing key.
