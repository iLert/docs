---
description: >-
  Create ilert alerts from HashiCorp Consul Health Check events and get alerted
  through ilert for high priority issues.
---

# HashiCorp Consul

| ![](<../../.gitbook/assets/Consul Cloud Verified Badge_Small (1).png>) | [HashiCorp Consul](https://www.consul.io/) is a service mesh solution providing a full featured control plane with service discovery, configuration, and segmentation functionality. This integration creates based on Consul health checks. |
| ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## In ilert: Create a HashiCorp Consul alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **HashiCorp Consul** in the search field, click on the HashiCorp Consul tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Consul Server: Configure Consul-Alerts <a href="#in-topdesk" id="in-topdesk"></a>

1. Install Consul-Alerts as per the guide at [https://github.com/iLert/consul-alerts/blob/master/README.md](https://github.com/iLert/consul-alerts/blob/master/README.md)
2. Once the Consul-Alerts are running, we can set the ilert integration key using curl.

```bash
curl -X PUT -d 'YOUR_API_KEY' http://localhost:8500/v1/kv/consul-alerts/config/notifiers/ilert/api-key
```

3. Enable ilert notifications in Consul-Alerts.

```bash
curl -X PUT -d 'true' http://localhost:8500/v1/kv/consul-alerts/config/notifiers/ilert/enabled
```

4. (Optional) Generating a test alert by having a health check fail to confirm the integration is working.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, Consul-Alerts will resolve the ilert alert once health checks are passing.

**Will alerts in ilert be accepted automatically?**

No, unfortunately Consul events are not compatible with ilert accept events.

**Can I connect Consul Server with multiple alert sources from ilert?**

No, Consul-Alerts only supports sending alerts to a single alert source.
