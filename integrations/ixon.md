---
description: >-
  IXON Cloud is an Industrial IoT platform for the advanced machine manufacturer
  with a tailor-made cloud platform for optimal remote service and applicable
  data insights.
cover: >-
  https://images.unsplash.com/photo-1518704618243-b719e5d5f2b8?crop=entropy&cs=srgb&fm=jpg&ixid=MnwxOTcwMjR8MHwxfHNlYXJjaHw0fHxpbmR1c3RyeSUyMDQuMHxlbnwwfHx8fDE2MzM5NjYyNTQ&ixlib=rb-1.2.1&q=85
coverY: -157.98946088366438
---

# IXON Cloud Integration

This integration uses IXON's [Cloud Notify](https://support.ixon.cloud/hc/en-us/articles/360016840620) to dispatch real-time notifiations from your machine(s) to ilert. That way, you can leverage ilert's alerting, scheduling and escalation capabiltites to send critical alerts from your machines to the right personnel and take immediate action.

### In ilert: Create IXON Cloud alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **IXON Cloud** in the search field, click on the IXON Cloud tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

### Advanced routing configuration

By default ilert will route the alerts of your IXON alert source to the configured escalation policy.\
However if you need a more flexible routing for your IXON use cases you may use our advanced routing options.

![](<../.gitbook/assets/image (52).png>)

You may choose the fields **user id, system label or company id** as dynamic routing fields.\
ilert will then extract the given value e.g. user id from the IXON event and search for an escalation policy that has a matching routing key.

Navigate to the escalation policy that you wish to route to and set its routing key to the IXON value:

![](<../.gitbook/assets/image (47).png>)

Note that if no match for the routing key is found, ilert will fall back to using the configured escalation policy.

### In IXON Cloud

#### Create ilert webhook

1\. Navigate and login to Ixon Cloud Portal at [https://portal.ixon.cloud/](https://portal.ixon.cloud/)

2\. Click on the ![](https://cdn.ixon.cloud/support/website/images/gui-icons/mail\_outline.svg) icon on the top right of the dashboard to navigate to **Messages**

![](../.gitbook/assets/ixon-message.png)

3\. Click on the ![](https://cdn.ixon.cloud/support/website/images/gui-icons/settings\_outline.svg) icon on the top right of the dashboard and select **Configure webhooks**

![](../.gitbook/assets/ixon-webhook.png)

4\. Add the name of the webhook and the webhook url of the ilert alert source from above.

![](../.gitbook/assets/ixon-newwebhook.png)

#### Setup alarm and alarm trigger

Now that the ilert webhook is configured, we're going to setup an alarm and alarm trigger to test the integration. Refer to this [support article](https://support.ixon.cloud/hc/en-us/articles/360016805380) from the IXON documentation for information on how to setup alarms.

1\. Navigate to [**Fleet Manager**](https://portal.ixon.cloud/fleet-manager) \*\*\*\* by clicking on the ![](https://cdn.ixon.cloud/support/website/images/gui-icons/apps\_rounded.svg) icon on the top right and selecting ![](https://cdn.ixon.cloud/support/website/images/gui-icons/gear\_outline.svg) **Fleet Manager**

![](../.gitbook/assets/ixon-tofleet.png)

2\. Go to **Devices** ![](https://cdn.ixon.cloud/support/website/images/gui-icons/cloud\_connectors\_outline.svg) and select the device that you need create an ilert alarm trigger for

![](../.gitbook/assets/ixon-device.png)

3\. If you haven't added any Data Source, add a **Data Source.** In the screenshot below, we chose **Modbus**

![](../.gitbook/assets/ixon-datasource.png)

4\. If you haven't added any variables, add them by clicking on the **Variable** under **Data Source**

![](../.gitbook/assets/ixon-variable.png)

5\. Add Alarms by clicking on the **Alarm Triggers** and based on the alarm trigger, a message will be sent through Webhook and alerts will be created in ilert

![](../.gitbook/assets/ixon-trigger.png)

6\. Click **\[Push config to device]** in the top right corner for your changes to take effect.

For more information on IXON Cloud, please refer to [https://support.ixon.cloud/hc/en-us](https://support.ixon.cloud/hc/en-us).

### References

* [IXON support article: Expand on notifications: call, sms and more, using webhooks](https://support.ixon.cloud/hc/en-us/articles/360018158379-Expand-on-notifications-call-sms-and-more-using-webhooks)
