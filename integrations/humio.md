---
description: >-
  CrowdStrike Falcon LogScale provides logging and observability service that
  gives organizations complete visibility to see anomalies, threats, and
  problems, and get to the root of what happened.
---

# Humio Integration

{% hint style="info" %}
Humio has been renamed to CrowdStrike Falcon LogScale
{% endhint %}

## In ilert

* Go to the "**Alert sources**" tab and click "**Create new alert source**"

![](<../.gitbook/assets/ilert-create-alert (4).png>)

* Enter a name and select your desired escalation policy.
* Select "**Humio**" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/humio\_alertsources.png)

* On the next page, an **Humio URL** is generated. You will need the URL for the webhook configuration

![](../.gitbook/assets/humio\_alerturl.png)

## In CrowdStrike Falcon LogScale

* Create an Action by clicking **Alerts** -> **Actions** -> **New Action** from your dashboard

![C](../.gitbook/assets/humio-newaaction.png)

* Choose **Webhook** as type, fill in the name in this case **ilert-webhook**, and on Endpoint URL, put on the **Humio URL** that is generated on ilert

![](../.gitbook/assets/humio-newwebhook.png)

* Save the Action Webhook by clicking on **Save Action** after scrolling down

![](../.gitbook/assets/humio-savewebhook.png)

* Add a new Alert by Clicking **Alerts -> Alerts -> New Alert**

![](../.gitbook/assets/humio-newalert.png)

* Create the Alert by specifying the query that you want the Alert to be based on, and don't forget to check **Alert Enabled** and put the **Webhook Action** that has been configured earlier

![](../.gitbook/assets/humio-alertdetails.png)

* Save the alert, and upon the alert, the incident will be created on ilert side as well
* For more information about LogScale Alerts please refer to the following: [https://library.humio.com/data-analysis/automated-alerts.html](https://library.humio.com/data-analysis/automated-alerts.html)
