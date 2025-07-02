---
description: >-
  OAuth 2.0 has become the de facto industry standard when it comes to offering
  authorization service. It is the successor to OAuth 1.0 since 2012.
---

# Understanding OAuth2

OAuth2 or OAuth 2.0 stands for **Open Authorization**. It is a standard that allows a webservice to access resources (user data) owned by other webservices on behalf of a user.

The standard provides consented access and restricts actions to resource operations on behalf of the user that has granted the access. It works **without** sharing the actual user's credentials between the webservices.

It works for websites, as well as native applications on mobiles devices or desktops.

OAuth2 is an authorization protocol and as such designed to take care of granting access to resources, it does not handle authentication.

## Access tokens (JWT)

A successful OAuth2 flow will leave the challanging webservice with an access token, which represents the authorization to access the user's resources. Most of the time the JWT (JSON Web Token) format is used for access and or refresh tokens. ilert uses JWT tokens.

## Auth2 Roles

* **Client** (the client is the party that requires access to the resources)
* **Authorization Server** (this system handles the requests of the client to issue an access token)
* **Resource Server** (the system that handles the user's resources and that may be queried using the access tokens issued by the Authorization server)
* **User** (also called _Resource owner,_ the actual user that the client asks to grant resources access)

## OAuth2 Scopes

To describe desired resources that the client requires access to, the protocol offers scopes. Scopes are defined by the authorization server and are presented to the user during authorization. e.g. `source:w` defines an ilert scope that grants read and write permission to the alert sources of the given user.

## OAuth2 grant flows

The protocol offers differnt kind of authorization flows. With a few being already deprecated because of their potential security risk such as the **Implicit grant**.

iLert's authorization server supports the **Authorization Code grant** as well as the optional **Authorization Code with PKCE grant** (which will be described below). The **Refresh Token grant** is also supported to refresh issued access tokens.

As the Authorization Code with PKCE grant is the suggested standard way of implementing OAuth2, the following guide will focus on this grant type. PKCE stands for **Proof Key for Code Exchange** and describes the addition of a code challenge that helps to ensure that the origin of the token request is actually the same as the origin of the authorization request. It is essentially helpful in implementing secure flows for native or single page applications, that cannot keep the client secret private.

## How does OAuth2 work?

![](../../.gitbook/assets/iLert\_oauth2\_pkce.png)

### Authorization request

To begin with, the client redirects the user to the authorization server asking for permissions to the users resources. In case the user is not logged in, the authorization server will ask the user to login and afterwards to accept the access requested by the client. The client identifies itself by providing his **client\_id**. It describes its desired resources using **scope** and transfers a **code\_challenge** that helps validate the origin of the request later in step 2. When the login is successfull and the user has accepted to grant the requested permissions, the user is redirect back using the provided **redirect\_uri** parameter.

### Token request

In the sescond step, as the user is redirected back to the client after successfull authorization, the authorization server will have appended a **code** parameter to the redirect url. The client will now use this code in when requesting an **access\_token** (and/or **refresh\_**_**token**) from the authorization server_. It will also provide the plain text version of the **code\_challenge** (which was the hashed representation) of the **verifier** (a random string generated before step 1) when making this request.

If possible (for private clients, ones that can keep secrets private e.g. backend based applications) the client will also provide his **client\_secret** on this request.

If the authorization server successfully validates the code, secret and verifier it will return an access\_token (and potentially refresh\_token) in its response.

### Resource request

Finally as the client has received an access\_token in step 2, the client will be able to make calls to the resource server on behalf of the user by providing the access\_token.

## Refreshing access\_token

Access tokens have a limited lifetime, they will expire after 1 hour (may be subject to change, see token response for exact lifetime). If either the client secret was provided during the token request or the offline access scope was requested, the authorization server will also issue a refresh token with a lifetime of 1 year (may be subject to change, see token response for exact lifetime).

![](../../.gitbook/assets/oauth2\_refresh\_flow.png)

1. when making requests with the access token in case of an invalid or expired token
2. the resource server will respond with HTTP status 401
3. the client should then send another token request with the **grant\_type** **refresh\_token** as well as the refresh token
4. if the refresh token is not exired the authorization server will respond with a fresh access token
5. the client may now continue using the new access token (where he stopped in step 2)
6. the resource server will respond with the requested data to the new and unexpired access token

## Deep dive

Enough theoretics, let's dive right into native or backend app development for OAuth2.

{% content-ref url="developing-a-web-or-native-app-with-oauth2-and-pkce.md" %}
[developing-a-web-or-native-app-with-oauth2-and-pkce.md](developing-a-web-or-native-app-with-oauth2-and-pkce.md)
{% endcontent-ref %}

{% content-ref url="developing-a-backend-app-with-oauth2.md" %}
[developing-a-backend-app-with-oauth2.md](developing-a-backend-app-with-oauth2.md)
{% endcontent-ref %}
