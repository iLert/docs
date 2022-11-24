---
description: Create alerts in ilert based on Azure Cost Budget.
---

# Budget Alert

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Azure Alerts alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/iLert (34).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](<../../.gitbook/assets/iLert (35).png>)

## In Azure <a href="#in-splunk" id="in-splunk"></a>

### Create an alert <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Cost Management + Billing.**&#x20;

![](<../../.gitbook/assets/Home\_-\_Microsoft\_Azure (4).png>)

1. Then go to **Cost Management**

![](../../.gitbook/assets/Cost\_Management\_\_\_Billing\_-\_Microsoft\_Azure.png)

1. In the **Cost Management** section click on the **Cost alerts** tab and then click on the **Add** button**.**

![](../../.gitbook/assets/Cost\_Management\_\_Nutzungsbasierte\_Bezahlung\_-\_Microsoft\_Azure.png)

1. On the next page, **name** the budget e.g. MyBudget, enter budget **amount** and click on the **Next** button

![](<../../.gitbook/assets/Cost\_Management\_\_Nutzungsbasierte\_Bezahlung\_-\_Microsoft\_Azure (1).png>)

1. On the next page click on the **Manage action group** button

![](<../../.gitbook/assets/Cost\_Management\_\_Nutzungsbasierte\_Bezahlung\_-\_Microsoft\_Azure (2).png>)

1. On the next page, click on the **Add action group** button

![](../../.gitbook/assets/Manage\_actions\_-\_Microsoft\_Azure.png)

1. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (3).png>)

1. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (4).png>)

1. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** OK**. Name the action e.g.** ilert **and click on the** Review + create\*\* button.

![](<../../.gitbook/assets/Webhook\_-\_Microsoft\_Azure (1).png>)

1. On the next page click on the **Create** button.

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (5).png>)

1. On the next page, enter the **% of budget** value and click on the **Create** button.

![](<../../.gitbook/assets/Cost\_Management\_\_Nutzungsbasierte\_Bezahlung\_-\_Microsoft\_Azure (3).png>)

Finished! Your Azure Activity Logs alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Azure Budget alert do not fire resolve events.

**Can I connect Azure Alerts with multiple alert sources from ilert?**

Yes, simply create more alert rules in Azure Alerts
