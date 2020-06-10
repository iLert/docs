---
title: Prometheus Integration
seoTitle: 'iLert: Prometheus Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert Prometheus Integration helps you to easily connect iLert with
  Prometheus.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Prometheus Integration

With Prometheus Integration, you can easily integrate Prometheus with iLert. That way, you can easily extend Prometheus with SMS, Push, Voice, and iLert rosters. Incidents are created in iLert and automatically closed when the problem is resolved. In addition, the iLert incidents created by Prometheus include bounce links to the Prometheus Alert Manager.

## System Requirements <a id="requirements"></a>

* [Prometheus Alert Manager v0.6.0 / 2017-04-25](https://github.com/prometheus/alertmanager/releases/tag/v0.6.0) or higher. If you are using an older version of the Alertmanager, please contact the iLert support at [support@ilert.com](mailto:support@ilert.com).

## In iLert: Create Prometheus alert source <a id="create-alarm-source"></a>

1. Switch to the tab "alert sources" and click on the button "Create new alert source"
2. Assign name and select escalation chain
3. Select and save in the **Prometheus** Integration Type field.
4. The next page will generate a URL. You will need this URL below when setting up in Prometheus

## In Prometheus Alertmanager: Add Webhook receiver <a id="add-webhook"></a>

1. Add a [Webhook configuration](https://prometheus.io/docs/alerting/configuration/#webhook_config) from the alert manager in the configuration file. Use the URL generated in iLert as the Webhook URL:

   \`\`\`

   receivers:

2. name: 'ilert.web.hook'

   webhook\_configs:

   * url: '[https://api.ilert.com/api/v1/events/prometheus/e6bcfcbf-a38f-462a-af9d-1687809b7594](https://api.ilert.com/api/v1/events/prometheus/e6bcfcbf-a38f-462a-af9d-1687809b7594)'

     \`\`\`

3. You can now configure any route in the Alert Manager. In the following example, all alerts that do not match another [route](https://prometheus.io/docs/alerting/configuration/#route) are sent to iLert:

   ```text
   route:
   group_by: ['alertname']
   group_wait: 10s
   group_interval: 10s
   repeat_interval: 1h
   receiver: 'ilert.web.hook'
   ```

4. Restart the alert manager
5. Optional: Send a test alert through the [Alert Manager API](https://prometheus.io/docs/alerting/clients/).

   ```text
   curl -d '[{"labels":{"Alertname":"iLert Test"},"annotations":{"summary":"iLert Test"}}]' http://localhost:9093/api/v1/alerts
   ```

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, Prometheus also sends resolved events by default, as long as the send\_resolved: false option is NOT set in the [Webhook configuration](https://prometheus.io/docs/alerting/configuration/#webhook_config) of the alert manager. Furthermore, resolved events - just like firing events - are not sent until the next `group_interval` configuration in the alert manager.

**Can I link Prometheus to multiple alert sources in iLert?**

Yes, create several Webhook receivers in Prometheus and enter the URL of the alert source from iLert in the Webhook URL.

**What if my internet connection is interrupted? Are the alerts generated in Prometheus lost?**

No, no alerts are lost. The alert manager has a retry mechanism. In addition, we recommend that you monitor your Internet connection with an external monitoring service \(e.g. using iLert's uptime monitoring\). You can send these alerts to iLert again.

**Not all Prometheus Alerts incidents are created in iLert. Why?**

The alerts from Prometheus are grouped sent to iLert and bundled in an incident. Grouping is affected by the `group_by` configuration in the Alert Manager route.

Example:

```text
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

**The integration does not work. How do I find the mistake?**

First, look in the log file of the alert manager. If you can not find the error, please contact our support at [support@ilert.com](support@ilert.com).

