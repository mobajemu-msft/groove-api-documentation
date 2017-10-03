---
title: Guidelines on using the Groove Service in your application | Groove Services
description: Developers must respect and follow these guidelines in any application that uses the Groove Service.
keywords: groove api, groove api guidelines, groove api faq
author: sakley
ms.assetid: d6fafbb7-2c07-cf9d-684b-74cba337a0af
---

| Notice to customers|
|----- |
|Starting Oct 2nd, the Onboarding to the Groove Music API is disabled. As part of the partnership, the Groove Music Pass service will be discontinued on December 31, 2017.  
After that date, Groove Music Pass content will not stream or play and our API features will not be accessible.
Please check our FAQ on <https://aka.ms/groovepartnerfaq> . All features of the Music API will be supported until Dec 31st.|


# Guidelines
Following are some important rules you must respect when using the Groove Service. This list is not meant to be exhaustive:   

+ Users of the Groove Service must comply with the [Groove API TERMS OF USE]. We remind you that any commercial use (including but not limited to selling your app, access to your app, advertising etc) is subjected to a formal agreement from Microsoft. Please contact us at groovepartners [@] microsoft.com if you intend any such use.

+ Every time data from the Groove Service is used in your application or web site, you must display a deep link to the relevant content.

  For more information about deep links, see [Deep Link].  

+ You may only display an item of album art in connection with an opportunity to purchase the corresponding track in Groove or to promote the availability of the track in Groove Music.    

	These can be created using action deep links (play, buy, view) and/or text and images as described in the [Badges].

+ For images, you must use the exact URLs returned by the Groove RESTful API.  

	You may customize them only by using the parameters described in [Image Service]. Any other change that is not documented in [Image Service] will be considered a breach of the terms of use of the Groove Service.

+ Affiliate sites and applications must comply with the [Badges].

  These branding guidelines provide detailed information about how Groove assets, naming, references, and linking must be integrated in your application.

+ The application or website may neither integrate nor redistribute the content obtained from the Groove Service to other services similar to Groove, such as radio services and other music services.

+ The application or website may cache the content retrieved through the Groove RESTful API for a limited period of time — a maximum of 24 hours.  

  After 24 hours, the application must update the data by querying the Groove RESTful API again.

+ If Microsoft provides you with an authentication token, your application may enable users to sign in to their Groove Music Pass premium subscription accounts and stream audio content. Your application must not enable download of audio content from the Groove Music service, or any other form of unauthorized reproduction such as stream capture.  

+ You must authenticate each user as a premium Groove Music Pass subscriber before streaming content from the Groove Music catalog as further described in the documentation provided by Microsoft.

+ Your application must list the artist name, song title and album title prior to each stream, and if technically possible, contemporaneously with playback.

+ You must not pre-load (pre-download) more than three songs in advance for streaming, and you may do so only when the currently playing song is 20 seconds or fewer from reaching the end.

[Groove API TERMS OF USE]: ../Groove-API-Terms-of-Use.md
[Deep Link]: Deep-Link.md
[Badges]: Badges.md
[Image Service]: Image-Service.md
