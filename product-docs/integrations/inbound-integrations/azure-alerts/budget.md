---
description: Create alerts in ilert based on Azure Cost Budget.
---

# Budget Alert

## In ilert: Create an Azure Alerts alert source <a href="#in-ilert" id="in-ilert"></a>

1. Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

<figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>

2. Search for **Azure Alerts** in the search field, click on the Azure Alerts tile and click on **Next**.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>

3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Azure: Create an alert <a href="#in-splunk" id="in-splunk"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Cost Management + Billing.**

![](<../../../.gitbook/assets/Home_-_Microsoft_Azure (4).png>)

2. Then go to **Cost Management**

![](../../../.gitbook/assets/Cost_Management___Billing_-_Microsoft_Azure.png)

3. In the **Cost Management** section click on the **Cost alerts** tab and then click on the **Add** button\*\*.\*\*

![](../../../.gitbook/assets/Cost_Management__Nutzungsbasierte_Bezahlung_-_Microsoft_Azure.png)

4. On the next page, **name** the budget e.g. MyBudget, enter budget **amount** and click on the **Next** button

![](<../../../.gitbook/assets/Cost_Management__Nutzungsbasierte_Bezahlung_-_Microsoft_Azure (1).png>)

5. On the next page click on the **Manage action group** button

![](<../../../.gitbook/assets/Cost_Management__Nutzungsbasierte_Bezahlung_-_Microsoft_Azure (2).png>)

6. On the next page, click on the **Add action group** button

![](../../../.gitbook/assets/Manage_actions_-_Microsoft_Azure.png)

7. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../../.gitbook/assets/Create_action_group_-_Microsoft_Azure (3).png>)

8. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../../.gitbook/assets/Create_action_group_-_Microsoft_Azure (4).png>)

9. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** OK\*\*. Name the action e.g.\*\* ilert **and click on the** Review + create\*\* button.

![](<../../../.gitbook/assets/Webhook_-_Microsoft_Azure (1).png>)

10. On the next page click on the **Create** button.

![](<../../../.gitbook/assets/Create_action_group_-_Microsoft_Azure (5).png>)

11. On the next page, enter the **% of budget** value and click on the **Create** button.

![](<../../../.gitbook/assets/Cost_Management__Nutzungsbasierte_Bezahlung_-_Microsoft_Azure (3).png>)

12. Finished! Your Azure Activity Logs alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Azure Budget alert do not fire resolve events.

**Can I connect Azure Alerts with multiple alert sources from ilert?**

Yes, simply create more alert rules in Azure Alerts
