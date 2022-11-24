---
description: >-
  AWS GuardDuty is a threat detection service that continuously monitors your
  AWS accounts and workloads for malicious activity and delivers detailed
  security findings for visibility and remediation.
---

# AWS GuardDuty Integration

## In ilert

* Go to the "**Alert sources**" tab and click "**Create new alert source**"

![](<../.gitbook/assets/ilert-create-alert (4).png>)

* Enter a name and select your desired escalation policy.  &#x20;
* Select "**AWS GuardDuty**" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/ilert-guardduty.png)

* On the next page, an **AWS GuardDuty URL** is generated. You will need the URL for the webhook configuration

![](<../.gitbook/assets/ilert-guardduty-url (1).png>)

## In AWS Dashboard

* Use the search bar and select **Simple Notification Service** (SNS). Select **Topics** and click **Create Topic** in the SNS Dashboard.
* Input a Topic name and Display name and Create topic. After the topic has been created, Select Subscriptions in the left hand menu and click Create Subscription.

![](../.gitbook/assets/awsguardduty-snstopic.png)

* Select **HTTPS** Protocol and put the URL that was received from ilert side into the Endpoint field, keep the Enable raw message delivery checkbox **unchecked** and **Create Subscription**.
* The subscription would be confirmed automatically on ilert side, but make sure the Subscription ID is not in **PendingConfirmation** state.
* Search and select the Amazon GuardDuty console in the Service Search. Search for GuardDuty click **Enable GuardDuty** if this is the first time enabling Amazon GuardDuty.
* If the GuardDuty is enabled, CloudWatch Event Rules can be configured to send alerts to ilert and please navigate to the CloudWatch console.
* To create a rule, select **Rules** under **Events** and then click **Create Rules**. Select GuardDuty as the Service Name and then choose GuardDuty Finding as the Event Type.

![](<../.gitbook/assets/awsguardduty-cloudwatchrule (1).png>)

* Click Add a target and select SNS topic, select Your Topic Name that has been created earlier and then click **Configure Details**.
* Assign a Name like `ilert-incidents` and click Create Rule.

![](../.gitbook/assets/awsguardduty-rulemade.png)

* In order to test this, go back to the Amazon GuardDuty console and generate sample findings, to create event in ilert.

![](../.gitbook/assets/awsguardduty-generatefindings.png)

* Select Settings, then select Generate Sample Findings and then click Findings in the left navigation bar.
* The sample findings should have been generated, and it will create the event in the ilert automatically.
