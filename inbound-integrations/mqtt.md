# MQTT Integration

[MQTT](https://mqtt.org/) is a lightweight, publish-subscribe, machine-to-machine network protocol for message queue/message queuing service. It is designed for connections with remote locations that have devices with resource constraints or limited network bandwidth, such as in the Internet of Things. While ilert doesn't directly support an MQTT broker to accept the publishing of messages, it supports integrations specifically meant to connect MQTT topics to ilert events and provides the **ilagent** tool to connect your MQTT brokers to ilert without actually writing the code yourself.

## In ilert: Create an MQTT alert source <a href="#create-alert-source" id="create-alert-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click on **Create new alert source.**\


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **MQTT** in the search field, click on the MQTT tile, and click **Next**. \


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.\


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later. \


    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click on **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated, which you will need later in this guide.



    <figure><img src="../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## In your environment

**Foreword**: you are free to use any MQTT client to subscribe to your topics and wire them into an API call to `POST api.ilert.com/api/v1/mqtt/{your-key-here}` (the endpoint accepts the payload of our generic [event API](https://api.ilert.com/api-docs/#tag/events/post/events). See also this [eventing guide](../rest-api/api-samples/creating-alerts-through-events.md)).

However, if you don't wish to write your own software to wire subscriber and POST request, you may use our _swiss-army-knife tool_ **ilagent** which supports an MQTT mode where it subscribes to a specific MQTT topic to deliver events or heartbeats to ilert; it automatically buffers the messages in a local database to support retries as well. It is open source and can be found on [GitHub](https://github.com/iLert/ilagent).

While you may [compile the binary](https://github.com/iLert/ilagent?tab=readme-ov-file#compile-the-binary-from-source) locally, we also support an official Docker image [ilert/ilagent](https://hub.docker.com/r/ilert/ilagent/tags) which can be used to get started quickly.

### Consume a topic and turn messages into events

{% hint style="warning" %}
**Note**: your messages need to be in the format of the ilert event API schema; at least: `{apiKey, eventType, summary}`
{% endhint %}

```
docker run -p 8977:8977 ilert/ilagent daemon -p 8977 -v -v \
    -m mqtt-broker-host -q 1883 -n ilagentsub -e 'ilert/e'
```

You can always check `docker run ilert/ilagent --help` for a full list of arguments. e.g. username and password for the MQTT broker.

If you don't want to provide the apiKey in every message, you can overwrite it with the `--event_key 'il1api123...'` argument.

### Transform any kind of message into events

{% hint style="warning" %}
**Note**: your messages need to be JSON.
{% endhint %}

The ilagent also supports basic event key overwrites so that you can map any message top-level keys into an event payload.

```
docker run -p 8977:8977 ilert/ilagent daemon -v -v \
    -m mqtt-broker-host -q 1883 -n ilagent -e '#' \
    --event_key 'il1api123...' \
    --map_key_alert_key 'mCode' \
    --map_key_summary 'comment' \
    --map_key_etype 'state' \
    --map_val_etype_alert 'SET' \
    --map_val_etype_accept 'ACK' \
    --map_val_etype_resolve 'CLR' \
    --filter_key 'type' \
    --filter_val 'ALARM'
```

The top sample code will subscribe to ALL MQTT topics and filter every message for `message.type == 'ALERT'` it will then map the field `message.state: SET => ALERT, ACK => ACCEPT and CLR => RESOLVE` to the `event.eventType` additionally `message.mCode` will be used as `event.alertKey` and `message.comment as event.summary`.&#x20;

With these flexible arguments, you may quickly prototype or start your alert management without the need to write and deploy a custom mapper.

_If you are using this subscriber bridge for critical scenarios, make sure to read the section on MQTT at least once delivery guarantee in the ilagent readme._

### FAQ

#### My local docker ilert/ilagent does not connect to my broker

In case your broker is running in docker as well, you cannot simply use localhost to connect; you will need to link your broker to your ilagent container with `--link broker-container-name:broker-container-name` then provide `-m broker-container-name` so that your ilagent actually connects to your broker.



