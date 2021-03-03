---
description: >-
  With the iLert Azure Alerts integration for Azure Logs, you can create
  incidents in iLert based on Azure Logs queries.
---

# Azure Logs

## In iLert <a id="in-ilert"></a>

### Create a Azure Alerts alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%2835%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](../../.gitbook/assets/ilert%20%2834%29.png)

## In Azure <a id="in-splunk"></a>

### Create a query <a id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Monitor.** 

![](../../.gitbook/assets/home_-_microsoft_azure%20%285%29.png)

2. Then go to **Logs** and create a query for which you’d like to create an alert.

![](../../.gitbook/assets/monitor_-_microsoft_azure.png)

3. Then click on the **New alert rule** button**.**

![](../../.gitbook/assets/logs_-_microsoft_azure.png)

4. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](../../.gitbook/assets/1.png)

5. On the modal window click on the **Create action group** button.

![](../../.gitbook/assets/2.png)

6. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](../../.gitbook/assets/3.png)

7. ****On the **Actions** tab**,** click on the **Action type** and choose **Webhook.**

![](../../.gitbook/assets/4.png)

8. ****On the modal window ****in the **URI** section and ****paste the **Webhook URL** that you generated in iLert and click on **OK**. Name the action e.g. **ilert** and click on the **Review + create** button.

![](../../.gitbook/assets/5.png)

9. On the next page click on the **Create** button.

![](../../.gitbook/assets/6%20%281%29.png)

10. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](../../.gitbook/assets/7.png)

Finished! Your Azure Logs alerts will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

No, unfortunately Azure Log alert do not fire resolve events.

**Can I connect Azure Sentinel with multiple alert sources from iLert?**

Yes, simply create more alert rules in Azure Alerts

