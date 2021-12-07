---
description: >-
  With the iLert Kapacitor integration, you can create alerts in iLert based on
  Kapacitor alerts.
---

# Kapacitor Integration

[Kapacitor](https://docs.influxdata.com/kapacitor/) is an open source data processing framework that makes it easy to create alerts, run ETL jobs and detect anomalies. Kapacitor is the final piece of the [TICK stack](https://influxdata.com/time-series-platform/).

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a Kapacitor alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/screenshot\_16\_03\_21\_\_16\_37.png)

1. Enter a name and select your desired escalation policy. Select "Kapacitor" as the **Integration Type** and click on **Save**.

![](<../.gitbook/assets/ilert (41).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert rule in Kapacitor.

![](<../.gitbook/assets/ilert (38).png>)

## In Kapacitor <a href="#in-kapacitor" id="in-kapacitor"></a>

### Create an alert rule <a href="#create-alert-rule" id="create-alert-rule"></a>

1. Go to Chronograph dashboard, then to **Alert Rule** and click on the **Create Rule** button

![](../.gitbook/assets/screenshot\_2021-03-29\_at\_15\_11\_55.png)

1. On the next page,  define your alert conditions, paste the **Webhook URL** that you generated in iLert, define alert summary and click on the **Save Rule** button

![](../.gitbook/assets/chronograf.png)

Finished! Your Kapacitor alerts will now create alerts in iLert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an alert has been completed in Kapacitor, the associated alert in iLert will be resolved automatically.

**Can I connect Kapacitor with multiple alert sources from iLert?**

Yes, simply add more alert rules in Kapacitor.
