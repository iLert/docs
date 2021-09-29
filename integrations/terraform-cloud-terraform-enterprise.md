---
description: >-
  With the iLert Terraform Cloud integration, you can create alerts in iLert
  based on Terraform Cloud runs.
---

# Terraform Cloud / Terraform Enterprise

## In iLert <a id="in-ilert"></a>

### Create a Terraform Cloud alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Terraform Cloud" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/screenshot_25_02_21__22_56.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the notification in Terraform Cloud.

![](../.gitbook/assets/screenshot_25_02_21__22_57.png)

## In Terraform Cloud / Terraform Enterprise <a id="in-splunk"></a>

### Create a notification setting <a id="create-action-sequences"></a>

1. Go to Terraform Cloud and then to **Your Workspace -&gt; Settings -&gt; Notifications**

![](../.gitbook/assets/screenshot_25_02_21__22_59.png)

2. On the next page,  click on the **Create a Notification** button

![](../.gitbook/assets/screenshot_25_02_21__23_03.png)

3. On the next page, name the  notification setting e.g. iLert, paste the **Webhook URL** that you generated in iLert, in the **Triggers** section choose **Only certain events** and select **Completed** and **Errored** options, then click on the **Create a Notification** button

![](../.gitbook/assets/screenshot_25_02_21__23_06.png)

Finished! Your Terraform Cloud run problems will now create alerts in iLert.

## FAQ <a id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an alert has been completed in Terraform Cloud, the associated alert in iLert will be resolved automatically.

**Can I connect Terraform Cloud with multiple alert sources from iLert?**

Yes, simply add more notification settings in Terraform Cloud.

