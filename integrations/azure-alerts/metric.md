---
description: Create alerts in ilert based on Azure Metric.
---

# Azure Metric

## In ilert: Create a Azure Alerts alert source <a href="#in-ilert" id="in-ilert"></a>

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

## In Azure <a href="#in-splunk" id="in-splunk"></a>

\
\


### Create an alert <a href="#create-action-sequences" id="create-action-sequences"></a>

{% hint style="info" %}
All Azure Metric based alerts are supported. However, this documentation page describes how to set up the Virtual machines based alerts.
{% endhint %}

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Virtual machines.**

![](<../../.gitbook/assets/Home\_-\_Microsoft\_Azure (2).png>)

1. Create or choose a virtual machine, then go to details page.

![](../../.gitbook/assets/Virtual\_machines\_-\_Microsoft\_Azure.png)

1. On the next page click on the **Alerts** tab and then click on the **New alert rule** button\*\*.\*\*

![](../../.gitbook/assets/MyServer\_-\_Microsoft\_Azure.png)

1. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](<../../.gitbook/assets/Create\_alert\_rule\_-\_Microsoft\_Azure (3).png>)

1. On the modal window click on the **Create action group** button.

![](<../../.gitbook/assets/Select\_an\_action\_group\_to\_attach\_to\_this\_alert\_rule\_-\_Microsoft\_Azure (1).png>)

1. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (3).png>)

1. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (4).png>)

1. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in ilert and click on** OK\*\*. Name the action e.g.\*\* ilert **and click on the** Review + create\*\* button.

![](<../../.gitbook/assets/Webhook\_-\_Microsoft\_Azure (1).png>)

1. On the next page click on the **Create** button.

![](<../../.gitbook/assets/Create\_action\_group\_-\_Microsoft\_Azure (5).png>)

1. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](../../.gitbook/assets/Create\_alert\_rule\_-\_Microsoft\_Azure1.png)

Finished! Your Azure Metric alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert has been resolved in Azure Alerts, the associated alert in ilert will be resolved automatically.

**Can I connect Azure Alerts with multiple alert sources from ilert?**

Yes, simply create more alert rules in Azure Alerts
