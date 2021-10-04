---
description: Create events in Amazon EventBridge using iLert alerts.
---

# Amazon EventBridge Integration

[Amazon EventBridge](https://aws.amazon.com/eventbridge/) is a serverless event bus that makes it easier to build event-driven applications at scale using events generated from your applications, integrated Software-as-a-Service \(SaaS\) applications, and AWS services.

## In iLert <a id="in-ilert"></a>

### Create the Amazon EventBridge Alert Action

1. **\*\*Go to the alert sources tab and open the alert source whose alerts you want to publish to Amazon EventBridge. Click on the** Alert actions **tab and then on the** Add new alert action\*\* button

![](../.gitbook/assets/ilert%20%2890%29.png)

1. On the next page choose **Amazon EventBridge** as the type, name it, choose **Trigger mode**, enter your AWS **account ID**, choose AWS **region** and click on the **Save** button.

![](../.gitbook/assets/notification_center%20%284%29.png)

## In AWS Console <a id="in-aws-console"></a>

### Create an Amazon EventBridge event source <a id="create-sns-topic-subscription"></a>

1. Go to the AWS Console and then to **Amazon EventBridge**, then click on the **Partner event sources** link and on the **Event Source** that you created in the previous step**.**

![](../.gitbook/assets/amazon_eventbridge%20%281%29.png)

1. On the next page, click on the **Associate with event bus** button

![](../.gitbook/assets/amazon_eventbridge%20%283%29.png)

1. On the next page in the permissions section, choose **Organization** and **My organization** - **\*\*then click on the** Associate\*\* button

![](../.gitbook/assets/amazon_eventbridge.png)

1. To finished the configuration, you need to create a rule for the new event bus e.g. a rule for Amazon SQS. To do that, go to the **EventBridge Rules,** choose the **Event bus** and click on the **Create rule** button

![](../.gitbook/assets/amazon_eventbridge%20%284%29.png)

1. On the next page in the **New and description** section, name the rule, e.g. my-rule and scroll down

![](../.gitbook/assets/amazon_eventbridge%20%282%29.png)

1. In the **Define pattern** section, choose **Pre-defined pattern by service**, in the **Service provider** section choose **All Events** and scroll down

![](../.gitbook/assets/notification_center%20%282%29.png)

1. In the **Select targets** section, choose **SQS queue** as target type and choose your queue, then scroll down and click on the **Create** button

![](../.gitbook/assets/notification_center%20%283%29.png)

1. Finished! Now an Amazon EventBridge notification will be created for each alert that is created to the linked alert source in iLert.

## Event types sent to Amazon EventBridge event bus

* incident-created
* incident-acknowledged
* incident-resolved
* incident-assigned
* incident-auto-escalated
* incident-auto-resolved
* incident-rejected
* incident-raised
* incident-comment-added

## Sample event payload sent to Amazon EventBridge event bus

{% tabs %}
{% tab title="incident-created" %}
```javascript
{
  "version": "0",
  "id": "cb5fbc21-5156-2073-1f94-116d1dadae0e",
  "detail-type": "incident-created",
  "source": "aws.partner/ilert.com/test/cc23670e-ad3e-4c38-8d45-d22c36ced352",
  "account": "61xxxxxxxx53",
  "time": "2021-08-06T08:16:16Z",
  "region": "eu-central-1",
  "resources": [
    "ilert"
  ],
  "detail": {
    "id": "3710705",
    "summary": "test incident",
    "details": "My server is down",
    "reportTime": "2021-08-06T08:16:01.154Z",
    "status": "PENDING",
    "eventType": "incident-created",
    "priority": "HIGH",
    "alertSource": {
      "id": 2193327,
      "name": "Test"
    },
    "assignedTo": null
  }
}
```
{% endtab %}

{% tab title="incident-auto-escalated" %}
```javascript
{
  "version": "0",
  "id": "e133ebe4-414e-aaf3-dc34-ffc006ecfc89",
  "detail-type": "incident-auto-escalated",
  "source": "aws.partner/ilert.com/test/cc23670e-ad3e-4c38-8d45-d22c36ced352",
  "account": "61xxxxxxxx53",
  "time": "2021-08-06T08:16:04Z",
  "region": "eu-central-1",
  "resources": [
    "ilert"
  ],
  "detail": {
    "id": "3710705",
    "summary": "test incident",
    "details": "My server is down",
    "reportTime": "2021-08-06T08:16:01.154Z",
    "status": "PENDING",
    "eventType": "incident-auto-escalated",
    "priority": "HIGH",
    "alertSource": {
      "id": 2193327,
      "name": "Test"
    },
    "assignedTo": {
      "id": 2193122,
      "username": "text",
      "firstName": "FirstName",
      "lastName": "LastName",
      "email": "example@acme.com"
    }
  }
}
```
{% endtab %}

{% tab title="incident-acknowledged" %}
```javascript
{
  "version": "0",
  "id": "48150448-798c-ed2f-cef8-27e8840b5956",
  "detail-type": "incident-acknowledged",
  "source": "aws.partner/ilert.com/test/cc23670e-ad3e-4c38-8d45-d22c36ced352",
  "account": "61xxxxxxxx53",
  "time": "2021-08-06T08:25:48Z",
  "region": "eu-central-1",
  "resources": [
    "ilert"
  ],
  "detail": {
    "id": "3710705",
    "summary": "test incident",
    "details": "My server is down",
    "reportTime": "2021-08-06T08:16:01.154Z",
    "status": "ACCEPTED",
    "eventType": "incident-acknowledged",
    "priority": "HIGH",
    "alertSource": {
      "id": 2193327,
      "name": "Test"
    },
    "assignedTo": {
      "id": 2193122,
      "username": "text",
      "firstName": "FirstName",
      "lastName": "LastName",
      "email": "example@acme.com"
    }
  }
}
```
{% endtab %}

{% tab title="incident-resolved" %}
```javascript
{
  "version": "0",
  "id": "761e5e6c-9200-f366-210c-f70a4e54b167",
  "detail-type": "incident-resolved",
  "source": "aws.partner/ilert.com/test/cc23670e-ad3e-4c38-8d45-d22c36ced352",
  "account": "61xxxxxxxx53",
  "time": "2021-08-06T08:26:01Z",
  "region": "eu-central-1",
  "resources": [
    "ilert"
  ],
  "detail": {
    "id": "3710705",
    "summary": "test incident",
    "details": "My server is down",
    "reportTime": "2021-08-06T08:16:01.154Z",
    "status": "RESOLVED",
    "eventType": "incident-resolved",
    "priority": "HIGH",
    "alertSource": {
      "id": 2193327,
      "name": "Test"
    },
    "assignedTo": null
  }
}
```
{% endtab %}
{% endtabs %}

## FAQ <a id="faq"></a>

**Can I link multiple Amazon EventBridge sources to an iLert account?**

Yes.

**Can I choose which updates to an alert will be published in Amazon EventBridge?**

Yes.

**How can I remove the Partner Event Source?**

The partner event source will be automatically removed with the alert action.

