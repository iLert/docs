---
title: AWS Lambda Integration
seoTitle: 'iLert: AWS Lambda Integration for Alerting | Incident Response | Uptime'
description: Invoke AWS Lambda functions based on alerts in iLert
date: '2020-05-12T05:02:05.000Z'
weight: 1
---

# AWS Lambda Integration

[AWS Lambda](https://aws.amazon.com/lambda/) is a serverless compute service that lets you run code without provisioning or managing servers, creating workload-aware cluster scaling logic, maintaining event integrations, or managing runtimes.

{% hint style="info" %}
Beforehand make sure that you have created an AWS lambda function in your AWS project and got its public `URL` handy. You might also create an additional authorization value e.g. a secure random string that you are evaluating in the HTTP request `Authorization` header when you function is invoked by iLert, we acutally suggest using this.
{% endhint %}

## Create the connector <a id="connector"></a>

Go to the connectors tab of your account.

![](../.gitbook/assets/s1%20%282%29.png)

And create a new connector. Choose AWS lambda as type \(you may add the additional `Authorization` parameter as stated in the beginning of this doc.\)

![](../.gitbook/assets/s2.png)

Click on save to save the connector.

## Create the alert action <a id="connection"></a>

Visit the alert source \(view\) whose alerts should trigger your serverless function. Navigate to the **Alert actions** tab and click on the **Create new alert action** button.

![](../.gitbook/assets/new_incident_action%20%281%29.png)

Choose AWS lambda as type and select your previously created connector. Enter a name and the url targeting your public function. You may also customize the HTTP request body that is used to invoke your function.

![](../.gitbook/assets/ilert%20%2857%29.png)

Click on save to create the alert action, you may test the alert action in the following screen.

