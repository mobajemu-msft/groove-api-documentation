---
title: Common parameters for Groove Music API endpoints| Groove Services
description:  Learn about common parameters for Groove Music API requests.
keywords: groove music, groove api, groove api parameters
author: sakley
ms.assetid: 99477573-7396-459b-9f4a-f0d568900321
---

| Notice to customers|
|----- |
|Starting Oct 2nd, the Onboarding to the Groove Music API is disabled. As part of the partnership, the Groove Music Pass service will be discontinued on December 31, 2017.  
After that date, Groove Music Pass content will not stream or play and our API features will not be accessible.
Please check our FAQ on <https://aka.ms/groovepartnerfaq> . All features of the Music API will be supported until Dec 31st.|


# Parameters common to every Groove RESTful API
This topic describes parameters that are common to all methods in the Groove RESTful API.

| **Parameter**       | **Type** | **Description**                                                                                                                                                                                                                                                                                  |
|---------------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *accessToken*       | string   | Required. A valid [developer authentication](../Using-the-Groove-RESTful-Services/Obtaining-a-Developer-Access-Token.md) Access Token , used to identify the third-party application using the Groove RESTful API.                                                                     |
| *language*          | string   | Optional. The two-letter standard code identifying the requested language for the response content. If not specified, defaults to the country's primary language.                                                                                                                                |
| *country*           | string   | Optional. The standard two-letter code that identifies the country/region of the user. If not specified, the value defaults to the geolocated country/region of the client's IP address. Responses will be filtered to provide only those that match the user's country/region.                  |
| *contentType*       | string   | Optional. "xml" or "json". Specifies the requested format for response serialization. Default is json. This parameter should be used only when it's not possible to customize standard HTTP headers; otherwise the recommended way to choose serialization format is by using the Accept header. |
| *continuationToken* | string   | Optional. A Continuation Token provided in an earlier service response and optionally passed back to the service to request the continuation of an incomplete list of content.                                                                                                                   |
| *jsonp*             | string   | Optional. The name of the JavaScript callback function as defined by the JSONP pattern.                                                                                                                                                                                                          |

Some of the APIs also require a user authentication token in the Authorization header of the request in order to access user-authenticated features such as collection management or full track streaming. See [User Authentication](../Using-the-Groove-RESTful-Services/User-Authentication.md) for more information on how to create a user authentication header.

#### Parent
[Groove Service REST Reference](overview.md)
