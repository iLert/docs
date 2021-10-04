---
description: Create alerts in iLert based on Azure Activity Logs queries.
---

# Azure Activity Logs

## In iLert <a id="in-ilert"></a>

### Create a Azure Alerts alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%2835%29.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](../../.gitbook/assets/ilert%20%2834%29.png)

## In Azure <a id="in-splunk"></a>

### Create an alert <a id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Activity log.** 

![](../../.gitbook/assets/home_-_microsoft_azure%20%282%29.png)

1. Find and click on the activity log for which you’d like to create an alert.

![](../../.gitbook/assets/activity_log_-_microsoft_azure.png)

1. On the modal window click on the **New alert rule** button**.**

![](../../.gitbook/assets/delete_action_group_-_microsoft_azure.png)

1. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](../../.gitbook/assets/create_alert_rule_-_microsoft_azure%20%283%29.png)

1. On the modal window click on the **Create action group** button.

![](../../.gitbook/assets/select_an_action_group_to_attach_to_this_alert_rule_-_microsoft_azure.png)

1. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](../../.gitbook/assets/create_action_group_-_microsoft_azure%20%285%29.png)

1. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](../../.gitbook/assets/create_action_group_-_microsoft_azure%20%281%29.png)

1. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in iLert and click on** OK**. Name the action e.g.** ilert **and click on the** Review + create\*\* button.

![](../../.gitbook/assets/webhook_-_microsoft_azure%20%281%29.png)

1. On the next page click on the **Create** button.

![](../../.gitbook/assets/create_action_group_-_microsoft_azure%20%283%29.png)

1. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](../../.gitbook/assets/create_alert_rule_-_microsoft_azure1.png)

Finished! Your Azure Activity Logs alerts will now create alerts in iLert.

## FAQ <a id="faq"></a>

**Will alerts in iLert be resolved automatically?**

No, unfortunately Azure Sentinel alert do not fire resolve events.

**Can I connect Azure Alerts with multiple alert sources from iLert?**

Yes, simply create more alert rules in Azure Alerts

