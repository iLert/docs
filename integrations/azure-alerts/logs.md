---
description: Create alerts in ilert based on Azure Logs queries.
---

# Azure Logs

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Azure Alerts alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/iLert (34).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](<../../.gitbook/assets/iLert (35).png>)

## In Azure <a href="#in-splunk" id="in-splunk"></a>

### Create a query <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Monitor.**

![](<../../.gitbook/assets/Home\_-\_Microsoft\_Azure (6).png>)

1. Then go to **Logs** and create a query for which you’d like to create an alert.

![](../../.gitbook/assets/Monitor\_-\_Microsoft\_Azure.png)

1. Then click on the **New alert rule** button\*\*.\*\*

![](../../.gitbook/assets/Logs\_-\_Microsoft\_Azure.png)

1. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](<../../.gitbook/assets/1 (1).png>)

1. On the modal window click on the **Create action group** button.

![](<../../.gitbook/assets/2 (1).png>)

1. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/3 (1).png>)

1. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../.gitbook/assets/4 (1).png>)

1. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** OK\*\*. Name the action e.g.\*\* ilert **and click on the** Review + create\*\* button.

![](<../../.gitbook/assets/5 (1).png>)

1. On the next page click on the **Create** button.

![](<../../.gitbook/assets/6 (1).png>)

1. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](<../../.gitbook/assets/7 (1).png>)

Finished! Your Azure Logs alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Azure Log alert do not fire resolve events.

**Can I connect Azure Sentinel with multiple alert sources from ilert?**

Yes, simply create more alert rules in Azure Alerts
