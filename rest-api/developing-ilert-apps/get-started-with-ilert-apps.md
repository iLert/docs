---
description: >-
  iLert apps allow you to extend your alerting, on-call and status page
  experience with custom functionality and integrations build by you or other
  iLert users.
---

# Get started with iLert Apps

## App connections

In the connections overview you can see all applications that you have granted access to your account. You may see their last activity as well as revoke their access.

![Click on your profile and navigate to Manage applications](<../../.gitbook/assets/image (52) (1).png>)

{% hint style="warning" %}
Revoking an app's access invalidates the refresh token of the app, its current access\_token stays intact until it expires. It can therefore take a few minutes until the app no longer has permissions to access the granted data.
{% endhint %}

## Applications

To create your first application, go to the **Applications** tab and click on **Create new application**.

![](<../../.gitbook/assets/image (51).png>)

You may choose a name and description for your app. Please note that you cannot change the name of your app later.

![](<../../.gitbook/assets/image (58) (1).png>)

{% hint style="success" %}
You may choose to limit your app to your own iLert account, while testing or in case your app is only ment for your organization.
{% endhint %}

After clicking on **Create application**, you will be taken to the edit view of your application that allows you to adjust futher settings:

![](<../../.gitbook/assets/image (48).png>)

iLert Apps use OAuth2 for user authorization - in our next guides we explain what that means and how you can setup native or web applications as well as backend driven applications.

{% content-ref url="understanding-oauth2.md" %}
[understanding-oauth2.md](understanding-oauth2.md)
{% endcontent-ref %}

{% content-ref url="developing-a-web-or-native-app-with-oauth2-and-pkce.md" %}
[developing-a-web-or-native-app-with-oauth2-and-pkce.md](developing-a-web-or-native-app-with-oauth2-and-pkce.md)
{% endcontent-ref %}

{% content-ref url="developing-a-backend-app-with-oauth2.md" %}
[developing-a-backend-app-with-oauth2.md](developing-a-backend-app-with-oauth2.md)
{% endcontent-ref %}
