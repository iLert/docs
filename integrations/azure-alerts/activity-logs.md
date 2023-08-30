---
description: Create alerts in ilert based on Azure Activity Logs queries.
---

# Azure Activity Logs

## In ilert: Create a Azure Alerts alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **Azure Alerts** in the search field, click on the Azure Alerts tile and click on **Next**.&#x20;

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5. Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>

6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.



    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Azure <a href="#in-splunk" id="in-splunk"></a>

### Create an alert <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Activity log.**

![](<../../.gitbook/assets/Home\_-\_Microsoft\_Azure (3).png>)

2. Find and click on the activity log for which you’d like to create an alert.

![](../../.gitbook/assets/Activity\_log\_-\_Microsoft\_Azure.png)

3. On the modal window click on the **New alert rule** button\*\*.\*\*

![](../../.gitbook/assets/Delete\_action\_group\_-\_Microsoft\_Azure.png)

4. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](<../../.gitbook/assets/Create\_alert\_rule\_-\_Microsoft\_Azure (3).png>)

5. On the modal window click on the **Create action group** button.

![](<../../.gitbook/assets/Select\_an\_action\_group\_to\_attach\_to\_this\_alert\_rule\_-\_Microsoft\_Azure (1).png>)

6. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (3).png>)

7. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (4).png>)

8. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** OK\*\*. Name the action e.g.\*\* ilert **and click on the** Review + create\*\* button.

![](<../../.gitbook/assets/Webhook\_-\_Microsoft\_Azure (1).png>)

9. On the next page click on the **Create** button.

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (5).png>)

10. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](../../.gitbook/assets/Create\_alert\_rule\_-\_Microsoft\_Azure1.png)

Finished! Your Azure Activity Logs alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Azure Sentinel alert do not fire resolve events.

**Can I connect Azure Alerts with multiple alert sources from ilert?**

Yes, simply create more alert rules in Azure Alerts
