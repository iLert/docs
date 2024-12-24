---
description: >-
  The ilert Agent is a program that lets you easily integrate your monitoring
  system with ilert.
---

# ilert Agent - ilagent

The ilert agent application comes a single binary file that is available for all major platforms. We also support an official Docker image.

* It helps you easily manage events from the CLI
* send (continuous) heartbeats from the CLI
* run a network local proxy HTTP server to pipe events to the ilert REST API
* run a network local [MQTT (proxy) to pipe events to ilert](../../inbound-integrations-1/mqtt.md)
* run a network local [Apache Kafka (proxy) client to pipe events to ilert](../../inbound-integrations-1/kafka.md)

The source code of ilagent is open source [https://github.com/iLert/ilagent](https://github.com/iLert/ilagent) and managed on GitHub.\
And run ilagent to see your command line options:

```
ilagent --help || docker run ilert/ilagent --help
```

{% hint style="info" %}
Missing a feature? Let us [know](../../contact.md)
{% endhint %}
