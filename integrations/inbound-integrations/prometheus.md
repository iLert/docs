---
description: Create alerts in ilert from Prometheus Alertmanager alerts
---

# Prometheus Integration

[Prometheus](https://github.com/prometheus) is an open-source systems monitoring and alerting toolkit that uses a pull-based approach to collecting metrics in a timeseries database.

With ilert's Prometheus integration, you can automatically create alerts in ilert using the Prometheus' Alertmanager. That way, you will never miss a critical alert and always alert the right person using ilert's on-call schedules, automatic escalation, and multiple alerting channels. When the Alertmanager triggers an alert, ilert will alert the on-call person through their preferred channel, including SMS, phone calls, push notifications and Slack. ilert will automatically escalate to the next person, if the alert is not acknowledged. ilert also lets you define alerting rules based on support hours and delay alerts until your support hours start.

## System Requirements <a href="#requirements" id="requirements"></a>

* [Prometheus Alert Manager v0.6.0 / 2017-04-25](https://github.com/prometheus/alertmanager/releases/tag/v0.6.0) or higher. If you are using an older version of the Alertmanager, please contact the ilert support at [support@ilert.com](mailto:support@ilert.com).

## In ilert: Create a Prometheus alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**\


    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Prometheus** in the search field, click on the Prometheus tile and click on **Next**. \


    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.\


    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later. \


    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.



    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Prometheus Alertmanager: add a webhook receiver <a href="#add-webhook" id="add-webhook"></a>

1\. Add a [Webhook configuration](https://prometheus.io/docs/alerting/configuration/#webhook_config) from the alert manager in the configuration file. Use the URL generated in ilert as the Webhook URL:

```yaml
receivers:
- name: 'ilert.web.hook'
  webhook_configs:
  - url: 'https://api.ilert.com/api/v1/events/prometheus/e6bcfcbf-a38f-462a-af9d-1687809b7594'
```

2\. You can now configure any route in the Alert Manager. In the following example, all alerts that do not match another [route](https://prometheus.io/docs/alerting/configuration/#route) are sent to ilert:

```yaml
route:
group_by: ['alertname']
group_wait: 10s
group_interval: 10s
repeat_interval: 1h
receiver: 'ilert.web.hook'
```

3\. Restart the alert manager

4\. Optional: Send a test alert through the [Alert Manager API](https://prometheus.io/docs/alerting/clients/).

```bash
curl -d '[{"labels":{"Alertname":"iLert Test"},"annotations":{"summary":"iLert Test"}}]' http://localhost:9093/api/v1/alerts
```

## Dynamic policy routing

ilert's Prometheus integration supports dynamic escalation policy routing with the help of routing keys.

In ilert navigate to the **escalation policies** that you want to route to and enter a unique routing key for for each policy.

![](<../../.gitbook/assets/image (55) (1) (1).png>)

In your Prometheus **alert rule** yml add a label called `ilert_routingkey` and set its value to the policy's routing key that you want to assign to the alert e.g. `ilert_routingkey: policy1`

When ilert receives Prometheus alert events it will look for the first alert with the specific label and decide upon the routing. If the label is not present the escalation policy that is assigned to the alert source is used instead.

## Supported custom labels <a href="#faq" id="faq"></a>

* `gcp_project` will be automatically added to the alert summary
* `url` may be used to add a custom link to the alert
* `urlLabel` may be used to set a defined label for the custom link (`url`)

{% hint style="info" %}
Note: for custom labels to be accepted they must be part of the **alert labels** of an alert in status **firing**
{% endhint %}

## FAQ <a href="#faq" id="faq"></a>

***

### **Will alerts in ilert be resolved automatically?**

Yes, Prometheus also sends resolved events by default, as long as the send\_resolved: false option is NOT set in the [Webhook configuration](https://prometheus.io/docs/alerting/configuration/#webhook_config) of the alert manager. Furthermore, resolved events - just like firing events - are not sent until the next `group_interval` configuration in the alert manager.

### **Can I link Prometheus to multiple alert sources in ilert?**

Yes, create several Webhook receivers in Prometheus and enter the URL of the alert source from ilert in the Webhook URL.

### **What if my internet connection is interrupted? Are the alerts generated in Prometheus lost?**

No, alerts are not lost. The alert manager has a retry mechanism. In addition, we recommend that you monitor your Internet connection with an external monitoring service (e.g. using [iLert's heartbeat feature](../../alerting/heartbeat-monitoring/) or uptime monitoring). See here for a [Prometheus Heartbeat Example](../../alerting/heartbeat-monitoring/prometheus-heartbeat-example.md).

### **Not all Prometheus Alerts alerts are created in ilert. Why?**

The alerts from Prometheus are grouped and sent to ilert and bundled in an alert. Grouping is affected by the `group_by` configuration in the Alert Manager route.

Example:

```
route:
  # The labels by which incoming alerts are grouped together. For example,
  # multiple alerts coming in for cluster=A and alertname=LatencyHigh would
  # be batched into a single group.
  #
  # To aggregate by all possible labels use '...' as the sole label name.
  # This effectively disables aggregation entirely, passing through all
  # alerts as-is. This is unlikely to be what you want, unless you have
  # a very low alert volume or your upstream notification system performs
  # its own grouping. Example: group_by: [...]
  group_by: ['alertname', 'cluster', 'service']
```

### **The integration does not work. How do I find the issue?**

First, look in the log file of the alert manager. If you can not find the issue, please contact our support at [support@ilert.com](https://github.com/iLert/docs/tree/dfe03283a452516a115a55f8c20942698e279d7b/integrations/support@ilert.com).

### How to setup multiple alert sources in the same config?

You can configure multiple alert sources for **different alerts** based on `routes` and conditions aka `matchers`. Make sure your `receivers` use the proper integration urls generated by ilert.

```
global: {}
receivers:
  - name: "alert-source-1"
    webhook_configs:
      - url: "alert-source-1-URL"
        send_resolved: true
  - name: "alert-source-2"
    webhook_configs:
      - url: "alert-source-2-URL"
        send_resolved: true

route:
  group_by: ["alertname", "cluster", "region"]
  group_wait: 10s
  group_interval: 5m
  repeat_interval: 1h
  receiver: alert-source-1
  routes:
    - receiver: "alert-source-1"
      matchers:
        - severity="warning"
    - receiver: "alert-source-2"
      matchers:
        - severity="critical"
```

Sending the **same alert** to multiple alert sources in **parallel**, is also possible if you use `continue`.

```
global: {}
receivers:
  - name: "alert-source-1"
    webhook_configs:
      - url: "alert-source-1-URL"
        send_resolved: true
  - name: "alert-source-2"
    webhook_configs:
      - url: "alert-source-2-URL"
        send_resolved: true

route:
  group_by: ["alertname", "cluster", "region"]
  group_wait: 10s
  group_interval: 5m
  repeat_interval: 1h
  receiver: alert-source-1
  routes:
    - receiver: "alert-source-1"
      continue: true
    - receiver: "alert-source-2"
```

## Further References <a href="#faq" id="faq"></a>

Here is the instruction on how to import metrics from Prometheus and display them on your ilert status page:

[Import metrics from Prometheus](https://docs.ilert.com/incident-comms-and-status-pages/metrics/import-metrics-from-prometheus)
