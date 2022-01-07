---
description: >-
  StatusHub is a tool for efficient and flexible communication during incidents
  and maintenance events. Display the information about the status of observed
  Website or API Endpoint.
---

# StatusHub Integration

## In iLert

* Go to the "**Alert sources**" tab and click "**Create new alert source**"

![](<../.gitbook/assets/ilert-create-alert (1).png>)

* Enter a name and select your desired escalation policy.  &#x20;
* Select "StatusHub" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/ilert-statushub.png)

* On the next page, an **StatusHub URL** is generated. You will need the URL for the webhook configuration

![](<../.gitbook/assets/ilert-url (1).png>)



## In Statushub

* Navigate to StatusHub Dashboard or go to your StatusHub Page (If you navigate to StatusHub Page, skip to step 2)

![](../.gitbook/assets/statushub-statuspageadmin.png)

* On your StatusHub Page, click on **Subscribe** on the top right

![](../.gitbook/assets/statushub-statuspage.png)

* Click **Webhook** on the Subscribe Page

![](../.gitbook/assets/statushub-subscribe.png)

* Use the **StatusHub URL** that you generated in iLert and paste it in the URL field, and make sure the Content Type is **JSON**

![](../.gitbook/assets/statushub-subscribewebhook.png)

* On the Customization you can leave it as it is and click **Save**

![](../.gitbook/assets/statushub-customization.png)

* To trigger the Incident in iLert, just create an Incident from StatusHub Dashboard

![](../.gitbook/assets/statushub-incident.png)

* The Incident will be created in iLert automatically upon creating an Incident in StatusHub
