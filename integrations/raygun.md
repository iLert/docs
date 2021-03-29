---
description: >-
  With the iLert Raygun integration, you can create incidents in iLert based on
  Raygun crash reports.
---

# Raygun Integration

[Raygun](https://raygun.com/) is a cloud-based platform that provides error, crash, and performance monitoring for your web and mobile applications.

## In iLert <a id="in-ilert"></a>

### Create a Raygun alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

![](../.gitbook/assets/screenshot_16_03_21__16_37.png)

2. Enter a name and select your desired escalation policy. Select "Raygun" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/screenshot_16_03_21__17_12.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the webhook integration in Raygun.

![](../.gitbook/assets/screenshot_16_03_21__17_13.png)

## In Raygun <a id="in-splunk"></a>

### Create a notification hook <a id="create-action-sequences"></a>

1. Go to Raygun, then to **Integrations** and click on the **Webhook** tile

![](../.gitbook/assets/screenshot_16_03_21__17_14.png)

2. On the next page,  paste the **Webhook URL** that you generated in iLert and lick on the **Save** button

![](../.gitbook/assets/screenshot_16_03_21__17_17.png)

Finished! Your Raygun crash reports will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an alert has been completed in Raygun, the associated incident in iLert will be resolved automatically.

**Can I connect Raygun with multiple alert sources from iLert?**

No

