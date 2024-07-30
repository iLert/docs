---
description: Create alerts in ilert based on Azure Logs queries.
---

# Azure Logs

## In ilert: Create an Azure Alerts alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Azure Alerts** in the search field, click on the Azure Alerts tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Azure: Create a query <a href="#in-splunk" id="in-splunk"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Monitor.**

![](<../../.gitbook/assets/Home\_-\_Microsoft\_Azure (6).png>)

2. Then go to **Logs** and create a query for which you’d like to create an alert.

![](../../.gitbook/assets/Monitor\_-\_Microsoft\_Azure.png)

3. Then click on the **New alert rule** button\*\*.\*\*

![](../../.gitbook/assets/Logs\_-\_Microsoft\_Azure.png)

4. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](<../../.gitbook/assets/1 (1) (1) (1) (1) (1) (1).png>)

5. On the modal window click on the **Create action group** button.

![](<../../.gitbook/assets/2 (1) (1) (1) (1) (1) (1).png>)

6. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/3 (1) (1) (1) (1) (1).png>)

7. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../.gitbook/assets/4 (1) (1) (1) (1).png>)

8. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** OK\*\*. Name the action e.g.\*\* ilert **and click on the** Review + create\*\* button.

![](<../../.gitbook/assets/5 (1) (1) (1).png>)

9. On the next page click on the **Create** button.

![](<../../.gitbook/assets/6 (1) (1) (1).png>)

10. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](<../../.gitbook/assets/7 (1) (1) (1).png>)

11. Finished! Your Azure Logs alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Azure Log alert do not fire resolve events.

**Can I connect Azure Sentinel with multiple alert sources from ilert?**

Yes, simply create more alert rules in Azure Alerts
