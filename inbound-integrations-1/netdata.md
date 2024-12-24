---
description: >-
  ilert integrates with Netdata to provide real-time actionable alerts, enabling
  fast response and resolution via multiple notification channels.
---

# Netdata Integration

[Netdata](https://www.netdata.cloud/) is a high-performance, open-source monitoring tool that provides real-time insights into system and application metrics. It allows users to track and visualize performance data across distributed systems with minimal resource overhead. Pairing Netdata with ilert’s incident management platform enhances the monitoring experience by adding powerful alerting and incident response capabilities. Here is a step-by-step guide on how to connect Netdata with ilert.

## In ilert: Create a Netdata alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Netdata** in the search field, click the Netdata tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/1 (12).png" alt="" width="563"><figcaption></figcaption></figure>

## In Netdata: Configure Agent Dispatched Notification

1. Edit following configuration file: `health_alarm_notify.conf`
2. Open the terminal and enter following:

```bash
cd /etc/netdata 2>/dev/null || cd /opt/netdata/etc/netdata
sudo ./edit-config health_alarm_notify.conf
```

3. Insert the previous created alertsource URL as value for `ILERT_ALERT_SOURCE_URL`
4. Example:

```
SEND_ILERT="YES"
ILERT_ALERT_SOURCE_URL="https://api.ilert.com/api/v1/events/netdata/{API-KEY}"
```



## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as Netdata sends a notification with a severity value of **clear** or **resolved**, the alert in ilert will be resolved automatically.
