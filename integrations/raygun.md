---
description: >-
  With the ilert Raygun integration, you can create alerts in ilert based on
  Raygun crash reports.
---

# Raygun Integration

[Raygun](https://raygun.com/) is a cloud-based platform that provides error, crash, and performance monitoring for your web and mobile applications.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Raygun alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_37.png)

1. Enter a name and select your desired escalation policy. Select "Raygun" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_12.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the webhook integration in Raygun.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_13.png)

## In Raygun <a href="#in-splunk" id="in-splunk"></a>

### Create a notification hook <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Raygun, then to **Integrations** and click on the **Webhook** tile

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_14.png)

1. On the next page,  paste the **Webhook URL** that you generated in ilert and lick on the **Save** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_17.png)

Finished! Your Raygun crash reports will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert has been completed in Raygun, the associated alert in ilert will be resolved automatically.

**Can I connect Raygun with multiple alert sources from ilert?**

No
