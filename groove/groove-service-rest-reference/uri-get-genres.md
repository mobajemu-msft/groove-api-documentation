---
title: Get available genres for a given locale| Groove Services
description:  Learn how to browse available genres in Groove Music with the APIs.
keywords: groove music, groove api, groove user collection, groove genres api
author: sakley
ms.assetid: 0f99ebbb-63be-42ef-9147-c6dee3a593f8
---

# GET (/3/content/{namespace}/catalog/genres)
Get a list of genres available for a locale.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [Examples](#examples)

## Remarks
The BrowseGenres request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
/1/content/{namespace}/catalog/genres?language={language}&country={country}

Authorization: Bearer [...]
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

## Response object
[ContentResponse (JSON)](JSON-ContentResponse.md)

## Examples
### Browse genres
#### Request
```http
GET /3/content/music/catalog/genres?country=us&language=en

Authorization: Bearer [...]
```

#### Response (list truncated)
```json
{
  "CatalogGenres": [
    {
      "ParentName": "Blues / Folk",
      "HasEditorialPlaylists": false,
      "Name": "Acoustic Blues"
    },
    {
      "ParentName": "Electronic / Dance",
      "HasEditorialPlaylists": false,
      "Name": "Ambient"
    },
    {
      "HasEditorialPlaylists": false,
      "Name": "Electronic / Dance"
    },
    {
      "ParentName": "Country",
      "HasEditorialPlaylists": false,
      "Name": "Americana / Roots"
    },
    {
      "HasEditorialPlaylists": true,
      "Name": "Country"
    },
    {
      "ParentName": "More",
      "HasEditorialPlaylists": false,
      "Name": "Avant-Garde / Experimental"
    },
    {
      "HasEditorialPlaylists": false,
      "Name": "More"
    },
        {
      "ParentName": "Country",
      "HasEditorialPlaylists": false,
      "Name": "Bluegrass"
    },
    {
      "HasEditorialPlaylists": false,
      "Name": "Blues / Folk"
    },
    {
      "ParentName": "Electronic / Dance",
      "HasEditorialPlaylists": false,
      "Name": "Breakbeat / Electro"
    },
    {
      "ParentName": "World",
      "HasEditorialPlaylists": false,
      "Name": "Caribbean"
    },
    {
      "ParentName": "Classical",
      "HasEditorialPlaylists": false,
      "Name": "Chamber"
    },
    {
      "HasEditorialPlaylists": false,
      "Name": "Christian / Gospel"
    },
    {
      "ParentName": "Christian / Gospel",
      "HasEditorialPlaylists": false,
      "Name": "Christian Rock / Hip Hop"
    },
    {
      "ParentName": "More",
      "HasEditorialPlaylists": false,
      "Name": "Christmas Music"
    },
    {
      "HasEditorialPlaylists": false,
      "Name": "World"
    },
    {
      "HasEditorialPlaylists": true,
      "Name": "Classical"
    },
    {
      "ParentName": "Classical",
      "HasEditorialPlaylists": false,
      "Name": "Classical Guitar"
    },
    {
      "ParentName": "Classical",
      "HasEditorialPlaylists": false,
      "Name": "Classical Period"
    }
  ],
  "Culture": "en-US"
}
```

### Parent
[Groove Service REST Reference](overview.md)