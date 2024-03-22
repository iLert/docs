---
description: Connect your third party tools to ilert.
---

# Alert sources

An alert source represents the connection between your tools (usually a monitoring system, a ticketing tool, or an application) and ilert. We often refer to alert sources as **inbound integrations**.

ilert provides the following inbound integration options:

<table data-header-hidden><thead><tr><th width="250"></th><th></th></tr></thead><tbody><tr><td><a href="broken-reference"><strong>Tool integrations</strong></a></td><td>These are pre-built integrations by ilert and work-out-of the box with your monitoring tools. If you're missing a tool, feel free to <a href="../contact.md">suggest</a> an integration that you'd like to see in ilert.</td></tr><tr><td><a href="../integrations/email/"><strong>Email integration</strong></a></td><td>Forward emails to an alert source's email address to integrate with ilert.</td></tr><tr><td><a href="https://api.ilert.com/api-docs/#tag/Events"><strong>Event API</strong></a></td><td>Write your own integration using our easy-to-use Event API.</td></tr><tr><td><strong>SMS integration</strong></td><td>Send alerts to ilert via SMS.</td></tr><tr><td><a href="heartbeat-monitoring/"><strong>Heartbeat monitoring</strong></a></td><td>A heartbeat alert source will automatically create an alert if it does not receive a heartbeat signal from your app at regular intervals.</td></tr></tbody></table>

## Create an alert source

1.  Go to **Alert sources** -> **Alert sources** and click on **Create new alert source**\


    <figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>
2.  Select your integration type in the search search field click on **Next**.\


    <figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one. \


    <figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.\


    <figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings such as custom alert templates or notification prioritiy. Click on **Finish setup** for now.

## Alert template

With alert templates, you can create your own template for the alert summary and alert details using preset fields from the integration. Moreover, our templating lets you extract links from the alert payload. Extracted links will be added to the links section of an alert.

### Custom alert summary and details template

1. Click on **Alert sources -> Alert sources** and choose an alert source to edit
2. Navigate to the section **Alert template** and check the boxes for **Alert summary** and/or **Alert details**
3.  Create your custom template by selecting the **fields** you want use and entering any static text. \
    The available fields are specific to the integration.\


    <figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Field colors and accessing raw fields**

* Blue fields are preset fields provided by ilert.
* Orange fields are extracted from past alerts in your account that were sent from the specific integration
* Grey fields lets you extract any raw fields from the JSON payload by typing the name of the custom field, e.g. `custom_field`. You malso access nested fields and arrays, e.g. `custom_field.array_field[5].nested_field`
{% endhint %}

#### Switching edit modes: Text <--> Block

You may switch between Text and Block mode when editing alert source templates. ilert will automatically translate your current template.

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

#### Testing your templates before saving

Using the preview button you may try out your current template. By default, ilert will try to find one of the latest event payload's that was received by your alert source. If there is none present, we will render a fallback JSON doc, which you might alter as you like.



<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

#### Manipulate alert fields by applying functions

You can also use functions on dynamic fields to manipulate alert fields.

To apply a function, hover over the field and click on the `f(x)` icon.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-25 at 12.55.43.png" alt=""><figcaption></figcaption></figure>

#### Using the template text syntax

By default ilert supports 2 different styles of template content:

* Text
* Block Builder (currently in BETA)

