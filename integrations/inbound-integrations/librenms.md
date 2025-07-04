---
description: >-
  Learn how to connect LibreNMS with ilert to automatically trigger alerts and
  manage incident response through on-call schedules and multi-channel
  notifications.
---

# LibreNMS Integration

[LibreNMS](https://www.librenms.org/) is an open-source network monitoring system that offers auto-discovery, alerting, and performance graphing for a wide range of network devices. With the ilert integration, LibreNMS can automatically send alerts to ilert to trigger incident notifications and ensure timely response from your on-call team.

## In ilert: Create a LibreNMS alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **LibreNMS** in the search field, click the LibreNMS tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (7).png" alt=""><figcaption></figcaption></figure>

## In LibreNMS: Create an Alert Transport

1. In the navigation bar, click **Alerts** **->** **Alert Transports**.

<figure><img src="../../.gitbook/assets/1 (22).png" alt=""><figcaption></figcaption></figure>

2. Now click on **Create alert transport**.

<figure><img src="../../.gitbook/assets/2 (20).png" alt=""><figcaption></figcaption></figure>

3. Enter a **Transport name** and choose 'ilert' as **Transport type**.
4. Enter the **Integration Key** of the previously created alert source in ilert.
5. Click on Save Transport to finish the setup.

<figure><img src="../../.gitbook/assets/3 (17).png" alt=""><figcaption></figcaption></figure>

## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as LibreNMS sends an event with the eventType of 'RESOLVE', the corresponding alert in ilert will be resolved.

**Will alerts in ilert be acknowledged automatically?**

Yes, as soon as LibreNMS sends an event with the eventType of 'ACCEPT', the corresponding alert in ilert will be resolved.
