|                                                           |
|-----------------------------------------------------------|
| POST (/1/content/{namespace}/collection/playlists/delete) |
| [See Also](#seeAlsoToggle)                                |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Delete a playlist of a user.

-   [Remarks](#remarks)

-   [Examples](#examples)

Remarks
=======

The full delete request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

/1/content/{namespace}/collection/playlists/delete?accessToken={accessToken}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

You can delete only one playlist at a time. Provide the ID of the playlist to delete; all other metadata will be ignored.

| **Important **                                                                           |
|------------------------------------------------------------------------------------------|
| [User authentication](../Endpointdocumentation/user_auth.htm) is mandatory for this API. |

Examples
========

Request object: [PlaylistAction (JSON)](../Endpointdocumentation/JSON_PlaylistAction.htm).

Response object: [PlaylistActionResponse (JSON)](../Endpointdocumentation/JSON_PlaylistActionResponse.htm).

Delete a playlist
-----------------

#### Request

This API can delete a playlist by providing its ID (obtained from an earlier Browse Playlist call).

POST /1/content/music/collection/playlists/delete?accessToken=Bearer+

http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity

%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252f

schemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims

%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199

%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256

%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=409259454;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw\[...\]

Content-Type: application/json

{

"Id": "music.playlist.2071a9ce-8004-00fe-c91b-436f68384ad1"

}

#### Response

{

"PlaylistActionResult": {

"Id": "music.playlist.2071a9ce-8004-00fe-c91b-436f68384ad1"

}

}

See also
========

#### Parent

[/1/content/{namespace}/collection/playlists/delete](../Endpointdocumentation/URI_ContentNamespaceCollectionPlaylistsDelete.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
