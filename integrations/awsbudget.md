---
description: The ilert AWS Budget Integration helps you to easily connect ilert with AWS.
---

# AWS Budget Integration

[AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/) allows you to set custom budgets to track your cost and usage from the simplest to the most complex use cases.

With ilert AWS Budget Integration, you can receive AWS Budget alert through ilert and easily extend AWS Budget functionality with SMS, push, voice, and ilert on-call schedules.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create an AWS Budget alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click "Create new alert source"
2. Enter a name and select your desired escalation policy. Select "**AWS Budget**" as the **Integration Type** and click on **Save**.

![](<../.gitbook/assets/iLert (8).png>)

1. On the next page, a **Webhook URL** is generated. You will need this URL below when setting up the SNS topic subscription in AWS.

![](<../.gitbook/assets/iLert (9).png>)

## In AWS

### Create an SNS topic <a href="#create-sns-topic" id="create-sns-topic"></a>

> If you have already created an SNS topic for your AWS Budget, that you want to reuse, you can proceed to step 3.

1. On the SNS Dashboard click on **Create topic**

![](../.gitbook/assets/awsphd0.png)

1. Give the topic a name and click on **Create topic**

![](../.gitbook/assets/Simple\_Notification\_Service.png)

1. Click on **Create subscription** on the Topic Detail page

![](<../.gitbook/assets/Simple\_Notification\_Service (1).png>)

1. In the **Topic ARN** section, ensure that the **SNS Topic** that you generated is selected
2. In the **Protocol** section, choose the **HTTPS** protocol
3. In the **Endpoint** section, paste the **Webhook URL** that you generated in ilert
4. In the **Enable raw message delivery** section, ensure that the checkbox is unchecked
5. Click on **Create subscription**

![](<../.gitbook/assets/Simple\_Notification\_Service (2).png>)

1. The subscription is **automatically confirmed by ilert** when it is created. After updating the overview, the status "PendingConfirmation" should disappear, and the ID should be displayed.

### Billing Dashboard: Create budget and link to topic <a href="#create-phd-rule" id="create-phd-rule"></a>

You can now link any AWS Budget to the topic you have created. The following section describes how to create a budget and make the link.

1. In AWS, click on the **Profile Menu** icon and select **My Billing Dashboard**

![](<../.gitbook/assets/Simple\_Notification\_Service (3).png>)

1. In the AWS Billing Dashboard click on **Budgets** and then click on **Create budget** to add a budget

![](<../.gitbook/assets/Billing\_Management\_Console (1).png>)

1. On the **Select budget type** page, choose a budget type that interests you and click on **Set your budget**

![](<../.gitbook/assets/Billing\_Management\_Console (2).png>)

1. On the **Set your budget** page, choose the settings according to your liking and click on **Configure thresholds**

![](<../.gitbook/assets/Billing\_Management\_Console (3).png>)

1. On the **Configure thresholds** page, in the **Amazon SNS** section, paste the **SNS ARN** that you generated before and make sure that you configured the right topic permissions (you should see ✅ sign), then click on **Confirm budget**

![](<../.gitbook/assets/Billing\_Management\_Console (4).png>)

1. On the **Config budget** page click on **Create**

![](<../.gitbook/assets/Billing\_Management\_Console (6).png>)

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No.

**Can I link AWS Budget to multiple alert sources in ilert?**

Yes, create an SNS topic subscription in AWS for each alert source.
