---
description: >-
  The ilert InfluxDB Integration helps you to easily connect ilert with
  InfluxDB.
---

# InfluxDB Integration

[InfluxDB](https://www.influxdata.com) is an open-source time series database designed to handle high write and query loads, ideal for storing and analyzing time-stamped data such as metrics, events, and real-time analytics. It provides features like built-in time-stamping, data retention policies, and support for various data visualization tools, making it a popular choice for monitoring applications, IoT, and performance metrics.

## In ilert: Create an InfluxDB alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **InfluxDB** in the search field, click the InfluxDB tile, and click **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click on **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated, which you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>



## In InfluxDB: Add ilert Webhook as Notification Endpoint

1. On the sidebar, click **Alerts**.

<figure><img src="../../.gitbook/assets/1 (4).png" alt="" width="563"><figcaption></figcaption></figure>

2. Click **Notification Endpoints -> Create**.

<figure><img src="../../.gitbook/assets/2 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

3. Set HTTP as Destination and enter a Name.
4. Under **HTTP Options**, set **HTTP Method** to POST and enter the previously generated in ilert alert source URL into the **URL**.
5. Click **Create Notification Endpoint** to save.

<figure><img src="../../.gitbook/assets/3-2 (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

6. Navigate to **Checks -> Create** (this documentation uses threshold checks).

<figure><img src="../../.gitbook/assets/4-1.png" alt="" width="563"><figcaption></figcaption></figure>

7. Set a **Name** for your check.
8. Now select a metric you want to create a check for.
9. Click on **2. Configure Check** to set up the threshold.

<figure><img src="../../.gitbook/assets/5 (2).png" alt="" width="563"><figcaption></figcaption></figure>

10. Set up some thresholds.

{% hint style="info" %}
We recommend that you create a threshold for setting the check status to '**OK'** as it is necessary to resolve corresponding alerts in ilert.
{% endhint %}

<figure><img src="../../.gitbook/assets/6 (2).png" alt="" width="563"><figcaption></figcaption></figure>

11. Click on the blue tick in the top right corner to save the check.
12. Now navigate to **Notification Rules -> Create**.

<figure><img src="../../.gitbook/assets/4 (1) (1) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

13. Add the following Notification Rules:

{% tabs %}
{% tab title="CRIT" %}
<figure><img src="../../.gitbook/assets/7 (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="WARN" %}
<figure><img src="../../.gitbook/assets/8 (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="OK" %}
<figure><img src="../../.gitbook/assets/9 (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

14. Save the Notification Rule(s).

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, if you created a threshold and a notification rule for the 'OK' status, corresponding alerts will be resolved automatically.
