---
description: Create alerts in ilert from Grafana alerts.
---

# Grafana Integration

{% hint style="info" %}
Are you using Grafana v9.x or higher? Please refer our [Grafana Integration (v 9.x)](grafana-integration-v-9.x.md) guide.
{% endhint %}

## In ilert: Create Grafana alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Grafana** in the search field, click on the Grafana tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Grafana: Add ilert Webhook as Alerting Channel <a href="#add-webhook" id="add-webhook"></a>

1. In the sidebar, go to **Alerting** → **Notification channels** and click on the **New channel** button.

<figure><img src="../../.gitbook/assets/gr3.png" alt=""><figcaption></figcaption></figure>

2. Select **Type** webhook and in the field **URL** insert the webhookurl generated in ilert. Set the HTTP Method to **POST**.

<figure><img src="../../.gitbook/assets/gr4.png" alt=""><figcaption></figcaption></figure>

3. Optionally test the integration by cliking on the **Send Test** button. Click on **Save**

<figure><img src="../../.gitbook/assets/gr5.png" alt=""><figcaption></figcaption></figure>

4. Check if an alert has been created in ilert.
5. After the Notification Channel has been created in Grafana, add it to one or more **graph alerts**.
6. Switch to any dashboard of your Grafana installation and edit a graph.

<figure><img src="../../.gitbook/assets/gr6.png" alt=""><figcaption></figcaption></figure>

7. In the edit view, open the **Alert** section via the left sidemenu and click on the green **Create Alert** button.
8. Fill in the desired **condition** and select the relevant ilert **Notification channel** under **Notifications → Send to** you created in steps 2 and 3. Do not forget to save the dashboard afterwards (in the upper right Navibar).

<figure><img src="../../.gitbook/assets/gr7.png" alt=""><figcaption></figcaption></figure>

9. The integration is now set up!

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert with "ok" has been resolved in Grafana, the associated alert in ilert will be resolved automatically.

**What happens when an alert is paused in Grafana, is the associated alert also accepted in ilert?**

Yes.

**Can I link Grafana to multiple alert sources in ilert?**

Yes, create a **Notification Channel** per alert source in Grafana.
