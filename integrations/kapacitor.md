---
description: >-
  With the iLert Kapacitor integration, you can create incidents in iLert based
  on Kapacitor alerts.
---

# Kapacitor Integration

[Kapacitor](https://docs.influxdata.com/kapacitor/) is an open source data processing framework that makes it easy to create alerts, run ETL jobs and detect anomalies. Kapacitor is the final piece of the [TICK stack](https://influxdata.com/time-series-platform/).

## In iLert <a id="in-ilert"></a>

### Create a Kapacitor alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/screenshot_16_03_21__16_37.png)

2. Enter a name and select your desired escalation policy. Select "Kapacitor" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/ilert%20%2841%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the alert rule in Kapacitor.

![](../.gitbook/assets/ilert%20%2838%29.png)

## In Kapacitor <a id="in-kapacitor"></a>

### Create an alert rule <a id="create-alert-rule"></a>

1. Go to Chronograph dashboard, then to **Alert Rule** and click on the **Create Rule** button

![](../.gitbook/assets/screenshot_2021-03-29_at_15_11_55.png)

2. On the next page,  define your alert conditions, paste the **Webhook URL** that you generated in iLert, define alert summary and click on the **Save Rule** button

![](../.gitbook/assets/chronograf.png)

Finished! Your Kapacitor alerts will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an alert has been completed in Kapacitor, the associated incident in iLert will be resolved automatically.

**Can I connect Kapacitor with multiple alert sources from iLert?**

Yes, simply add more alert rules in Kapacitor.

