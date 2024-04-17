---
description: >-
  With the ilert Terraform Cloud integration, you can create alerts in ilert
  based on Terraform Cloud runs.
---

# Terraform Cloud / Terraform Enterprise

## In ilert: Create a Terraform Cloud alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Terraform Cloud** in the search field, click on the Terraform Cloud tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Terraform Cloud / Terraform Enterprise: Create a notification setting <a href="#in-splunk" id="in-splunk"></a>

1. Go to Terraform Cloud and then to **Your Workspace -> Settings -> Notifications**

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_22\_59.png)

2. On the next page, click on the **Create a Notification** button

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_23\_03.png)

3. On the next page, name the notification setting e.g. ilert, paste the **Webhook URL** that you generated in ilert, in the **Triggers** section choose **Only certain events** and select **Completed** and **Errored** options, then click on the **Create a Notification** button

![](../.gitbook/assets/Screenshot\_25\_02\_21\_\_23\_06.png)

4. Finished! Your Terraform Cloud run problems will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert has been completed in Terraform Cloud, the associated alert in ilert will be resolved automatically.

**Can I connect Terraform Cloud with multiple alert sources from ilert?**

Yes, simply add more notification settings in Terraform Cloud.
