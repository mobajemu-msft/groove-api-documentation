|                                                           |
|-----------------------------------------------------------|
| POST (/1/content/{namespace}/collection/playlists/update) |
| [See Also](#seeAlsoToggle)                                |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Update a playlist on behalf of a user.

-   [Remarks](#remarks)

-   [Examples](#examples)

Remarks
=======

The full update request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

/1/content/{namespace}/collection/playlists/update?accessToken={accessToken}

You can update only one playlist at a time. Provide the ID of the playlist to be updated, the metadata you want to update, and a list of actions to perform on the playlist's tracks.

You can add and remove tracks from the playlist, or reorder existing tracks in the playlist. As with other edit APIs, when some sub-operations fail (such as adding a track), you will receive an HTTP 200 error with a non-null Error field. You can determine the failure by looking at the Error fields of the sub-operations.

Playlist names are restricted to 256 characters and cannot be empty.

| **Important **                                                                           |
|------------------------------------------------------------------------------------------|
| [User authentication](../Endpointdocumentation/user_auth.htm) is mandatory for this API. |

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

Examples
========

Request object: [PlaylistAction (JSON)](../Endpointdocumentation/JSON_PlaylistAction.htm).

Response object: [PlaylistActionResponse (JSON)](../Endpointdocumentation/JSON_PlaylistActionResponse.htm).

Update playlist metadata
------------------------

You can use this API to update the name of a playlist and control whether it's published, read-only, or both..

#### Request

POST /1/content/music/collection/playlists/update?accessToken=Bearer+http%253a%252f%252f

schemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3d

AwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice

%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256

%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=138432095;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw\[...\]

Content-Type: application/json

{

"Id": "music.playlist.88195f49-8008-00fe-a87e-5774b0384ad1",

"Name": "Fill me up with love",

"IsPublished": true

}

#### Response

{

"PlaylistActionResult": {

"Id": "music.playlist.88195f49-8008-00fe-a87e-5774b0384ad1",

"Name": "Fill me up with love",

"IsPublished": true

}

}

Update playlist metadata and tracks
-----------------------------------

You can update both metadata and tracks in the same call. Provide a list of actions to perform on tracks (only add and delete are supported for now), with the IDs of the tracks. To add tracks you only need to provide catalog IDs (obtainable from a search or lookup), but for delete you need to provide collection IDs obtained by looking up the collection or the playlist.

In this example, we add a track and delete one. Both operations are successful.

#### Request

POST /1/content/music/collection/playlists/update?accessToken=Bearer+

http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252f

identity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a

%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07

%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.

windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn

%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=138432095;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw\[...\]

Content-Type: application/json

{

"Id": "music.playlist.88195f49-8008-00fe-a87e-5774b0384ad1",

"Name": "Fill me up with hate",

"TrackActions": \[

{

"Id": "music.AQQfj2DtARB5ZkGFCMHea2k8Xge5PqgAAQ",

"Action": "Delete"

},

{

"Id": "music.2DEBEA07-0100-11DB-89CA-0019B92A3933",

"Action": "Add"

}

\]

}

#### Response

{

"PlaylistActionResult": {

"Id": "music.playlist.88195f49-8008-00fe-a87e-5774b0384ad1",

"Name": "Fill me up with hate",

"TrackActionResults": \[

{

"InputId": "music.AQQfj2DtARB5ZkGFCMHea2k8Xge5PqgAAQ"

},

{

"InputId": "music.2DEBEA07-0100-11DB-89CA-0019B92A3933",

"Id": "music.AQQfB5dE\_kGIEUeJYkX\_sl9HXgfq6y0AAQ"

}

\]

}

}

Add an invalid track to a playlist
----------------------------------

If you add an invalid track to a playlist, you'll receive a non-null Error field at the sub-operation level, and an Error at the top-level saying that some sub-operations failed. You must parse the sub-operations to determine the failure.

In this example, we try to add a random GUID as a track ID to a playlist.

#### Request

POST /1/content/music/collection/playlists/update?accessToken=Bearer+http%253a%252f

%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier

%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice

%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.

windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27

SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=138432095;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw\[...\]

Content-Type: application/json

{

"Id": "music.playlist.88195f49-8008-00fe-a87e-5774b0384ad1",

"TrackActions": \[

{

"Id": "music.E8AEDB01-23D6-4659-9916-2349BE9F9C26",

"Action": "Delete"

}

\]

}

#### Response

{

"PlaylistActionResult": {

"Id": "music.playlist.88195f49-8008-00fe-a87e-5774b0384ad1",

"TrackActionResults": \[

{

"InputId": "music.E8AEDB01-23D6-4659-9916-2349BE9F9C26",

"Error": {

"ErrorCode": "COLLECTION\_INVALID\_ID",

"Description": "Invalid collection id for this operation"

}

}

\]

},

"Error": {

"ErrorCode": "COLLECTION\_SOME\_OPERATIONS\_FAILED",

"Description": "Some of the operations failed"

}

}

Reorder tracks in a playlist
----------------------------

You can reorder tracks inside a playlist using this API. A reorder operation can only contain Move operations (cannot be mixed with Add and Delete operations).

A reorder operation must match an atomic user input: selecting a list of tracks in the playlist, and inserting them before another track.

Use the InsertBeforeTrackId field for the track before which you want to insert, and fill the TrackActions field with the tracks that should move to that new position.

#### Request

POST /1/content/music/collection/playlists/update?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=1285729083;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Ii\[...\]

Content-Type: application/json

{

"Id": "music.playlist.3fd92a44-8004-00fe-ad98-7e49091a6bd1",

"InsertBeforeTrackId": "music.AQQf-ObmX44CIE2B3mKYF2pHZAe5PqgAAQ",

"TrackActions": \[

{

"Id": "music.AQQfxVXC0f4ZKEOVOI99QZNG7Afq6y0AAQ",

"Action": "Move"

}

\]

}

#### Response

{

"PlaylistActionResult": {

"Id": "music.playlist.3fd92a44-8004-00fe-ad98-7e49091a6bd1"

}

}

See also
========

#### Parent

[/1/content/{namespace}/collection/playlists/update](../Endpointdocumentation/URI_ContentNamespaceCollectionPlaylistsUpdate.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
