---
title: Azure Function Integration
seoTitle: 'iLert: Azure Function Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert Azure Function Integration helps you to easily connect iLert with
  Azure Function.
date: '2020-05-12T05:02:05.000Z'
weight: 1
---

# Azure Function Integration

Beforehand make sure that you have created an Azure Function function in your Microsoft Azure project and got its public `URL` handy. You might also create an additional authorization value e.g. a secure random string that you are evaluating in the HTTP request `Authorization` header when you function is invoked by iLert, we actually suggest using this.

## Create the connector <a id="connector"></a>

Go to the connectors tab of your account.

![](../.gitbook/assets/s1%20%281%29.png)

And create a new connector. Choose Azure Function as type \(you may add the additional `Authorization` parameter as stated in the beginning of this doc.\)

![](../.gitbook/assets/s2%20%281%29.png)

Click on save to save the connector.

## Create the connection <a id="connection"></a>

Visit the alert source \(view\) whose alerts should trigger your serverless function. Navigate to the connections tab and create a new connection.

![](../.gitbook/assets/s3%20%282%29.png)

Choose Azure Function as type and select your previously created connector. Enter a name and the url targeting your public function. You may also customize the HTTP request body that is used to invoke your function.

![](../.gitbook/assets/s4%20%281%29.png)

Click on save to create the connection, you may test the connection in the following screen.

