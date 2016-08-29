|                                   |
|-----------------------------------|
| GET (/1/user/{namespace}/profile) |
| [See Also](#seeAlsoToggle)        |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Retrieve a user's profile or the features available in a given region.

-   [Remarks](#remarks)

-   [Examples](#examples)

Remarks
=======

The full request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

/1/user/{namespace}/profile?language={language}&country={country}&accessToken={accessToken}&contentType={contentType}&jsonp={jsonp}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

| **Note **                                                                                                         |
|-------------------------------------------------------------------------------------------------------------------|
| Accessing a user's profile requires [user authentication](http://msdn.microsoft.com/en-us/library/dn768189.aspx). |

Examples
========

User doesn't have a Groove Pass
-------------------------------

#### Request

GET /1/user/music/profile?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org

%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner

%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07

%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256

%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=847278487;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw\[...\]

#### Response

{

"HasSubscription": false,

"IsSubscriptionAvailableForPurchase": true,

"Culture": "en-US",

"Collection": {

"Token": "3.0.0.0.7.7.7",

"PlaylistCount": 2,

"RemainingPlaylistCount": 98,

"TrackCount": 3,

"RemainingTrackCount": 49997

}

}

Check Groove Pass availability in France
----------------------------------------

#### Request

GET /1/user/music/profile?country=fr&accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%

252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a

%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f

%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f

%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3

%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

#### Response

{

"IsSubscriptionAvailableForPurchase": true,

"Culture": "fr-FR"

}

Check if your region is supported by Groove
-------------------------------------------

#### Request

GET /1/user/music/profile?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org

%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner

%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07

%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3

%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

#### Response

{

"IsSubscriptionAvailableForPurchase": true,

"Culture": "en-US"

}

See also
========

#### Parent

[/1/user/{namespace}/profile](../Endpointdocumentation/URI_UserNamespaceProfile.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
