---
title: Grafana Integration
seoTitle: 'iLert: Grafana Integration for Alerting | Incident Response | Uptime'
date: '2018-12-29T05:02:05.000Z'
weight: 1
description: Create alerts in iLert from Grafana alerts.
---

# Grafana Integration

## In iLert: Create Grafana alert source

1. Go to A**lert sources** and click on the **Create new alert source** button
2. Set a name for your Grafana alert sourc and select an escalation policy
3. In the field Integration type select **Grafana** and save.

![](../.gitbook/assets/gr1.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up in Grafana.

![](../.gitbook/assets/gr2.png)

## In Grafana: Add iLert Webhook as Alerting Channel <a href="#add-webhook" id="add-webhook"></a>

1. In the sidebar, go to **Alerting** → **Notification channels** and click on the **New channel** button.

![](../.gitbook/assets/gr3.png)

1. Select **Type** webhook and in the field **URL** insert the webhookurl generated in iLert. Set the HTTP Method to **POST**.

![](../.gitbook/assets/gr4.png)

1. Optionally test the integration by cliking on the **Send Test** button. Click on **Save**

![](../.gitbook/assets/gr5.png)

1. Check if an alert has been created in iLert.
2. After the Notification Channel has been created in Grafana, add it to one or more **graph alerts**.
3. Switch to any dashboard of your Grafana installation and edit a graph.

![](../.gitbook/assets/gr6.png)

1. In the edit view, open the **Alert** section via the left sidemenu and click on the green **Create Alert** button.
2. Fill in the desired **condition** and select the relevant iLert **Notification channel** under **Notifications → Send to** you created in steps 2 and 3. Do not forget to save the dashboard afterwards (in the upper right Navibar).

![](../.gitbook/assets/gr7.png)

1. The integration is now set up!

## In Grafana 9: Add iLert Webhook as Alerting Channel

1. In the sidebar, go to **Alerting** -> **Contact points** and click on the **New contact point button.**

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 16.31.10.png" alt=""><figcaption></figcaption></figure>

2\. Select **Contact point type** Webhook and in the field **URL** insert the webhookurl generated in iLert. Set the HTTP Method to **POST**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 16.50.25.png" alt=""><figcaption></figcaption></figure>

3\. Optionally test the integration by clicking on the **Test** button. Click on **Save contact point**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 16.52.38.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 16.53.35.png" alt=""><figcaption></figcaption></figure>

4\. Check if an alert has been created in iLert.

5\. After the Contact Point has been created in Grafana 9, switch to any dashboard of your Grafana 9 installation and edit a graph.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 17.05.28.png" alt=""><figcaption></figcaption></figure>

6\. In the edit view, open the **Alert** section via the left sidemenu and click on the blue **Create alert rule from this panel** button.

7\. Fill in the desired **Conditions**.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 18.12.58.png" alt=""><figcaption></figcaption></figure>

8\. Enter a **Rule name** and a **Group** name for your alert rule. Afterwards select a **Folder** for your alert rule to be stored in.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 17.27.16.png" alt=""><figcaption></figcaption></figure>

9\. Enter a **Description** and a **Summary** to your alert rule by clicking on the grey Add info button.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 18.23.07.png" alt=""><figcaption></figcaption></figure>

10\. Create custom **Labels** to identify the alert rule.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 17.28.12.png" alt=""><figcaption></figcaption></figure>

11\. To save the alert rule, click on the blue **Save** button located on the top right corner.

12\. After the Alert rule has been created in Grafana 9, create a new Notification policy by clicking on **Notification policies** tab -> **New specific policy**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 17.12.12.png" alt=""><figcaption></figcaption></figure>

13\. Add the created customised **Labels** in **step 10** and choose the **Contact point** created in **step 3**. Save the notification policy by clicking on the **Save policy** button.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-08 at 17.14.26.png" alt=""><figcaption></figcaption></figure>

14\. The integration is now set up!

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an alert with "ok" has been resolved in Grafana, the associated alert in iLert will be resolved automatically.

**What happens when an alert is paused in Grafana, is the associated alert also accepted in iLert?**

Yes.

**Can I link Grafana to multiple alert sources in iLert?**

Yes, create a **Notification Channel** per alert source in Grafana.
