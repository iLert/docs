# VictoriaMetrics Integration

[VictoriaMetrics](https://victoriametrics.com/) is a high-performance, scalable time series database that is designed for monitoring large-scale environments and efficiently storing and querying large volumes of metrics data.

## In ilert: Create a VictoriaMetrics alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **VictoriaMetrics** in the search field, click the VictoriaMetrics tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>



## In Prometheus Alertmanager  <a href="#create-alert-source" id="create-alert-source"></a>

> In order to be able to use VictoriaMetrics alerts and receive notifications, you need first configure and start alertmanager

1. Install Prometheus Alertmanager in any way that suits your needs. For more information about the alertmanager installation process please visit [https://prometheus.io/docs/alerting/latest/alertmanager/](https://prometheus.io/docs/alerting/latest/alertmanager/)
2. Configure Alertmanager receivers in order to inform ilert every time there's an alert. In the example below replace the previously created VictoriaMetrics URL:

{% code title="alertmanager.yaml" lineNumbers="true" %}
```yaml
route:
  receiver: ilert

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

## In VictoriaMetrics <a href="#create-alert-source" id="create-alert-source"></a>

1. Configure the `vmalert` alert rules in order to trigger alerts regarding the rule expression. For example:

```yaml
groups:
  - name: vm-health
    rules:
      - alert: TooManyRestarts
        expr: changes(process_start_time_seconds{job=~".*(victoriametrics|vmselect|vminsert|vmstorage|vmagent|vmalert|vmsingle|vmalertmanager|vmauth).*"}[2m]) > 2
        labels:
          severity: critical
        annotations:
          summary: "{{ $labels.job }} too many restarts (instance {{ $labels.instance }})"
          description: "Job {{ $labels.job }} (instance {{ $labels.instance }}) has restarted more than twice in the last 15 minutes.
            It might be crashlooping."
```

2. Configure `vmalert`:

```sh
./bin/vmalert -rule=alert.rules \            # Path to the file with rules configuration. Supports wildcard
    -datasource.url=http://localhost:8428 \  # Prometheus HTTP API compatible datasource
    -notifier.url=http://localhost:9093 \    # AlertManager URL (required if alerting rules are used)
    -notifier.url=http://127.0.0.1:9093 \    # AlertManager replica URL
    -remoteWrite.url=http://localhost:8428 \ # Remote write compatible storage to persist rules and alerts state info (required if recording rules are used)
    -remoteRead.url=http://localhost:8428 \  # Prometheus HTTP API compatible datasource to restore alerts state from
    -external.label=cluster=east-1 \         # External label to be applied for each rule
    -external.label=replica=a                # Multiple external labels may be set
```



## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the Alertmanager sends a "RESOLVE" event, the associated alert is automatically resolved in ilert.
