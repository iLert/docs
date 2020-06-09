---
title: Amazon CloudWatch Integration
seoTitle: 'iLert: Amazon CloudWatch Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert Amazon CloudWatch Integration helps you to easily connect iLert with
  Cloudwatch.
date: '2018-12-29T05:02:05.000Z'
weight: 1
type: post
---

# Amazon CloudWatch

Amazon CloudWatch is a monitoring service for AWS cloud resources and applications running in the AWS Cloud. Amazon CloudWatch can monitor AWS resources, such as EC2 instances, Amazon DynamoDB tables, and Amazon RDS DB instances, as well as application and service generated metrics and log files.

With iLert CloudWatch Integration, you can receive CloudWatch alerts through iLert and easily extend CloudWatch with SMS, push, voice, and iLert rosters.

## In iLert: Create CloudWatch alert source <a id="create-alert-source"></a>

1. Switch to the tab "alert sources" and click on the button "Create new alert source"
2. Assign name and select escalation chain
3. Select and save "Amazon CloudWatch" in the Integration Type field.
4. The URL shown on the next page is the HTTP endpoint for the SNS topic in Amazon and will be needed in later steps.

## In AWS SNS: create topic <a id="create-topic"></a>

> If you have already created an SNS topic for your CloudWatch alarms that you want to reuse, you can proceed to step 3.

1. In the SNS Dashboard click on "Create topic"
2. Name the topic and click on "Create topic".
3. Click on "Create subscription" on the Topic Detail page
4. Select "HTTPS" as the protocol and transfer the URL from the above-created alert source to iLert at Endpoint and click on "Create subscription".
5. The subscription is automatically confirmed by iLert when it is created. After updating the overview, the status "PendingConfirmation" should disappear and the ID should be displayed.

## In AWS CloudWatch: Create alarm and link to topic <a id="create-alarm"></a>

You can now link any CloudWatch alarm to the topic you have created. The following section describes how to create an alarm and make the link.

1. In CloudWatch, on the Alarms tab, click Create Alarm and select a metric
2. Click on "+ Notification" to add two "Notification Actions": one for the states ALARM and OK. In the "Send notification to:" box, select the topic created above.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as the condition of an alarm is OK again in CloudWatch, the incident in iLert will be fixed.

**Can I link CloudWatch to multiple alert sources in iLert?**

Yes, create an SNS topic in CloudWatch for each alert source. You can then select for each alert in CloudWatch which topic you want to use for alerting.

