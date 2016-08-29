|                                                 |
|-------------------------------------------------|
| POST (/1/content/{namespace}/collection/delete) |
| [See Also](#seeAlsoToggle)                      |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Delete tracks from a user's collection.

-   [Remarks](#remarks)

-   [Response object](#response-object)

-   [URI parameters](#uri-parameters)

-   [Examples](#examples)

Remarks
=======

| **Important **                                                                           |
|------------------------------------------------------------------------------------------|
| [User authentication](../Endpointdocumentation/user_auth.htm) is mandatory for this API. |

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

Response object
===============

[TrackActionResponse (JSON)](../Endpointdocumentation/JSON_TrackActionResponse.htm)

URI parameters
==============

The Delete Tracks request is composed of mandatory URL parts and query parameters, described in the table below. A Delete Tracks request containing all parameters would look like the following string:

/1/content/{namespace}/collection/delete?accessToken={accessToken}

| **Parameter** | **Type** | **Description**                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| namespace     | string   | Required. The namespace to browse (Namespace).                                                                                                     |
| accessToken   | string   | A valid developer authentication Access Token obtained from Azure Data Market, used to identify the 3rd party application using the Platform APIs. |

A valid user authentication token is also required in the Authorization header to access the user's collection.

Examples
========

Request object: [TrackActionRequest (JSON)](../Endpointdocumentation/JSON_TrackActionRequest.htm).

Response object: [TrackActionResponse (JSON)](../Endpointdocumentation/JSON_TrackActionResponse.htm).

Delete tracks from collection
-----------------------------

In this example we delete a valid track (which is in the user's collection), and an invalid one (randomly-generated ID).

#### Request

POST /1/content/music/collection/delete?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org

%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26

http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims

%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience

%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a

%252f%252fdatamarket.accesscontrol.windows.net

%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

Content-Type: application/json

{

"TrackIds": \[

"music.9bb2c5c5-455c-4c15-827c-f9bfd759a458",

"music.AQQfjl2zcVUd602kG1MvCy4e\_Ae-QZkAAQ"

\]

}

#### Response

{

"TrackActionResults": \[

{

"InputId": "music.9BB2C5C5-455C-4C15-827C-F9BFD759A458",

"Error": {

"ErrorCode": "COLLECTION\_INVALID\_ID",

"Description": "Invalid collection id for this operation"

}

},

{

"InputId": "music.AQQfjl2zcVUd602kG1MvCy4e\_Ae-QZkAAQ"

}

\],

"Error": {

"ErrorCode": "COLLECTION\_SOME\_OPERATIONS\_FAILED",

"Description": "Some of the operations failed"

}

}

See also
========

#### Parent

[/1/content/{namespace}/collection/delete](../Endpointdocumentation/URI_ContentNamespaceCollectionDelete.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
