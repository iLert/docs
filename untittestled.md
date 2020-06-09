---
title: "Azure Function Integration"
seoTitle: "iLert: Azure Function Integration for Alerting | Incident Response | Uptime"
description: "The iLert Azure Function Integration helps you to easily connect iLert with Azure Function."
date: 2020-05-12T11:02:05+06:00
weight: 1
---

**On this page**

* [Create the connector](#connector)
* [Create the connection](#connection)

Beforehand make sure that you have created an Azure Function function in your Microsoft Azure project and got its public `URL` handy. You might also create an additional authorization value e.g. a secure random string that you are evaluating in the HTTP request `Authorization` header when you function is invoked by iLert, we acutally suggest using this.

## Create the connector {#connector}

Go to the connectors tab of your account.

![s1](s1.png "image")

And create a new connector.
Choose Azure Function as type (you may add the additional `Authorization` parameter as stated in the beginning of this doc.)

![s2](s2.png "image")

Click on save to save the connector.

## Create the connection {#connection}

Visit the alert source (view) whose incidents should trigger your serverless function. Navigate to the connections tab and create a new connection.

![s3](s3.png "image")

Choose Azure Function as type and select your previously created connector.
Enter a name and the url targeting your public function.
You may also customize the HTTP request body that is used to invoke your function.

![s4](s4.png "image")

Click on save to create the connection, you may test the connection in the following screen.
