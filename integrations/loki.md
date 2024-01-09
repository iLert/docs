# Loki integration

[Loki](https://grafana.com/oss/loki/) is a horizontally scalable, highly available, multi-tenant log aggregation system inspired by [Prometheus](https://prometheus.io/).

{% hint style="info" %}
You can use our [example prometheus setup](https://github.com/iLert/prometheus-integration-docs) to test the Loki integration&#x20;
{% endhint %}

## In ilert <a href="#create-alert-source" id="create-alert-source"></a>

## Create a Loki alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to **Alert sources** -> **Alert sources** and click on **Create new alert source**\


<figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>

1.  Search for **Loki** in the search field, click on the Loki tile, and click on **Next**. \


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
2. Give your alert source a name, optionally assign teams, and click **Next**.
3.  Select an **escalation policy** by creating a new one or assigning an existing one.\


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
4.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later. \


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
5. The next page shows additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
6. On the final page, a Loki URL will be generated that you will need later in this guide.

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

## In Prometheus Alertmanager  <a href="#create-alert-source" id="create-alert-source"></a>

> In order to be able to use Loki alerts and receive notifications, you need first configure and start alertmanager

1. Install Prometheus Alertmanager in any way that suits your needs. For more information about the alertmanager installation process please visit [https://prometheus.io/docs/alerting/latest/alertmanager/](https://prometheus.io/docs/alerting/latest/alertmanager/)
2. Configure Alertmanager receivers in order to inform ilert every time there's an alert. In the example below replace the previously created Loki URL:

{% code title="alertmanager.yaml" lineNumbers="true" %}
```yaml
receivers:
  - name: "ilert"
    webhook_configs:
      - url: "<your alert source url here>"
        send_resolved: true
```
{% endcode %}

{% hint style="info" %}
You could also split alert to high and low priority by creating two alert sources accordingly
{% endhint %}

<pre class="language-yaml" data-title="alertmanager.yaml" data-line-numbers><code class="lang-yaml"><strong>receivers:
</strong>  - name: "high-priority"
    webhook_configs:
      # high priority alert source url
      - url: "&#x3C;your high priority alert source url here>"
        send_resolved: true
  - name: "low-priority"
    webhook_configs:
      # low priority alert source url
      - url: "&#x3C;your low priority alert source url here>"
        send_resolved: true
</code></pre>

## In Loki  <a href="#create-alert-source" id="create-alert-source"></a>

1. Install Loki in any way that suits your needs.&#x20;
2. Configure the Loki alert rules in order to trigger alerts regarding the rule expression. For example:

{% code title="mimir-alert-rules.yaml" lineNumbers="true" %}
```yaml
groups:
  - name: mimir-critical
    rules:
      - alert: MimirIngesterUnhealthy
        expr: |
          min by (cluster, namespace) (cortex_ring_members{state="Unhealthy", name="ingester"}) > 0
        for: 15m
        labels:
          severity: critical
        annotations:
          summary: Mimir cluster has unhealthy ingesters alert
          description: "Mimir cluster has unhealthy ingesters \n  VALUE = {{ $value }}\n  LABELS = {{ $labels }}"
```
{% endcode %}

3. Configure the Loki ruler to send alerts to an external alertmanager and point the alert rules folder:

<pre class="language-yaml" data-title="mimir-config.yaml" data-line-numbers><code class="lang-yaml"><strong>ruler:
</strong>  alertmanager_url: http://alertmanager:9093
  enable_api: true

ruler_storage:
  backend: local
  local:
    directory: /etc/alertmanager
</code></pre>

## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the Alertmanager sends a "RESOLVE" event, the associated alert is automatically resolved in ilert.

