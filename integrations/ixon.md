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

This integration uses IXON's [Cloud Notify](https://support.ixon.cloud/hc/en-us/articles/360016840620) to dispatch real-time notifiations from your machine(s) to iLert. That way, you can leverage iLert's alerting, scheduling and escalation capabiltites to send critical alerts from your machines to the right personnel and take immediate action.

### In iLert - create IXON Cloud alert source

1\. Go to the **Alert sources** tab and click on **Create new alert source**

![](<../.gitbook/assets/ilert-create-alert (2).png>)

2\. Enter a name and select your desired escalation policy. Select **IXON Cloud** as the **Integration type** and click **Save**.

![](../.gitbook/assets/ilert-ixoncloud.png)

3\. On the next page, an **IXON Cloud URL** is generated. You will need the URL for the webhook configuration below

![](../.gitbook/assets/ilert-ixoncloud-url.png)



### In IXON Cloud

#### Create iLert webhook

1\. Navigate and login to Ixon Cloud Portal at [https://portal.ixon.cloud/](https://portal.ixon.cloud) 

2\. Click on the ![](https://cdn.ixon.cloud/support/website/images/gui-icons/mail_outline.svg) icon on the top right of the dashboard to navigate to **Messages**

![](../.gitbook/assets/ixon-message.png)

3\. Click on the ![](https://cdn.ixon.cloud/support/website/images/gui-icons/settings_outline.svg) icon on the top right of the dashboard and select **Configure webhooks**

![](../.gitbook/assets/ixon-webhook.png)

4\. Add the name of the webhook and the webhook url of the iLert alert source from above.

![](../.gitbook/assets/ixon-newwebhook.png)

#### Setup alarm and alarm trigger

Now that the iLert webhook is configured, we're going to setup an alarm and alarm trigger to test the integration. Refer to this [support article](https://support.ixon.cloud/hc/en-us/articles/360016805380) from the IXON documentation for information on how to setup alarms.

1\. Navigate to [**Fleet Manager**](https://portal.ixon.cloud/fleet-manager)** **by clicking on the ![](https://cdn.ixon.cloud/support/website/images/gui-icons/apps_rounded.svg)  icon on the top right  and selecting ![](https://cdn.ixon.cloud/support/website/images/gui-icons/gear_outline.svg) **Fleet Manager**

![](../.gitbook/assets/ixon-tofleet.png)

2\. Go to  **Devices **![](https://cdn.ixon.cloud/support/website/images/gui-icons/cloud_connectors_outline.svg) and select the device that you need create an iLert alarm trigger for

![](../.gitbook/assets/ixon-device.png)

3\. If you haven't added any Data Source, add a **Data Source. **In the screenshot below,  we chose **Modbus**

![](../.gitbook/assets/ixon-datasource.png)

4\. If you haven't added any variables, add them by clicking on the **Variable** under **Data Source**

![](../.gitbook/assets/ixon-variable.png)

5\. Add Alarms by clicking on the **Alarm Triggers** and based on the alarm trigger, a message will be sent through Webhook and alerts will be created in iLert

![](../.gitbook/assets/ixon-trigger.png)

6\. Click **\[Push config to device]** in the top right corner for your changes to take effect.

For more information on IXON Cloud, please refer to [https://support.ixon.cloud/hc/en-us](https://support.ixon.cloud/hc/en-us).