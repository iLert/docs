---
title: Grafana Integration
seoTitle: 'iLert: Grafana Integration for Alerting | Incident Response | Uptime'
description: Create incidents in iLert from Grafana alerts.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Grafana Integration



## In iLert: Create Grafana alert source

1. **Go to the alert sources tab** and click on the "Create new alert source" button

2. Assign name and select escalation chain

3. In the field Integration type select **Grafana** and save.

![](../.gitbook/assets/gr1.png)

4. On the next page, a Webhook URL is generated. You will need this URL below when setting up in Grafana.

![](../.gitbook/assets/gr2.png)

## In Grafana: Add iLert Webhook as Alerting Channel <a id="add-webhook"></a>

1. Go to the sidebar tab Alerting → Notification channels and click on the green New channel button.

![](../.gitbook/assets/gr3.png)

2. Select **Type** webhook and in the field **Url** insert the webhookurl generated in iLert, Http Method should be set to "POST".

![](../.gitbook/assets/gr4.png)

3. Before you click on **Save** , you have the opportunity to test the integration. Click **Send Test**

![](../.gitbook/assets/gr5.png)

4. Check if an incident has been created in iLert.

5. After the Notification Channel has been created in Grafana, add it to one or more **graph alerts**.

6. Switch to any dashboard of your Grafana installation and edit a graph.

![](../.gitbook/assets/gr6.png)

7. In the edit view, open the **Alert** section via the left sidemenu and click on the green **Create Alert** button.

8. Fill in the desired **condition** and select the relevant iLert **Notification channel** under **Notifications → Send to** you created in steps 2 and 3. Do not forget to save the dashboard afterwards \(in the upper right Navibar\).

![](../.gitbook/assets/gr7.png)

9. The integration is now set up!

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an alert with "ok" has been resolved in Grafana, the associated incident in iLert will be resolved automatically.

**What happens when an alert is paused in Grafana, is the associated incident also accepted in iLert?**

Yes.

**Can I link Grafana to multiple alert sources in iLert?**

Yes, create a **Notification Channel** per alert source in Grafana.

