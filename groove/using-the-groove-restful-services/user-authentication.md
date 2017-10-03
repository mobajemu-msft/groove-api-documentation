---
title: Authenticate a Groove user | Groove Services
description: When using user-dependent APIs, follow these steps to authenticate Groove users and validate their perimissions.
keywords: groove api, groove api authentication, groove user authentication
author: sakley
ms.assetid:
---

| Notice to customers|
|----- |
|Starting Oct 2nd, the Onboarding to the Groove Music API is disabled. As part of the partnership, the Groove Music Pass service will be discontinued on December 31, 2017.  
After that date, Groove Music Pass content will not stream or play and our API features will not be accessible.
Please check our FAQ on <https://aka.ms/groovepartnerfaq> . All features of the Music API will be supported until Dec 31st.|


# Groove User Authentication
To use the user-authenticated APIs, you need to have an access token that authenticates
your app to a particular set of permissions for a user.

The Groove API uses the standard [OAuth 2.0](http://oauth.net/2/) authentication scheme to authenticate users and generate access tokens. You must provide an access token for every user-authenticated API call via the following header:

* `Authorization: Bearer {token}`

###Nota Bene
There are two distinct use cases depending on the API you are using:
- If the user must be authentified, you must send your request with a **User Authentication** token
- Otherwise, you must send your request with either an application token or a user token

For any API, you'll always need **one** (and exactly one) auth token with your request.

## Register a Microsoft Account application
To register your app to connect with Groove, you'll need a Microsoft account.

1. Go to the [Microsoft Application Registration Portal](https://account.live.com/developers/applications)
2. When prompted, sign in with your Microsoft account credentials.
3. Find My applications and click Add an app.
4. Enter your app's name and click Create application.
5. Scroll to the bottom of the page and check the Live SDK support box.

After you've completed these steps, an application ID and application secret are created for your app and displayed on your new app's properties page.

**Important** Treat the value of client secret the same as you would a user's password. The secret represents the key to your application and, if made available, can be used to impersonate your application.

Under the Platforms header, configure details about your app. By default a new app is created as a web app and needs one or more redirect URIs. To enable native client flows for your app as well, click the Add Platform button and choose Mobile.

## User Authentication
The way you will implement user authentication depends on the platforms you are targeting.
* If you are building a website, see the [User Authentication on the Web](User-Authentication-on-the-Web.md) documentation
* If you are building an application, see the [User Authentication in Applications](User-Authentication-in-Applications.md) documentation

## Related topics
The following topics contain high-level overviews of other concepts that apply
to the Groove API.

* [Develop with the Groove API](../api-overview.md)
* [User Authentication on the Web](user-authentication-on-the-web.md)
* [User Authentication in Applications](user-authentication-in-applications.md)
