---
description: >-
  StatusHub is a tool for efficient and flexible communication during incidents
  and maintenance events. Display the information about the status of observed
  Website or API Endpoint.
---

# StatusHub Integration

## In iLert

1. Go to the "**Alert sources**" tab and click "**Create new alert source**"

![](../.gitbook/assets/ilert-create-alert%20%281%29.png)

1. Enter a name and select your desired escalation policy.   

   Select "StatusHub" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/ilert-statushub.png)

1. On the next page, an **StatusHub URL** is generated. You will need the URL for the webhook configuration

![](../.gitbook/assets/ilert-url%20%282%29.png)



## In Statushub

1. Navigate to StatusHub Dashboard or go to your StatusHub Page \(If you navigate to StatusHub Page, skip to step 2\)

![](../.gitbook/assets/statushub-statuspageadmin.png)

1. On your StatusHub Page, click on **Subscribe** on the top right

![](../.gitbook/assets/statushub-statuspage.png)

1. Click **Webhook** on the Subscribe Page

![](../.gitbook/assets/statushub-subscribe.png)

1. Use the **StatusHub URL** that you generated in iLert and paste it in the URL field, and make sure the Content Type is **JSON**

![](../.gitbook/assets/statushub-subscribewebhook.png)

1. On the Customization you can leave it as it is and click **Save**

![](../.gitbook/assets/statushub-customization.png)

1. To trigger the Incident in iLert, just create an Incident from StatusHub Dashboard

![](../.gitbook/assets/statushub-incident.png)

1. The Incident will be created in iLert automatically upon creating an Incident in StatusHub

