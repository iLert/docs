---
description: Connect your third party tools to ilert.
---

# Alert sources

An alert source represents the connection between your tools (usually a monitoring system, a ticketing tool, or an application) and ilert. We often refer to alert sources as **inbound integrations**.

ilert provides the following inbound integration options:

<table data-header-hidden><thead><tr><th width="250"></th><th></th></tr></thead><tbody><tr><td><a href="broken-reference"><strong>Tool integrations</strong></a></td><td>These are pre-built integrations by ilert and work-out-of the box with your monitoring tools. If you're missing a tool, feel free to <a href="../contact.md">suggest</a> an integration that you'd like to see in ilert.</td></tr><tr><td><a href="../integrations/email/"><strong>Email integration</strong></a></td><td>Forward emails to an alert source's email address to integrate with ilert.</td></tr><tr><td><a href="https://api.ilert.com/api-docs/#tag/Events"><strong>Event API</strong></a></td><td>Write your own integration using our easy-to-use Event API.</td></tr><tr><td><strong>SMS integration</strong></td><td>Send alerts to ilert via SMS.</td></tr><tr><td><a href="heartbeat-monitoring/"><strong>Heartbeat monitoring</strong></a></td><td>A heartbeat alert source will automatically create an alert if it does not receive a heartbeat signal from your app at regular intervals.</td></tr></tbody></table>

### Create an alert source

1.  Click on **Alert sources -> Alert sources -> Create a new alert source**\


    <figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>
2.  Choose a name, an escalation policy and your integration type and create the alert source. Refer to our integration documentations for detailed information on how to set up each integration properly.\


    ![](<../.gitbook/assets/image (1) (1) (1) (1).png>)

### Customize your alerts with alert templates

With alert templates, you can create your own template for the alert summary and alert details using preset fields from the integration.

{% hint style="info" %}
Alert template configuration is not available during alert source creation.
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

In the above example, the field `Run location` (after it was transformed to lower case) from the alert payload will be used as the routing key.

### Customise your alerts with notification priority

By using notification priority, you can easily customise your alert notification based on your notification rules.

1. Click on **Alert sources -> Alert sources** and choose an alert source to edit
2. Navigate to section **Advanced Settings** and see **Notification Priority**

<figure><img src="../.gitbook/assets/Screenshot 2023-04-18 at 13.26.24.png" alt=""><figcaption></figcaption></figure>

&#x20;ilert provides different priority settings to customize your alerts.

* **High (with escalation):** You will be notified based on your high-priority notification rules and an alert can be escalated based on escalation policy.
* **Low (no escalation):** You will be notified based on your low-priority notification rules and an alert cannot be escalated.

> By selecting **High during support hours, low priority** **otherwise** or **Low during support hours, high priority otherwise** you can easily arrange the support hours for each day of the week.

* **High during support hours, low priority otherwise:** During your support hours, you are notified based on your high priority notification rules. At all other times, you are notified based on your low priority notification rules.
* **Low during support hours, high priority otherwise:** During your support hours, you are notified based on your low priority notification rules. At all other times, you are notified based on your high priority notification rules.

If you select **High during support hours, low priority otherwise,** you can choose to **Raise priority of all pending alerts** by ticking the checkbox located under the support hour selection. All your pending alerts for the current alert source will be raised to "high" when your support hours **begin**.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

If you select **Low during support hours, high priority otherwise,** you can choose to **Raise priority of all pending alerts** by ticking the checkbox located under the support hour selection. All your pending alerts for the current alert source will be raised to "high" when your support hours **end**.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
