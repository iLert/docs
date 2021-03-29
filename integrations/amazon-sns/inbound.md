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

![](../../.gitbook/assets/ilert%20%2842%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the SNS subscription in AWS Console.

![](../../.gitbook/assets/ilert%20%2847%29.png)

## In AWS Console <a id="in-aws-console"></a>

### Create a SNS topic subscrition <a id="create-sns-topic-subscription"></a>

{% hint style="info" %}
If you already have an Amazon SNS topic, please skip the steps 1 and 2.
{% endhint %}

1. Go to the AWS Console and then to **Amazon SNS**, then click on the **Topic** link and on the **Create topic** button**.**

![](../../.gitbook/assets/simple_notification_service%20%287%29.png)

2. On the next page, choose **Standard** topic, name the topic e.g. iLert and click on the **Create topic** button

![](../../.gitbook/assets/simple_notification_service%20%284%29.png)

3. On the topic overview page, click on the **Create subscription** button

![](../../.gitbook/assets/simple_notification_service%20%285%29.png)

3. On the next page, in the **Protocol** section choose **HTTPS**, on the **Endpoint** section paste the **Webhook URL** that you generated in iLert and click on the **Create subscription** button

![](../../.gitbook/assets/simple_notification_service%20%286%29.png)

Finished! Your Amazon SNS notifications will now create incidents in iLert.

## Custom attributes

{% hint style="info" %}
All attributes are optional
{% endhint %}

| Attribute | Preconditions | Allowed values |
| :--- | :--- | :--- |
| eventType | optional | ALERT, ACCEPT, RESOLVE |
| incidentKey | required if eventType used | Any string |
| priority | optional | HIGH, LOW |
| incidentUrl1 | optional | Any URL string |
| incidentUrl2 | optional | Any URL string |
| incidentUrl3 | optional | Any URL string |

#### Example

{% tabs %}
{% tab title="Java" %}
```java
AmazonSNSClient snsClient = new AmazonSNSClient(new BasicAWSCredentials("AWS_ACCESS_KEY","AWS_SECRET_KEY"));

String msg = "Test incident details";
String subject = "Test alert for Amazon SNS Integration";

PublishRequest publishRequest = new PublishRequest("arn:aws:sns:xxxxxxxxx:xxxxxxxxxx:MyTopic", msg, subject);

publishRequest.addMessageAttributesEntry("eventType", new MessageAttributeValue()
                    .withDataType("String").withStringValue("ALERT"));
publishRequest.addMessageAttributesEntry("incidentKey", new MessageAttributeValue()
                    .withDataType("String").withStringValue("my-uniq-incident-string"));
publishRequest.addMessageAttributesEntry("priority", new MessageAttributeValue()
                    .withDataType("String").withStringValue("HIGH"));
publishRequest.addMessageAttributesEntry("incidentUrl1", new MessageAttributeValue()
                    .withDataType("String").withStringValue("https://www.ilert.com"));

PublishResult publishResult = snsClient.publish(publishRequest);
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
	"github.com/aws/aws-sdk-go/aws"
	"github.com/aws/aws-sdk-go/aws/session"
	"github.com/aws/aws-sdk-go/service/sns"

	"fmt"
	"os"
)

func main() {
	// Initialize a session that the SDK will use to load
	// credentials from the shared credentials file. (~/.aws/credentials).
	sess := session.Must(session.NewSessionWithOptions(session.Options{
		SharedConfigState: session.SharedConfigEnable,
	}))

	svc := sns.New(sess)

	result, err := svc.Publish(&sns.PublishInput{
		Message:  aws.String("Test incident details"),
		Subject:  aws.String("Test alert for Amazon SNS Integration"),
		TopicArn: aws.String("arn:aws:sns:xxxxxxxxx:xxxxxxxxxx:MyTopic"),
		MessageAttributes: map[string]*sns.MessageAttributeValue{
			"eventType":    {StringValue: aws.String("ALERT"), DataType: aws.String("String")},
			"incidentKey":  {StringValue: aws.String("my-uniq-incident-string"), DataType: aws.String("String")},
			"priority":     {StringValue: aws.String("HIGH"), DataType: aws.String("String")},
			"incidentUrl1": {StringValue: aws.String("https://www.ilert.com"), DataType: aws.String("String")},
		},
	})
	
	if err != nil {
		fmt.Println(err.Error())
		os.Exit(1)
	}

	fmt.Println(*result.MessageId)
}

```
{% endtab %}
{% endtabs %}

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

No, but you can use the **eventType** custom attribute to resolve an incident in specified **incidentKey**.

**Can I accept an incident via Amazon SNS?**

Yes, use the **eventType** custom attribute to resolve an incident in specified **incidentKey**.

**Can I connect Amazon SNS Alerting with multiple alert sources from iLert?**

Yes, simply add more Amazon SNS topics or add more topic subscriptions to the same topic and use the **incidentKey** custom attribute.

