---
description: >-
  StatusHub is a tool for efficient and flexible communication during incidents
  and maintenance events. Display the information about the status of observed
  Website or API Endpoint.
---

# StatusHub Integration

## In ilert: Create StatusHub alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **StatusHub** in the search field, click on the StatusHub tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Statushub

1. Navigate to StatusHub Dashboard or go to your StatusHub Page (If you navigate to StatusHub Page, skip to step 2)

![](../.gitbook/assets/statushub-statuspageadmin.png)

2. On your StatusHub Page, click on **Subscribe** on the top right

![](../.gitbook/assets/statushub-statuspage.png)

3. Click **Webhook** on the Subscribe Page

![](../.gitbook/assets/statushub-subscribe.png)

4. Use the **StatusHub URL** that you generated in ilert and paste it in the URL field, and make sure the Content Type is **JSON**

![](../.gitbook/assets/statushub-subscribewebhook.png)

5. On the Customization you can leave it as it is and click **Save**

![](../.gitbook/assets/statushub-customization.png)

6. To trigger the Incident in ilert, just create an Incident from StatusHub Dashboard

![](../.gitbook/assets/statushub-incident.png)

7. The Incident will be created in ilert automatically upon creating an Incident in StatusHub
