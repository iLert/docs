---
description: >-
  Details of incidents created by iLert's call routing number may be posted to
  Slack and Microsoft Team channels, as well as trigger external services using
  webhooks.
---

# Adding webhooks and outbound chat messages

When a call routing number is created for your account, an alert source that is used by the call routing number to manage incidents for incoming calls is automatically added as well. You can find this alert source under the services \(**alert sources**\) navigation option.

The alert source of your call routing number, will always have the **same name** as the call routing number.

![](../.gitbook/assets/image%20%288%29.png)

Click on the connections link in the list view of your call routing number's alert source.

![](../.gitbook/assets/image%20%2814%29.png)

You will then be able to create a new outbound connection for your call routing number.

![](../.gitbook/assets/image%20%289%29.png)

{% hint style="info" %}
Some connections \(when setup for the first time\) will require you to create a connector first \(an entity that keeps your third party tool's secrets and urls safe\) when selecting them in the menu, iLert will automatically take you to the create screen of these connectors.
{% endhint %}

For the sake of this tutorial we stick to the webhook type which does not require a connector.

![](../.gitbook/assets/image%20%2812%29.png)

Make sure the **automatic** type is chosen, fill out your desired **label** and add the webhook's **url**.  
Every incoming call that creates an incident will now also send the webhook including details to your third party system.

Read more on webhooks [here](../integrations/webhook.md).

