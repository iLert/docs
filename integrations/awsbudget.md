---
description: The ilert AWS Budget Integration helps you to easily connect ilert with AWS.
---

# AWS Budget Integration

[AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/) allows you to set custom budgets to track your cost and usage from the simplest to the most complex use cases.

With ilert AWS Budget Integration, you can receive AWS Budget alert through ilert and easily extend AWS Budget functionality with SMS, push, voice, and ilert on-call schedules.

## In ilert: Create an AWS Budget alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **AWS Budget** in the search field, click on the AWS Budget tile and click on **Next**.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](https://docs.ilert.com/alerting/alert-sources#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FueugN4JgHn1c90ggFA6u%2FScreenshot%202023-08-28%20at%2011.38.24.png?alt=media&#x26;token=b8009daf-3ca8-4264-a6fa-e42ef7333205" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.​

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2Fi3TIOBvNYBQfDtNpmm0A%2FScreenshot%202023-08-28%20at%2011.47.34.png?alt=media&#x26;token=6cae965a-e448-4443-8c20-37cf501c43b2" alt=""><figcaption></figcaption></figure>

## In AWS: Create a SNS topic

> If you have already created an SNS topic for your AWS Budget, that you want to reuse, you can proceed to step 3.

1. On the SNS Dashboard click on **Create topic**

![](../.gitbook/assets/awsphd0.png)

2. Give the topic a name and click on **Create topic**

![](../.gitbook/assets/Simple\_Notification\_Service.png)

3. Click on **Create subscription** on the Topic Detail page

![](<../.gitbook/assets/Simple\_Notification\_Service (1).png>)

4. In the **Topic ARN** section, ensure that the **SNS Topic** that you generated is selected
5. In the **Protocol** section, choose the **HTTPS** protocol
6. In the **Endpoint** section, paste the **Webhook URL** that you generated in ilert
7. In the **Enable raw message delivery** section, ensure that the checkbox is unchecked
8. Click on **Create subscription**

![](<../.gitbook/assets/Simple\_Notification\_Service (2).png>)

9. The subscription is **automatically confirmed by ilert** when it is created. After updating the overview, the status "PendingConfirmation" should disappear, and the ID should be displayed.

### Billing Dashboard: Create budget and link to topic <a href="#create-phd-rule" id="create-phd-rule"></a>

You can now link any AWS Budget to the topic you have created. The following section describes how to create a budget and make the link.

1. In AWS, click on the **Profile Menu** icon and select **My Billing Dashboard**

![](<../.gitbook/assets/Simple\_Notification\_Service (3).png>)

2. In the AWS Billing Dashboard click on **Budgets** and then click on **Create budget** to add a budget

![](<../.gitbook/assets/Billing\_Management\_Console (1).png>)

3. On the **Select budget type** page, choose a budget type that interests you and click on **Set your budget**

![](<../.gitbook/assets/Billing\_Management\_Console (2).png>)

4. On the **Set your budget** page, choose the settings according to your liking and click on **Configure thresholds**

![](<../.gitbook/assets/Billing\_Management\_Console (3).png>)

5. On the **Configure thresholds** page, in the **Amazon SNS** section, paste the **SNS ARN** that you generated before and make sure that you configured the right topic permissions (you should see ✅ sign), then click on **Confirm budget**

![](<../.gitbook/assets/Billing\_Management\_Console (4).png>)

6. On the **Config budget** page click on **Create**

![](<../.gitbook/assets/Billing\_Management\_Console (6).png>)

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No.

**Can I link AWS Budget to multiple alert sources in ilert?**

Yes, create an SNS topic subscription in AWS for each alert source.
