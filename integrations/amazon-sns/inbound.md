---
description: >-
  With the iLert Amazon SNS integration, you can create incidents in iLert based
  on SNS notifications.
---

# Amazon SNS Inbound Integration

[Amazon Simple Notification Service](https://aws.amazon.com/sns/) \(Amazon SNS\) is a fully managed messaging service for both application-to-application \(A2A\) and application-to-person \(A2P\) communication.

The A2A pub/sub functionality provides topics for high-throughput, push-based, many-to-many messaging between distributed systems, microservices, and event-driven serverless applications. Using Amazon SNS topics, your publisher systems can fanout messages to a large number of subscriber systems including Amazon SQS queues, AWS Lambda functions and HTTPS endpoints, for parallel processing, and Amazon Kinesis Data Firehose. The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

## In iLert <a id="in-ilert"></a>

### Create a Amazon SNS alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Amazon SNS" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%2836%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the SNS subscription in AWS Console.

![](../../.gitbook/assets/ilert%20%2842%29.png)

## In AWS Console <a id="in-splunk"></a>

### Create a SNS topic subscrition <a id="create-action-sequences"></a>

1. Go to Kibana and then to **Management -&gt; Watcher**, then click on the **Create** button and on the **Create advanced watch** button**.**

![](../../.gitbook/assets/kibana%20%281%29.png)

2. On the next page, name the watcher e.g. iLert, define conditions and actions the **Webhook URL** that you generated in iLert as follows:

![](../../.gitbook/assets/kibana.png)

```text
{
    ...
    [CONFIGURATIONS OF YOUR X-PACK ALERTING ALERT]
    ...
    "actions" : {
        "ilert" : {
            "webhook" : {
                "scheme" : "https",
                "method" : "POST",
                "host" : "api.ilert.com",
                "port" : 443,
                "path" : "/api/v1/events/eswatcher/[YOUR API KEY]",
                "headers" : {
                    "Content-Type" : "application/json"
                },
                "params": {},
                "body" : "{{#toJson}}ctx{{/toJson}}"
            }
        }
    }
}
```

Finished! Your X-Pack alerts will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

No, unfortunately Watcher's notification is not compatible with iLert's resolve event.

**Can I connect X-Pack Alerting with multiple alert sources from iLert?**

Yes, simply add more watchers in X-Pack Alerting.

