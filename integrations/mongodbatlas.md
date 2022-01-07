---
description: >-
  MongoDB Atlas is a fully-managed cloud database that handles all the
  complexity of deploying, managing, and deployments to the preferred cloud
  service provider  (AWS , Azure, and GCP).
---

# MongoDB Atlas Integration

## In iLert

* Go to the "**Alert sources**" tab and click "**Create new alert source**"

![](<../.gitbook/assets/ilert-create-alert (5).png>)

* Enter a name and select your desired escalation policy.  &#x20;
* Select "**MongoDB Atlas**" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/mongodb\_alertsource.png)

* On the next page a **MongoDB Atlas URL** is generated. You will need the URL for the webhook configuration

![](<../.gitbook/assets/mongodb\_apikey (1).png>)

## In MongoDB Atlas

* In the Project page, click the **Bell (Notification) Icon** on top right.

![](../.gitbook/assets/mongodb\_project\_alert.png)

* Add Webhook Settings in Integration if it was not configured, by clicking **Integrations** and add the Webhook Settings (there can only be one Webhook).

![](../.gitbook/assets/mongodb\_project\_webhook.png)

* Create the Alert by navigating to **Alert -> Add New Alert**. From here any alerts can be added, and make sure that it sends the Alert to the Webhook.

![](../.gitbook/assets/mongodb\_project\_addalert.png)

* If the Alert has been configured, it should show up in the **Alert Settings** tab and the Alert should be created in iLert.

![](../.gitbook/assets/mongodb\_project\_alertsettings.png)

