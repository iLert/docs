---
description: >-
  With the ilert Senty integration, you can create alerts in ilert based on
  Sentry issues.
---

# Sentry Integration

Sentry's platform helps developers diagnose, fix, and optimize the performance of their code.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Sentry alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Sentry" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_21\_51.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in Sentry.

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_21\_52.png)

## In Sentry <a href="#in-splunk" id="in-splunk"></a>

### Create a search <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Sentry and then to **Settings -> Developer Settings**, then click on the **New Internal Integration**

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_21\_58.png)

1. On the next page,  **name** the integration e.g. ilert, paste the **Webhook URL** that you generated in ilert, enable **Alert Rule Action** option, give the read access to **Issue & Event** and in the **Webhooks** section choose **Issue** option, then click on **Save**

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_22\_53.png)

1. Go to **Alerts** and click on **Create Alert Rule**

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_22\_08.png)

1. On the next page,  **name** the alert rule e.g. ilert, in the **Then perform these actions** section choose **Send a notification via an  integration** and choose ilert, then click on **Create Alert Rule** button

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_22\_10.png)

Finished! Your Sentry alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert has been resolved or ignored in Sentry, the associated alert in ilert will be resolved automatically.

**Can I connect Sentry with multiple alert sources from ilert?**

Yes, simply add more alert rules in Sentry.
