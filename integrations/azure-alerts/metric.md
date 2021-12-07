---
description: Create alerts in iLert based on Azure Metric.
---

# Azure Metric

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Azure Alerts alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Azure Alerts" as the **Integration Type** and click on **Save**.

![](<../../.gitbook/assets/ilert (35).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert action in Azure Alerts.

![](<../../.gitbook/assets/ilert (34).png>)

## In Azure <a href="#in-splunk" id="in-splunk"></a>

### Create an alert <a href="#create-action-sequences" id="create-action-sequences"></a>

{% hint style="info" %}
All Azure Metric based alerts are supported. However, this documentation page describes how to set up the Virtual machines based alerts.
{% endhint %}

1. Go to [**Azure Portal**](https://portal.azure.com) and then to **Virtual machines.**&#x20;

![](<../../.gitbook/assets/home\_-\_microsoft\_azure (6).png>)

1. Create or choose a virtual machine, then go to details page.

![](../../.gitbook/assets/virtual\_machines\_-\_microsoft\_azure.png)

1. On the next page click on the **Alerts** tab and then click on the **New alert rule** button**.**

![](../../.gitbook/assets/myserver\_-\_microsoft\_azure.png)

1. On the next page change the **Condition** for the alerts and click on the **Add action groups.**

![](<../../.gitbook/assets/create\_alert\_rule\_-\_microsoft\_azure (3).png>)

1. On the modal window click on the **Create action group** button.

![](../../.gitbook/assets/select\_an\_action\_group\_to\_attach\_to\_this\_alert\_rule\_-\_microsoft\_azure.png)

1. On the next page name the group e.g. **iLert** and click on the **Actions** tab.

![](<../../.gitbook/assets/create\_action\_group\_-\_microsoft\_azure (5).png>)

1. **\*\*On the** Actions **tab**, **click on the** Action type **and choose** Webhook.\*\*

![](<../../.gitbook/assets/create\_action\_group\_-\_microsoft\_azure (1).png>)

1. **On the modal window** in the **URI** section and **\*\*paste the** Webhook URL **that you generated in iLert and click on** OK**. Name the action e.g.** ilert **and click on the** Review + create\*\* button.

![](<../../.gitbook/assets/webhook\_-\_microsoft\_azure (1).png>)

1. On the next page click on the **Create** button.

![](<../../.gitbook/assets/create\_action\_group\_-\_microsoft\_azure (3).png>)

1. On the next page scroll down to the **Alert rule details** section, name the alert rule and click on the **Create alert rule** button.

![](../../.gitbook/assets/create\_alert\_rule\_-\_microsoft\_azure1.png)

Finished! Your Azure Metric alerts will now create alerts in iLert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an alert has been resolved in Azure Alerts, the associated alert in iLert will be resolved automatically.

**Can I connect Azure Alerts with multiple alert sources from iLert?**

Yes, simply create more alert rules in Azure Alerts
