---
title: Delete a playlist in Groove Music| Groove Services
description:  Learn how to delete a Groove Music playlist on behalf of a user.
keywords: groove music, groove api, groove user collection, groove delete playlist
author: sakley
ms.assetid: af466950-88b4-4ef0-a63e-bcfd15a42c35
---

# POST (/1/content/{namespace}/collection/playlists/delete)
Delete a playlist of a user.

-   [Remarks](#remarks)
-   [Examples](#examples)

## Remarks
The full delete request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
POST /1/content/{namespace}/collection/playlists/delete

Authorization: Bearer [...]
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

You can delete only one playlist at a time. Provide the ID of the playlist to delete; all other metadata will be ignored.

| Important                                                                        |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using-the-Groove-RESTful-Services/User-Authentication.md) is mandatory for this API. |

## Examples
Request object: [PlaylistAction (JSON)](JSON-PlaylistAction.md).

Response object: [PlaylistActionResponse (JSON)](JSON-PlaylistActionResponse.md).

### Delete a playlist
#### Request
This API can delete a playlist by providing its ID (obtained from an earlier Browse Playlist call).
```http
POST /1/content/music/collection/playlists/delete

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
[Groove Service REST Reference](overview.md)
