---
description: >-
  AWS GuardDuty is a threat detection service that continuously monitors your
  AWS accounts and workloads for malicious activity and delivers detailed
  security findings for visibility and remediation.
---

# AWS GuardDuty Integration

## In ilert: Create an AWS GuardDuty alert source <a href="#create-alert-source" id="create-alert-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **AWS GuardDuty** in the search field, click on the AWS GuardDuty tile and click on **Next**.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](https://docs.ilert.com/alerting/alert-sources#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FueugN4JgHn1c90ggFA6u%2FScreenshot%202023-08-28%20at%2011.38.24.png?alt=media&#x26;token=b8009daf-3ca8-4264-a6fa-e42ef7333205" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.​

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2Fi3TIOBvNYBQfDtNpmm0A%2FScreenshot%202023-08-28%20at%2011.47.34.png?alt=media&#x26;token=6cae965a-e448-4443-8c20-37cf501c43b2" alt=""><figcaption></figcaption></figure>

## In AWS Dashboard

1. Use the search bar and select **Simple Notification Service** (SNS). Select **Topics** and click **Create Topic** in the SNS Dashboard.
2. Input a Topic name and Display name and Create topic. After the topic has been created, Select Subscriptions in the left hand menu and click Create Subscription.

![](../.gitbook/assets/awsguardduty-snstopic.png)

3. Select **HTTPS** Protocol and put the URL that was received from ilert side into the Endpoint field, keep the Enable raw message delivery checkbox **unchecked** and **Create Subscription**.
4. The subscription would be confirmed automatically on ilert side, but make sure the Subscription ID is not in **PendingConfirmation** state.
5. Search and select the Amazon GuardDuty console in the Service Search. Search for GuardDuty click **Enable GuardDuty** if this is the first time enabling Amazon GuardDuty.
6. If the GuardDuty is enabled, CloudWatch Event Rules can be configured to send alerts to ilert and please navigate to the CloudWatch console.
7. To create a rule, select **Rules** under **Events** and then click **Create Rules**. Select GuardDuty as the Service Name and then choose GuardDuty Finding as the Event Type.

![](<../.gitbook/assets/awsguardduty-cloudwatchrule (1).png>)

8. Click Add a target and select SNS topic, select Your Topic Name that has been created earlier and then click **Configure Details**.
9. Assign a Name like `ilert-incidents` and click Create Rule.

![](../.gitbook/assets/awsguardduty-rulemade.png)

10. In order to test this, go back to the Amazon GuardDuty console and generate sample findings, to create event in ilert.

![](../.gitbook/assets/awsguardduty-generatefindings.png)

11. Select Settings, then select Generate Sample Findings and then click Findings in the left navigation bar.
12. The sample findings should have been generated, and it will create the event in the ilert automatically.
