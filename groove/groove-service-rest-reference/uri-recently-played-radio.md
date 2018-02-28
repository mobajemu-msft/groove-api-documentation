---
title: Recently played radio stations| Groove Services
description:  Retrieve the list of recently played radio station
keywords: groove music, groove api, groove radio station, radio, recent radio, recently played
author: bfreydier
ms.assetid:  
---

# GET (/1/content/{namespace}/radio/recentlyplayed)
Browse the user's recently played radio stations

-   [Remarks](#remarks)
-   [URI parameters](#uri-parameters)
-   [Response object](#response-object)
-   [Examples](#examples)

## Remarks
The recently played radios request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would look like the following string:
```
GET /1/content/{namespace}/radio/recentlyplayed?maxItems={maxItems}&page={page}

Authorization: Bearer [...]
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

## URI parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| page          | 32-bit signed integer | Optional. The page to browse (will skip **page**\***maxItems** items). The first (and default) page is page 0.         |
| maxItems          | 32-bit signed integer | *Optional*. The number of items to browse per page. The default value is 25, and it's the maximum value allowed as well.                                                                                                                                          |

## Response object
[ContentResponse (JSON)](JSON-contentresponse.md)

## Examples
### Get recently played radios
#### Request
```http
GET /1/content/music/radio/recentlyplayed?maxItems=5 HTTP/1.1

Authorization: Bearer EwA4A0Z+BAAUXKAI8P6g2eY6bwX56k[...]
```

#### Response
```json
{
  "Radios": {
    "Items": [
      {
        "Id": "music.radio.2011c75e-adcc-4d8e-b7dd-27c6ce3d2f26",
        "Name": "Gesaffelstein",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
      },
      {
        "Id": "music.radio.99612281-a975-4e46-b86f-118259895c8f",
        "Name": "electronic / dance",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
      },
      {
        "Id": "music.radio.1f96ac2b-78dc-4ee5-8c2f-ed27686d82b0",
        "Name": "Daft Punk",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
      },
      {
        "Id": "music.radio.497c6216-4f1a-415c-9859-2e2615c68003",
        "Name": "Eminem",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
      },
      {
        "Id": "music.radio.66afd256-913e-4546-97cd-d6b26cab6c4c",
        "Name": "Avicii",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
      }
    ],
    "TotalItemCount": 27
  }
}
```

#### Parent
[Groove Service REST Reference](overview.md)
