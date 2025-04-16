---
description: The simplest way to monitor service, device or workflow health.
---

# Heartbeat monitoring

ilert's heartbeat alert sources allow you to monitor services, devices, or workflows easily — depending only on an HTTPS outbound connection. It checks whether your systems or services are still running by expecting regular signals, and you get alerted automatically when those signals stop, indicating a failure or outage.&#x20;

To start monitoring via ilert heartbeat, log into your ilert account, click Alert sources, and find **Heartbeat monitors** in the dropdown menu. Then, click **Create heartbeat monitor**.

<figure><img src="../../.gitbook/assets/Heartbeat monitor 02.png" alt="ilert Heartbeat monitor creation"><figcaption></figcaption></figure>

Assing new monitor to the [team](https://docs.ilert.com/user-administration/teams), name it, and choose an [alert source](https://docs.ilert.com/alerting/alert-sources) that will trigger an alert if the heartbeat ping is overdue.&#x20;

Choose an interval after which the heartbeat will create an alert through the given alert source if it does not receive a response. You can choose between seconds, minutes, and hours.

Finally, provide a summary of the alert to help your team quickly identify the issue.

<figure><img src="../../.gitbook/assets/Heartbeat monitor 03.png" alt="Create a heartbeat monitor in ilert"><figcaption></figcaption></figure>

When ready, click **Create**. You will see the Monitor's details view, where the **integration URL** (API key) will be shown. You can use this key to call ping requests for your heartbeat alert source.

The heartbeat timer starts once the first ping is received. The heartbeat monitor will not do its job until it is activated by receiving the first ping.

<figure><img src="../../.gitbook/assets/Heartbeat monitoring 04.png" alt="Heartbeat monitoring in ilert"><figcaption></figcaption></figure>

If you need to update the monitor, click the **pencil** icon. You can also delete your monitor using the same menu by clicking the bin icon.&#x20;

To adjust alerting settings for your newly created Heartbeat monitor, go to **Alert sources**, then, again, **Alert sources,** and choose **Heartbeat** from the list of integrations. You can have many heartbeats pointing to the same alert source and have unified alerting settings for all of them.

<figure><img src="../../.gitbook/assets/Heartbeat monitoring 05.png" alt="create ilert heartbeat monitoring"><figcaption></figcaption></figure>

You can find more examples on how to implement heartbeats here:

{% content-ref url="prometheus-heartbeat-example.md" %}
[prometheus-heartbeat-example.md](prometheus-heartbeat-example.md)
{% endcontent-ref %}

{% content-ref url="cli-heartbeat-examples.md" %}
[cli-heartbeat-examples.md](cli-heartbeat-examples.md)
{% endcontent-ref %}
