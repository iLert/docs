---
description: >-
  The ilert Google Cloud Function Integration helps you to easily connect ilert
  with Google Cloud Function.
---

# Google Cloud Function Integration

Beforehand make sure that you have created an Google Cloud Function function in your Google Cloud project and got its public `URL` handy. You might also create an additional authorization value e.g. a secure random string that you are evaluating in the HTTP request `Authorization` header when you function is invoked by ilert, we acutally suggest using this.

## Create the connector <a href="#connector" id="connector"></a>

Go to the connectors tab of your account.

![](<../.gitbook/assets/s1 (1).png>)

And create a new connector. Choose Google Cloud Function as type (you may add the additional `Authorization` parameter as stated in the beginning of this doc.)

![](<../.gitbook/assets/s2 (2).png>)

Click on save to save the connector.

## Create the connection <a href="#connection" id="connection"></a>

Visit the alert source (view) whose alerts should trigger your serverless function. Navigate to the **Alert actions** tab and click on the **Create alert action** button.

![](<../.gitbook/assets/new\_incident\_action (4).png>)

Choose Google Cloud Function as type and select your previously created connector. Enter a name and the url targeting your public function. You may also customize the HTTP request body that is used to invoke your function.

![](<../.gitbook/assets/iLert (78).png>)

Click on save to create the alert action, you may test the connection in the following screen.
