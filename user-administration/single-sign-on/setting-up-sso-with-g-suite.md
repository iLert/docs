# Setting up SSO with GSuite

{% hint style="info" %}
**Account owner permissions required**

You need to be the account owner to setup SSO.
{% endhint %}

1\. Click on the cog-icon on the top right and go to **Account settings**

![](<../../.gitbook/assets/image (2) (1) (1).png>)

2\. Go to the **Single sign-on** tab.

3\. Chose **Google (OAuth 2.0)** as the authentication method and enter your Google domain.

![](<../../.gitbook/assets/Screenshot 2020-08-25 at 15.40.07.png>)

4\. Optionally set **Allow login with username and password**, if you want to allow users in ilert that are not part of your GSuite organization, and therefore, will need to login via email/username and password.

5\. Optionally set **Provision new users on first sso login**, if you don't want to manually create users in advance and have them automatically created on their first SSO login.

{% hint style="warning" %}
If you revoke a user's access at your SSO provider, the user won't be able to login to ilert via SSO, but this will not delete the user in ilert. The user needs to be manually deleted in ilert by an admin or by the account owner.
{% endhint %}

## FAQ

#### Are multiple GSuite domains supported?

No, only a single domain is supported.

