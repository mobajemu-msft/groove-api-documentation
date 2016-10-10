# POST (/1/content/{namespace}/collection/playlists/delete)
Delete a playlist of a user.

-   [Remarks](#remarks)
-   [Examples](#examples)

## Remarks
The full delete request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
/1/content/{namespace}/collection/playlists/delete?accessToken={accessToken}
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

You can delete only one playlist at a time. Provide the ID of the playlist to delete; all other metadata will be ignored.

| Important                                                                        |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using-the-Groove-RESTful-Services/User-Authentication.md) is mandatory for this API. |

## Examples
Request object: [PlaylistAction (JSON)](JSON_PlaylistAction.md).

Response object: [PlaylistActionResponse (JSON)](JSON_PlaylistActionResponse.md).

### Delete a playlist
#### Request
This API can delete a playlist by providing its ID (obtained from an earlier Browse Playlist call).
```http
POST /1/content/music/collection/playlists/delete?accessToken=Bearer+[...]

Authorization: Bearer eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw[...]

Content-Type: application/json

{
  "Id": "music.playlist.2071a9ce-8004-00fe-c91b-436f68384ad1"
}
```

#### Response
```json
{
  "PlaylistActionResult": {
    "Id": "music.playlist.2071a9ce-8004-00fe-c91b-436f68384ad1"
  }
}
```

#### Parent
[Groove Service REST Reference](Groove-Service-REST-Reference.md)
