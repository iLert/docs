---
title: AWS Personal Health Dashboard Integration
seoTitle: >-
  iLert: AWS Personal Health Dashboard Integration for Alerting | Incident
  Response | Uptime
description: Create incidents in iLert from issues AWS Personal Health Dashboard.
date: '2020-04-28T02:40:05.000Z'
weight: 1
type: post
---

# AWS Personal Health Dashboard Integration

[AWS Personal Health Dashboard](https://aws.amazon.com/premiumsupport/technology/personal-health-dashboard/) provides alerts and remediation guidance when AWS is experiencing events that may impact you.

With iLert's AWS Personal Health Dashboard integration, you can automatically create incidents in iLert from problems in AWS Personal Health Dashboard. That way, you will never miss a critical alert and always alert the right person using iLert's on-call schedules, automatic escalation, and multiple alerting channels. When AWS Personal Health Dashboard reports an issue, iLert will alert the on-call person through their preferred channel, including SMS, phone calls, push notifications and Slack. iLert will automatically escalate to the next person, if the alert is not acknowledged. iLert also lets you define alerting rules based on support hours and delay alerts until your support hours start.

## In iLert <a id="in-ilert"></a>

### Create AWS Personal Health Dashboard alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click "Create new alert source"

2. Enter a name and select your desired escalation policy. Select "AWS Personal Health Dashboard" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/awsphd9.png)

3. On the next page, a **Webhook URL** is generated. You will need this URL below when setting up the SNS topic subscription in AWS.

![](../.gitbook/assets/awsphd10.png)

## In AWS

### Create an SNS topic <a id="create-sns-topic"></a>

> If you have already created an SNS topic for your AWS Personal Health Dashboard that you want to reuse, you can proceed to step 3.

1. In the SNS Dashboard click on **Create topic**

![](../.gitbook/assets/awsphd0.png)

2. Name the topic and click on **Create topic**

![](../.gitbook/assets/awsphd1.png)

3. Click on **Create subscription** on the Topic Detail page

![](../.gitbook/assets/awsphd2.png)

4. In the **Topic ARN** section, ensure that the **SNS Topic** that you generated is selected

5. In the **Protocol** section, choose the **HTTPS** protocol

6. In the **Endpoint** section, paste the **Webhook URL** that you generated in iLert

7. In the **Enable raw message delivery** section, ensure that the checkbox is unchecked

8. Click on **Create subscription**

![](../.gitbook/assets/awsphd3.png)

9. The subscription is **automatically confirmed by iLert** when it is created. After updating the overview, the status "PendingConfirmation" should disappear, and the ID should be displayed.

### Personal Health Dashboard: Create rule and link to topic <a id="create-phd-rule"></a>

You can now link any AWS Personal Health Dashboard rule to the topic you have created. The following section describes how to create a rule and make the link.

1. In AWS, click on **Alerts** icon and select **View all alerts**

![](../.gitbook/assets/awsphd4.png)

2. In the AWS Personal Health Dashboard click on **Dashboard** and then click on **Set up notifications with CloudWatch Events** to add a rule

![](../.gitbook/assets/awsphd5.png)

3. In the **Event Source** section, choose the **Event Pattern**

4. In the **Service Name** section, choose the **Health** service

5. In the **Event Type** section, choose the **Specific Health events** service

6. In the next section, choose **Any service** to receive an health update for each AWS service or choose **Specific service\(s\)** and select a service that interests you

7. In the **Targets** section, choose the **SNS Topic** and select the SNS topic that you generated before

8. Click on the **Configure details** button

![](../.gitbook/assets/awsphd6.png)

9. On the next page in the **Name** section, enter a name for the rule

10. Click on the **Create rule** button

![](../.gitbook/assets/awsphd7.png)

![](../.gitbook/assets/awsphd8.png)

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as the Personal Health Issue is solved in AWS, the incident in iLert will be closed.

**Can I link AWS Personal Health Dashboard to multiple alert sources in iLert?**

Yes, create an SNS topic subscription in AWS for each alert source.

