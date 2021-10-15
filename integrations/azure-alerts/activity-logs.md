---
description: Create alerts in iLert based on Azure Activity Logs queries.
---

# Azure Activity Logs

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create a Azure Alerts alert source <a href="create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/iLert (34).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](<../../.gitbook/assets/iLert (35).png>)

## In Azure <a href="in-splunk" id="in-splunk"></a>

### Create an alert <a href="create-action-sequences" id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Activity log.** 

![](<../../.gitbook/assets/Home\_-\_Microsoft_Azure (3).png>)

1. Find and click on the activity log for which you’d like to create an alert.

![](../../.gitbook/assets/Activity_log\_-\_Microsoft_Azure.png)

1. On the modal window click on the **New alert rule** button**.**

![](../../.gitbook/assets/Delete_action_group\_-\_Microsoft_Azure.png)

1. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](<../../.gitbook/assets/Create_alert_rule\_-\_Microsoft_Azure (3).png>)

1. On the modal window click on the **Create action group** button.

![](<../../.gitbook/assets/Select_an_action_group_to_attach_to_this_alert_rule\_-\_Microsoft_Azure (1).png>)

1. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/Create_action_group\_-\_Microsoft_Azure (3).png>)

1. **\*\*On the **Actions** tab**,** click on the **Action type** and choose **Webhook.\*\*

![](<../../.gitbook/assets/Create_action_group\_-\_Microsoft_Azure (4).png>)

1. **On the modal window **in the **URI** section and **\*\*paste the **Webhook URL** that you generated in iLert and click on **OK**. Name the action e.g. **ilert** and click on the **Review + create\*\* button.

![](<../../.gitbook/assets/Webhook\_-\_Microsoft_Azure (1).png>)

1. On the next page click on the **Create** button.

![](<../../.gitbook/assets/Create_action_group\_-\_Microsoft_Azure (5).png>)

1. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](../../.gitbook/assets/Create_alert_rule\_-\_Microsoft_Azure1.png)

Finished! Your Azure Activity Logs alerts will now create alerts in iLert.

## FAQ <a href="faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

No, unfortunately Azure Sentinel alert do not fire resolve events.

**Can I connect Azure Alerts with multiple alert sources from iLert?**

Yes, simply create more alert rules in Azure Alerts