Your alert source template fields will start in text mode by default (see [here](alert-sources.md#switching-edit-modes-text-less-than-greater-than-block)  for more info on how to switch to Block mode). In text mode you may use the **Insert data...** dropdown to help you add template variables quickly (see here to understand more about variables and how ilert automatically parses event data to offer additional variables to you) - the text syntax works like this:

<table><thead><tr><th width="203">Type</th><th width="351.3333333333333">Sample</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>Some text</td><td>You may of course add generic text content to your liking</td></tr><tr><td>Variable</td><td><strong><code>{{</code></strong><code>var</code><strong><code>}}</code></strong></td><td>Extract content of the event and insert it. Note: there is no further sanitizing of the values</td></tr><tr><td>Accessing nested variables</td><td><code>{{ var</code><strong><code>.</code></strong><code>subfield</code><strong><code>.</code></strong><code>evenMore }}</code></td><td>Access sub fields</td></tr><tr><td>Accessing fields of an array</td><td><code>{{ var.arrayField</code><strong><code>[0]</code></strong><code>.more }}</code></td><td>Access array contents</td></tr><tr><td>Applying functions to variables</td><td>{{<code>var</code><strong><code>##</code></strong><code>lowerCase}}</code></td><td>If you want to work with additional functions, we recommend switching to block mode to quickly generate the template syntax</td></tr><tr><td>Passing arguments to functions</td><td><code>{{var##substring((0</code><strong><code>||</code></strong><code>10))}}</code></td><td></td></tr></tbody></table>

{% embed url="https://www.youtube.com/watch?t=3s&v=RIYsmc1Uajs" %}

### Alert links

ilert can extract alert links from the alert payload. Extracted links will be added to the alert's links section.

| Alert link template                                                                       | Alert with extracted link                                           |
| ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| <p><img src="../.gitbook/assets/Screenshot 2023-12-04 at 12.21.15.png" alt=""></p><p></p> | ![](<../.gitbook/assets/Screenshot 2023-12-04 at 12.24.12 (2).png>) |

## Dynamic escalation policy routing

With dynamic escalation policy routing, the escalation policy to be used will be determined based on the incoming alert, instead of always using the same escalation policy that is configured on the alert source.

To extract the escalation policy [routing key](../on-call-management-and-escalations/escalation-policies.md#routing-key-optional) from the alert payload, add a routing key template  in the section **Escalation -> Dynamic routing**.

<figure><img src="../.gitbook/assets/Screenshot 2023-12-04 at 12.34.13.png" alt=""><figcaption></figcaption></figure>

In the above example, the field `Group key` from the alert payload will be used as the routing key.

## Notification priority and support hours

### Default notification priority

By using notification priority, you can easily customise your alert notification based on your notification rules.

1. Click on **Alert sources -> Alert sources** and choose an alert source to edit
2. Scroll down to the section **Notification priority** and set your desired **Notification priority**

<figure><img src="../.gitbook/assets/Screenshot 2023-12-04 at 12.39.28 (1).png" alt=""><figcaption></figcaption></figure>

&#x20;ilert provides different priority settings to customize your alerts.

* **High (with escalation):** You will be notified based on your [high-priority notification rules](notification-settings/#define-notification-rules) and an alert can be escalated based on escalation policy.
* **Low (no escalation):** You will be notified based on your low-priority notification rules and an alert cannot be escalated.

### Support hours based notification priority

ilert also lets you dynamically set the notification priority based on the alert source's [support hours](support-hours.md). This lets you, for instance, use more obstrusive notification methods like phone calls outside of business hours and use not so obstrusive ones during business hours.

<figure><img src="../.gitbook/assets/Screenshot 2023-12-04 at 12.48.44.png" alt=""><figcaption></figcaption></figure>

* **High during support hours, low priority otherwise:** During your support hours, you are notified based on your high priority notification rules. At all other times, you are notified based on your low priority notification rules.
* **Low during support hours, high priority otherwise:** During your support hours, you are notified based on your low priority notification rules. At all other times, you are notified based on your high priority notification rules.

If you select **High during support hours, low priority otherwise,** you can choose to **Raise priority of all pending alerts** by ticking the checkbox located under the support hour selection. All your pending alerts for the current alert source will be raised to "high" when your support hours **begin**.

If you select **Low during support hours, high priority otherwise,** you can choose to **Raise priority of all pending alerts** by ticking the checkbox located under the support hour selection. All your pending alerts for the current alert source will be raised to "high" when your support hours **end**.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

### Dynamic priority mapping

With dynamic priority mapping, you can use alert fields to extract and map notification priority. This will overwrite default priority, if enabled.

To enable dynamic priority mapping

1. Click on **Alert sources -> Alert sources** and choose an alert source to edit
2. Scroll down to the section **Notification priority** and check **Enable dynamic prioriuty mapping**
3. Enter template to to extract the priority field from the alert payload
4. Add priority mappings. A priority mapping maps an extracted value from the alert payload to the ilert priority

<figure><img src="../.gitbook/assets/Screenshot 2023-12-04 at 12.54.38.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
ilert will fallback to the alert source's default priority, if a priority could not be extracted.
{% endhint %}

## Alert grouping

Alert grouping helps you reduce noise by clustering related alerts within a defined time window or by allowing only one open alert at a time per source.

<figure><img src="../.gitbook/assets/Screenshot 2023-08-22 at 22.31.52.png" alt=""><figcaption><p>Enable alert grouping during alert source creation or in the alert source's advanced settings</p></figcaption></figure>

An alert source with alert grouping enabled will group together alerts triggered within the defined time window and create only one alert. Grouped alerts will show up as events in the alert's timeline. You can select relative time windows (e.g. 2 minutes, 5 minutes, etc) or an action-based time-window (e.g. until the alert is accepted or resolved).

<figure><img src="../.gitbook/assets/Screenshot 2023-08-22 at 22.33.18.png" alt="" width="142"><figcaption></figcaption></figure>
