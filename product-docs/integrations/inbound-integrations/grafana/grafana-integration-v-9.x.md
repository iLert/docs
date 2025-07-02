---
description: Create alerts in ilert from Grafana 9 alerts.
---

# Grafana Integration (v 9.x)

{% hint style="info" %}
Are you using Grafana 8.x or lower? Please refer to our [Grafana Integration](grafana-integration.md) guide.
{% endhint %}

## In ilert: Create a Grafana alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Grafana** in the search field, click on the Grafana tile and click on **Next**.&#x20;

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Grafana 9: Add ilert Webhook as Alerting Channel

1. In the sidebar, go to **Alerting** -> **Contact points** and click on the **New contact point button.**

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 16.31.10 (2).png" alt=""><figcaption></figcaption></figure>

2. Select **Contact point type** Webhook and in the field **URL** insert the webhookurl generated in ilert. Set the HTTP Method to **POST**.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 16.50.25.png" alt=""><figcaption></figcaption></figure>

3. Optionally test the integration by clicking on the **Test** button. Click on **Save contact point**.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 16.52.38.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 16.53.35.png" alt=""><figcaption></figcaption></figure>

4. Check if an alert has been created in ilert.
5. After the Contact Point has been created in Grafana 9, switch to any dashboard of your Grafana 9 installation and edit a graph.Screenshot 2022-09-08 at 17.05.28.png

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 17.05.28.png" alt=""><figcaption></figcaption></figure>

6. In the edit view, open the **Alert** section via the left sidemenu and click on the blue **Create alert rule from this panel** button.
7. Fill in the desired **Conditions**.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 18.12.58.png" alt=""><figcaption></figcaption></figure>

8. Enter a **Rule name** and a **Group** name for your alert rule. Afterwards select a **Folder** for your alert rule to be stored in.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 17.27.16.png" alt=""><figcaption></figcaption></figure>

9. Enter a **Description** and a **Summary** to your alert rule by clicking on the grey Add info button.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 18.23.07.png" alt=""><figcaption></figcaption></figure>

10. Create custom **Labels** to identify the alert rule.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 17.28.12.png" alt=""><figcaption></figcaption></figure>

11. To save the alert rule, click on the blue **Save** button located on the top right corner.
12. After the Alert rule has been created in Grafana 9, create a new Notification policy by clicking on **Notification policies** tab -> **New specific policy**.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 17.12.12.png" alt=""><figcaption></figcaption></figure>

13. Add the created customised **Labels** in **step 18** and choose the **Contact point** created in **step 2**. Save the notification policy by clicking on the **Save policy** button.

<figure><img src="../../../.gitbook/assets/Screenshot 2022-09-08 at 17.14.26.png" alt=""><figcaption></figcaption></figure>

14. The integration is now set up!

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert with "ok" has been resolved in Grafana, the associated alert in ilert will be resolved automatically.

**What happens when an alert is paused in Grafana, is the associated alert also accepted in ilert?**

Yes.

**Can I link Grafana to multiple alert sources in ilert?**

Yes, create a **Notification Channel** per alert source in Grafana.
