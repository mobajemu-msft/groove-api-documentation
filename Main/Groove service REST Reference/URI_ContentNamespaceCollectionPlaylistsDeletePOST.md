# POST (/1/content/{namespace}/collection/playlists/delete) 

Delete a playlist of a user.

-   [Remarks](#remarks)

-   [Examples](#examples)

##Remarks


The full delete request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
/1/content/{namespace}/collection/playlists/delete?accessToken={accessToken}
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

You can delete only one playlist at a time. Provide the ID of the playlist to delete; all other metadata will be ignored.

| Important                                                                        |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using the Groove RESTful Services/User Authentication.md) is mandatory for this API. |

##Examples


Request object: [PlaylistAction (JSON)](JSON_PlaylistAction.md).

Response object: [PlaylistActionResponse (JSON)](JSON_PlaylistActionResponse.md).

###Delete a playlist


#### Request

This API can delete a playlist by providing its ID (obtained from an earlier Browse Playlist call).
```
POST /1/content/music/collection/playlists/delete?accessToken=Bearer+
http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity
%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252f
schemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims
%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199
%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256
%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1 

Authorization: XBL3.0 x=409259454;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw[...] 

Content-Type: application/json 

{
  "Id": "music.playlist.2071a9ce-8004-00fe-c91b-436f68384ad1"
}
```
#### Response
```
{
  "PlaylistActionResult": {
    "Id": "music.playlist.2071a9ce-8004-00fe-c91b-436f68384ad1"
  }
}
```
###See also


#### Parent
