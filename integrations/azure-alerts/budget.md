---
description: Create alerts in iLert based on Azure Cost Budget.
---

# Budget Alert

## In iLert <a id="in-ilert"></a>

### Create a Azure Alerts alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%2835%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](../../.gitbook/assets/ilert%20%2834%29.png)

## In Azure <a id="in-splunk"></a>

### Create an alert <a id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Cost Management + Billing.** 

![](../../.gitbook/assets/home_-_microsoft_azure.png)

2. Then go to **Cost Management**

![](../../.gitbook/assets/cost_management___billing_-_microsoft_azure.png)

3. In the **Cost Management** section click on the **Cost alerts** tab and then click on the **Add** button**.**

![](../../.gitbook/assets/cost_management__nutzungsbasierte_bezahlung_-_microsoft_azure%20%283%29.png)

4. On the next page, **name** the budget e.g. MyBudget, enter budget **amount** and click on the **Next** button

![](../../.gitbook/assets/cost_management__nutzungsbasierte_bezahlung_-_microsoft_azure%20%282%29.png)

5. On the next page click on the **Manage action group** button

![](../../.gitbook/assets/cost_management__nutzungsbasierte_bezahlung_-_microsoft_azure.png)

6. On the next page, click on the **Add action group** button

![](../../.gitbook/assets/manage_actions_-_microsoft_azure.png)

7. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](../../.gitbook/assets/create_action_group_-_microsoft_azure%20%285%29.png)

8. ****On the **Actions** tab**,** click on the **Action type** and choose **Webhook.**

![](../../.gitbook/assets/create_action_group_-_microsoft_azure%20%281%29.png)

9. ****On the modal window ****in the **URI** section and ****paste the **Webhook URL** that you generated in iLert and click on **OK**. Name the action e.g. **ilert** and click on the **Review + create** button.

![](../../.gitbook/assets/webhook_-_microsoft_azure%20%281%29.png)

10. On the next page click on the **Create** button.

![](../../.gitbook/assets/create_action_group_-_microsoft_azure%20%283%29.png)

11. On the next page, enter the **% of budget** value and click on the **Create** button.

![](../../.gitbook/assets/cost_management__nutzungsbasierte_bezahlung_-_microsoft_azure%20%281%29.png)

Finished! Your Azure Activity Logs alerts will now create alerts in iLert.

## FAQ <a id="faq"></a>

**Will alerts in iLert be resolved automatically?**

No, unfortunately Azure Budget alert do not fire resolve events.

**Can I connect Azure Alerts with multiple alert sources from iLert?**

Yes, simply create more alert rules in Azure Alerts

