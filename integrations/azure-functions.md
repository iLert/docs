---
description: >-
  The ilert Azure Function Integration helps you to easily connect ilert with
  Azure Function.
---

# Azure Function Integration

Beforehand make sure that you have created an Azure Function function in your Microsoft Azure project and got its public `URL` handy. You might also create an additional authorization value e.g. a secure random string that you are evaluating in the HTTP request `Authorization` header when you function is invoked by ilert, we actually suggest using this.

## Create the connector <a href="#connector" id="connector"></a>

Go to the connectors tab of your account.

![](<../.gitbook/assets/s1 (1) (1) (1).png>)

And create a new connector. Choose Azure Function as type (you may add the additional `Authorization` parameter as stated in the beginning of this doc.)

![](<../.gitbook/assets/s2 (1).png>)

Click on save to save the connector.

## Create the connection <a href="#connection" id="connection"></a>

Visit the alert source (view) whose alerts should trigger your serverless function. Navigate to the connections tab and create a new connection.

![](<../.gitbook/assets/s3 (2).png>)

Choose Azure Function as type and select your previously created connector. Enter a name and the url targeting your public function. You may also customize the HTTP request body that is used to invoke your function.

![](<../.gitbook/assets/s4 (1).png>)

Click on save to create the connection, you may test the connection in the following screen.
