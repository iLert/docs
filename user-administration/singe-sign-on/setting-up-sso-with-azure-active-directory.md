---
description: >-
  The Azure Active Directory (Azure AD) enterprise identity service provides
  single sign-on and multi-factor authentication. You can configure iLert to use
  Azure AD as SAML provider for your users.
---

# Setting up SSO with Microsoft Azure Active Directory

When starting with Azure AD Apps things can be a bit complicated and overwhelming. In this guide we take your from zero to your own Azure AD SAML App that integrates with iLert's SSO login.

## Creating an AD Application

Login to your Microsoft Azure Dashboard. Open the directory and create a new application.

![](../../.gitbook/assets/meet\_google\_com\_is\_sharing\_your\_screen\_\_and\_Add\_your\_own\_application\_-\_Microsoft\_Azure.png)

From the seletion choose a **non gallery application**.

![](../../.gitbook/assets/Add\_your\_own\_application\_-\_Microsoft\_Azure.png)

Enter a name and create the application.

![](<../../.gitbook/assets/Add\_your\_own\_application\_-\_Microsoft\_Azure (1).png>)

## Configure your AD App SAML Settings

Configure single sign on for your newly created application.

![](../../.gitbook/assets/iLert\_SSO\_\_\_Overview\_-\_Microsoft\_Azure.png)

Choose SAML.

![](../../.gitbook/assets/iLert\_SSO\_\_\_Single\_sign-on\_-\_Microsoft\_Azure.png)

Configure the basic SAML Settings

![](<../../.gitbook/assets/iLert\_SSO\_\_\_Single\_sign-on\_-\_Microsoft\_Azure (1).png>)

## Setting up SSO in iLert

Log in to your iLert account as **account owner**, navigate to your **Account Settings** (cog right-side navigation) and click on the **Single sign-on** tab.

{% hint style="info" %}
SSO with SAML requires your account to be on a Premium or Enterprise Plan.
{% endhint %}

![](../../.gitbook/assets/iLert.png)

Copy your SAML Endpoint URL and Audience Restriction values into the Azure AD SAML App Basic Configuation.

![](../../.gitbook/assets/Basic\_SAML\_Configuration\_-\_Microsoft\_Azure.png)

Save and close the basic SAML settings. Scroll a bit down and and copy the 3 values from your AD App, you will have to download the Certificate's Base64 representation and copy the value of its file into iLerts SSO settings certificate field.

![](<../../.gitbook/assets/iLert\_SSO\_\_\_Single\_sign-on\_-\_Microsoft\_Azure (2).png>)

Transfer the values to iLert's SSO settings.

![](<../../.gitbook/assets/iLert (1).png>)

Save the the settings on both windows. SSO is now configured, however to make the login process work properly you will have to do 2 more things.

## Adjusting the SAML claim name in Azure AD

To ensure iLert gets passed the correct email of your users from Azure we have to adjust the SAML claim name.

![](<../../.gitbook/assets/iLert\_SSO\_\_\_Single\_sign-on\_-\_Microsoft\_Azure copy.png>)

![](../../.gitbook/assets/User\_Attributes\_\_\_Claims\_-\_Microsoft\_Azure.png)

Set the claim name source to `user.mail`.

![](../../.gitbook/assets/Manage\_claim\_-\_Microsoft\_Azure.png)

Save and close the modal.

![](<../../.gitbook/assets/iLert\_SSO\_\_\_Single\_sign-on\_-\_Microsoft\_Azure (1) copy.png>)

You have now properly adjusted the SAML claim name of your app.

## Adding Azure Users to your Azure AD SAML App

Right now both your iLert account and your Azure AD App are properly configured. However you have not yet added any users to your app, which means no one is able to login currently. Let's change that.

Go to your app's settings and click on **Users and Groups**.

![](../../.gitbook/assets/iLert\_SSO\_\_\_Users\_and\_groups\_-\_Microsoft\_Azure.png)

![](../../.gitbook/assets/Users\_-\_Microsoft\_Azure.png)

Click on Users and select the users that should be able to login to your iLert account. Confirm the assignment afterwards.

![](../../.gitbook/assets/Add\_Assignment\_-\_Microsoft\_Azure.png)

Your users should now be able to login to iLert using their Azure AD accounts.

![](<../../.gitbook/assets/Screenshot 2020-06-17 at 13.55.33.png>)

## Additional SSO Configurations

![](<../../.gitbook/assets/Screenshot 2020-06-17 at 13.58.03.png>)

### Auto-provisioning Azure AD Users in iLert

You can auto-provision users on their first SSO login by enabling the checkbox for **Provision new users on first sso login** in your iLert account's settings. This way user accounts will be automatically setup with the role **User** in iLert. Optionally, you can also pass in the user's role via custom SAML attributes. See  below for more information.

Keep in mind that auto-provisioning new users will require your account to have enough seats booked.

### Disable login with username and password

You can optionally disable the login for username and password combinations on your iLert account and enforce users to use SSO by disabling the checkbox for **Allow login with username and password** in your iLert account's settings.

### Passing additional attributes during auto-provisioning

Besides the `NameID` you may pass additional parameters for the user or the team to be automatically setup on the first login, please checkout our [auto provisioning section](auto-provisioning-users-and-teams.md).

