---
description: Create alerts in iLert from Prometheus Alertmanager alerts
---

# Prometheus Integration

[Prometheus](https://github.com/prometheus) is an open-source systems monitoring and alerting toolkit that uses a pull-based approach to collecting metrics in a timeseries database.

With iLert's Prometheus integration, you can automatically create alerts in iLert using the Prometheus' Alertmanager. That way, you will never miss a critical alert and always alert the right person using iLert's on-call schedules, automatic escalation, and multiple alerting channels. When the Alertmanager triggers an alert, iLert will alert the on-call person through their preferred channel, including SMS, phone calls, push notifications and Slack. iLert will automatically escalate to the next person, if the alert is not acknowledged. iLert also lets you define alerting rules based on support hours and delay alerts until your support hours start.

## System Requirements <a href="#requirements" id="requirements"></a>

* [Prometheus Alert Manager v0.6.0 / 2017-04-25](https://github.com/prometheus/alertmanager/releases/tag/v0.6.0) or higher. If you are using an older version of the Alertmanager, please contact the iLert support at [support@ilert.com](mailto:support@ilert.com).

## In iLert: Create Prometheus alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to **Services** --> **Alert sources** and click on **Create new alert source**
2. Give it a name and chose an escalation policy
3. Select Prometheus as the **Integration type**

![](<../.gitbook/assets/Screenshot 2021-04-26 at 13.04.18.png>)

1. A webhook URL will be generated on the next page. You will need this URL later in Prometheus.

![](<../.gitbook/assets/Screenshot 2021-04-26 at 13.05.18.png>)

## In Prometheus Alertmanager: add webhook receiver <a href="#add-webhook" id="add-webhook"></a>

1. Add a [Webhook configuration](https://prometheus.io/docs/alerting/configuration/#webhook\_config) from the alert manager in the configuration file. Use the URL generated in iLert as the Webhook URL:

```yaml
receivers:
- name: 'ilert.web.hook'
  webhook_configs:
  - url: 'https://api.ilert.com/api/v1/events/prometheus/e6bcfcbf-a38f-462a-af9d-1687809b7594'
```

1. You can now configure any route in the Alert Manager. In the following example, all alerts that do not match another [route](https://prometheus.io/docs/alerting/configuration/#route) are sent to iLert:

```yaml
route:
group_by: ['alertname']
group_wait: 10s
group_interval: 10s
repeat_interval: 1h
receiver: 'ilert.web.hook'
```

1. Restart the alert manager
2. Optional: Send a test alert through the [Alert Manager API](https://prometheus.io/docs/alerting/clients/).

```bash
curl -d '[{"labels":{"Alertname":"iLert Test"},"annotations":{"summary":"iLert Test"}}]' http://localhost:9093/api/v1/alerts
```

## Dynamic policy routing



iLert's Prometheus integration supports dynamic escalation policy routing with the help of routing keys.

In iLert navigate to the **escalation policies** that you want to route to and enter a unique routing key for for each policy.

![](<../.gitbook/assets/image (55) (1) (1).png>)

In your Prometheus **alert rule** yml add a label called `ilert_routingkey` and set its value to the policy's routing key that you want to assign to the alert e.g. `ilert_routingkey: policy1`

When iLert receives Prometheus alert events it will look for the first alert with the specific label and decide upon the routing. If the label is not present the escalation policy that is assigned to the alert source is used instead.

## FAQ <a href="#faq" id="faq"></a>

****

**Will alerts in iLert be resolved automatically?**

Yes, Prometheus also sends resolved events by default, as long as the send\_resolved: false option is NOT set in the [Webhook configuration](https://prometheus.io/docs/alerting/configuration/#webhook\_config) of the alert manager. Furthermore, resolved events - just like firing events - are not sent until the next `group_interval` configuration in the alert manager.

**Can I link Prometheus to multiple alert sources in iLert?**

Yes, create several Webhook receivers in Prometheus and enter the URL of the alert source from iLert in the Webhook URL.

**What if my internet connection is interrupted? Are the alerts generated in Prometheus lost?**

No, alerts are not lost. The alert manager has a retry mechanism. In addition, we recommend that you monitor your Internet connection with an external monitoring service (e.g. using [iLert's heartbeat feature](../getting-started/heartbeat-monitoring/) or uptime monitoring). See here for a [Prometheus Heartbeat Example](../getting-started/heartbeat-monitoring/prometheus-heartbeat-example.md).

**Not all Prometheus Alerts alerts are created in iLert. Why?**

The alerts from Prometheus are grouped and sent to iLert and bundled in an alert. Grouping is affected by the `group_by` configuration in the Alert Manager route.

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

**The integration does not work. How do I find the issue?**

First, look in the log file of the alert manager. If you can not find the issue, please contact our support at [support@ilert.com](https://github.com/iLert/docs/tree/dfe03283a452516a115a55f8c20942698e279d7b/integrations/support@ilert.com).
