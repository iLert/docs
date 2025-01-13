---
description: >-
  MongoDB Atlas is a fully-managed cloud database that handles all the
  complexity of deploying, managing, and deployments to the preferred cloud
  service provider  (AWS , Azure, and GCP).
---

# MongoDB Atlas Integration

## In ilert: Create a MongoDB Atlas alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **MongoDB Atlas** in the search field, click on the MongoDB Atlas tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In MongoDB Atlas

1. In the Project page, click the **Bell (Notification) Icon** on top right.

![](../../.gitbook/assets/mongodb_project_alert.png)

2. Add Webhook Settings in Integration if it was not configured, by clicking **Integrations** and add the Webhook Settings (there can only be one Webhook).

![](../../.gitbook/assets/mongodb_project_webhook.png)

3. Create the Alert by navigating to **Alert -> Add New Alert**. From here any alerts can be added, and make sure that it sends the Alert to the Webhook.

![](../../.gitbook/assets/mongodb_project_addalert.png)

4. If the Alert has been configured, it should show up in the **Alert Settings** tab and the Alert should be created in ilert.

![](../../.gitbook/assets/mongodb_project_alertsettings.png)
