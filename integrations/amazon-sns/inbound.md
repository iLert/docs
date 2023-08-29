---
description: >-
  With the ilert Amazon SNS integration, you can create alerts in ilert based on
  SNS notifications.
---

# Amazon SNS Inbound Integration

[Amazon Simple Notification Service](https://aws.amazon.com/sns/) (Amazon SNS) is a fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.

The A2A pub/sub functionality provides topics for high-throughput, push-based, many-to-many messaging between distributed systems, microservices, and event-driven serverless applications. Using Amazon SNS topics, your publisher systems can fanout messages to a large number of subscriber systems including Amazon SQS queues, AWS Lambda functions and HTTPS endpoints, for parallel processing, and Amazon Kinesis Data Firehose. The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

## In ilert: Create a Amazon SNS alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **Amazon SNS** in the search field, click on the Amazon SNS tile and click on **Next**.&#x20;

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.\


    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FueugN4JgHn1c90ggFA6u%2FScreenshot%202023-08-28%20at%2011.38.24.png?alt=media&#x26;token=b8009daf-3ca8-4264-a6fa-e42ef7333205" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In AWS Console <a href="#in-aws-console" id="in-aws-console"></a>

### Create a SNS topic subscrition <a href="#create-sns-topic-subscription" id="create-sns-topic-subscription"></a>

{% hint style="info" %}
If you already have an Amazon SNS topic, please skip the steps 1 and 2.
{% endhint %}

4. Go to the AWS Console and then to **Amazon SNS**, then click on the **Topic** link and on the **Create topic** button\*\*.\*\*

![](<../../.gitbook/assets/Simple\_Notification\_Service (4).png>)

5. On the next page, choose **Standard** topic, name the topic e.g. ilert and click on the **Create topic** button

![](<../../.gitbook/assets/Simple\_Notification\_Service (5).png>)

6. On the topic overview page, click on the **Create subscription** button

![](<../../.gitbook/assets/Simple\_Notification\_Service (6).png>)

7. On the next page, in the **Protocol** section choose **HTTPS**, on the **Endpoint** section paste the **Webhook URL** that you generated in ilert and click on the **Create subscription** button

![](<../../.gitbook/assets/Simple\_Notification\_Service (7).png>)

{% hint style="warning" %}
Do not activate the checkbox **Enable raw message delivery**. ilert won't process those messages otherwise.
{% endhint %}

Finished! Your Amazon SNS notifications will now create alerts in ilert.

## Custom attributes

{% hint style="info" %}
All attributes are optional
{% endhint %}

| Attribute    | Preconditions              | Allowed values         |
| ------------ | -------------------------- | ---------------------- |
| eventType    | optional                   | ALERT, ACCEPT, RESOLVE |
| incidentKey  | required if eventType used | Any string             |
| incidentUrl1 | optional                   | Any URL string         |
| incidentUrl2 | optional                   | Any URL string         |
| incidentUrl3 | optional                   | Any URL string         |

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

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, but you can use the **eventType** custom attribute to resolve an incident in specified **incidentKey**.

**Can I accept an incident via Amazon SNS?**

Yes, use the **eventType** custom attribute to resolve an incident in specified **incidentKey**.

**Can I connect Amazon SNS Alerting with multiple alert sources from ilert?**

Yes, simply add more Amazon SNS topics or add more topic subscriptions to the same topic and use the **incidentKey** custom attribute.
