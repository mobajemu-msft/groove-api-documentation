---
title: TrackActionResponse JSON object | Groove Services
description:  Learn about TrackActionResponse JSON object in Groove Music API.
keywords: groove music, groove api, groove trackactionresponse json
author: sakley
ms.assetid: 
---

# TrackActionResponse (JSON)
The output element for every track action request: add and delete.

## TrackActionResponse
The TrackActionResponse object has the following specification.

| **Member**         | **Type**                                                                         | **Description**                                                                                                                                                       |
|--------------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Error              | [Error](JSON-Error.md)                                 | *Optional.* Error object. If some of the operations failed, this object will not be null, but the result might be HTTP 200 if the operation succeeded only partially.   |
| TrackActionResults | List of [TrackActionResult](JSON-TrackActionResult.md) | Required. List of action results, with an optional Error field if the action failed, and two IDs to match the request input to the generated ID (if one is returned). |

## Sample JSON syntax
```json
{
  "TrackActionResults": [
    {
      "InputId": "music.873FB507-0100-11DB-89CA-0019B92A3933",
      "Id": "music.AQQfLejCjRp0CUSXL6Ksx2WU6Ae1P4cAAQ"
    },
    {
      "InputId": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
      "Id": "music.AQQfnOQ4L9wx0ESVhqqExHAdSge5PqgAAQ"
    }
  ]
}
```

#### Parent
[Groove Service REST Reference](overview.md)
