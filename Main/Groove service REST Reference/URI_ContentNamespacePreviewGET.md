|                               |
|-------------------------------|
| GET (/1/content/{id}/preview) |
| [See Also](#seeAlsoToggle)    |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Request preview streaming.

-   [Remarks](#remarks)

-   [Response object](#response-object)

-   [Query string parameters](#query-string-parameters)

-   [Examples](#examples)

Remarks
=======

The preview streaming request is composed of mandatory and optional URL parts and query parameters. A preview request containing all parameters would resemble the following string:

/1/content/{namespace.id}/preview?country={country}&clientInstanceId={clientInstanceId} &contentType={contentType}&accessToken={accessToken}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

Response object
===============

[StreamResponse (JSON)](../Endpointdocumentation/JSON_StreamResponse.htm)

Query string parameters
=======================

| **Parameter**    | **Type** | **Description**                                                                                             |
|------------------|----------|-------------------------------------------------------------------------------------------------------------|
| clientInstanceId | string   | Required. Unique client identifier. Should be persisted client-side. Can be from 32 to 128 characters long. |

Examples
========

Search example
--------------

#### Request

GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/preview?clientInstanceId=fa624b17-412c-454a-a5a5-950bb06ae019&

accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier

%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims

%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f

%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

#### Response

{

"Url": "http://progdownload.zune.net/129/580/712/170/audio.mp3?rid=052d12ef-2084-45c4-9f02-c552ef834463\_i2\_en-US\_music\_asset\_location",

"ContentType": "audio/mp3"

}

See also
========

#### Parent

[/1/content/{id}/preview](../Endpointdocumentation/URI_ContentNamespacePreview.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
