---
title: Search for items in Groove Music| Groove Services
description:  Learn how to create a Groove Music playlist on behalf of a user.
keywords: groove music, groove api, groove api search
author: sakley
ms.assetid: 6a9749d3-114d-4dfb-baf2-f77ed9e2a8ab
---


# GET (/1/content/{namespace}/search?q={query})
Search for items in a media catalog, user's collection, or both.

-   [Remarks](#remarks)
-   [URI parameters](#uri-parameters)
-   [Response object](#response-object)
-   [Query string parameters](#query-string-parameters)
-   [Examples](#examples)

## Remarks
A Search request is composed of mandatory and **Optional** URL parts and query parameters, as described in the following table. A Search request containing all parameters would look like the following string:
```
/1/content/{namespace}/search?q={query}&language={language}&country={country}&maxItems={maxItems}&filters={filters}&source={source}&contentType={contentType}&continuationToken={continuationToken}&jsonp={jsonp}

Authorization: Bearer [...]
```

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

| Note                                                                                                |
|---------------------------------------------------------------------------------------------------------|
| Using the **collection** source requires [user authentication](../Using-the-Groove-RESTful-Services/User-Authentication.md). |

## URI parameters

| **Parameter** | **Type** | **Description**                                                           |
|---------------|----------|---------------------------------------------------------------------------|
| namespace     | string   | Required. The namespace in which to perform the search. Example: "music". |

## Response object
[ContentResponse (JSON)](JSON-ContentResponse.md)

## Query string parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|---------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| query         | string   | Required unless a **continuationToken** is passed. The search query. Any special characters in the query should be properly URL-encoded (for example, multiple words should be separated by "+").                                                                                                                                                                                                                                                                                                                                                               |
| maxItems      | uint     | **Optional**. Positive integer from 1 to 25, inclusive. The maximum number of results that should be returned in the response. If this parameter is not set, the response will be limited to a maximum of 25 results per item type. There is no guarantee that all search results will be returned in a single response; the response may contain a truncated list of responses and a continuation token.                                                                                                                                                           |
| filters       | string   | **Optional**. A subcategory of item types, in case the client is interested in only one or more specific types of items. Multiple categories may be passed in this parameter by separating them with "+". Possible values for the "music" namespace are "artists", "albums", "tracks" and "playlists". If this parameter is not provided, the search will be performed in all categories (for the "music" namespace, for example, the default value of the parameter is "artists+albums+tracks+playlists").                                                                               |
| source        | string   | **Optional**. One or more data source(s), in case the client is interested in searching data from specific sources. Multiple sources may be passed in this parameter by separating them with "+". Possible values for the "music" namespace are "catalog", "collection", and "collection+catalog". The use of the "collection" source requires passing a valid user authentication token. If this parameter is not provided, the search will be performed in the "catalog" if no user authentication token is provided and "collection+catalog" if one is provided. |

## Examples
### Simple search
#### Request
```http
GET /1/content/music/search?q=daft+punk

Authorization: Bearer [...]
```

#### Response
```json
{
  "Artists": {
    "Items": [
      {
        "Genres": [
          "Electronic / Dance"
        ],
        "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
        "Name": "Daft Punk",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/artist/daft-punk/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      {
        "Genres": [
          "Pop"
        ],
        "Id": "music.CCB70200-0200-11DB-89CA-0019B92A3933",
        "Name": "LCD Soundsystem",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.ccb70200-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/artist/lcd-soundsystem/ccb70200-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      [...]
    ],
    "TotalItemCount": 5
  },
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-05-20T12:00:00",
        "IsExplicit": false,
        "LabelName": "Columbia",
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music-ppe.microsoft.com/artist/daft-punk/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            }
          }
        ],
        "Duration": "01:14:24",
        "TrackCount": 13,
        "Id": "music.8D6KGX7G2BRD",
        "Name": "Random Access Memories",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/album/daft-punk/random-access-memories/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "OtherIds": {
          "music.icpn": "886443927087"
        },
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      {
        "ReleaseDate": "2003-12-16T12:00:00",
        "IsExplicit": false,
        "LabelName": "Parlophone France",
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music-ppe.microsoft.com/artist/daft-punk/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            }
          }
        ],
        "Duration": "01:13:27",
        "TrackCount": 14,
        "Id": "music.8D6KGX6HGKJX",
        "Name": "Daft Club",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.e7d22706-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/album/daft-punk/daft-club/e7d22706-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "OtherIds": {
          "music.icpn": "0724359638959"
        },
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      [...]
    ],
    "ContinuationToken": "AodrKUUZCQQBAA8ACWRhZnQgcHVuawABAAIyNQ",
    "TotalItemCount": 129
  },
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2001-11-06T12:00:00",
        "Duration": "00:45:31",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "Rights": [
          "Stream",
          "Purchase"
        ],
        "Album": {
          "Id": "music.8D6KGX6GC9PT",
          "Name": "Alive 1997",
          "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.1c062806-0100-11db-89ca-0019b92a3933/image?locale=en-US",
          "Link": "https://music-ppe.microsoft.com/album/daft-punk/alive-1997/1c062806-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
          "Source": "Catalog",
          "CompatibleSources": "Catalog, Collection"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music-ppe.microsoft.com/artist/daft-punk/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            }
          }
        ],
        "Id": "music.8D6KGX6KXKWR",
        "Name": "Daft Punk - Alive 1997",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.12504406-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/track/daft-punk/alive-1997/daft-punk-alive-1997/12504406-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "OtherIds": {
          "music.isrc": "FRZ110902138"
        },
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      {
        "ReleaseDate": "2005-03-15T12:00:00",
        "Duration": "00:05:55",
        "TrackNumber": 10,
        "IsExplicit": false,
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Breakbeat / Electro"
        ],
        "Rights": [
          "Stream",
          "Purchase"
        ],
        "Album": {
          "Id": "music.8D6KGWZQ8TPS",
          "Name": "Human After All (Remixes)",
          "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.d57f7608-0100-11db-89ca-0019b92a3933/image?locale=en-US",
          "Link": "https://music-ppe.microsoft.com/album/daft-punk/human-after-all-remixes/d57f7608-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
          "Source": "Catalog",
          "CompatibleSources": "Catalog, Collection"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music-ppe.microsoft.com/artist/daft-punk/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            }
          }
        ],
        "Id": "music.8D6KGWZQ8TPR",
        "Name": "Robot Rock (Daft Punk Maximum Overdrive Mix)",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.d67f7608-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/track/daft-punk/human-after-all-remixes/robot-rock-daft-punk-maximum-overdrive-mix/d67f7608-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "OtherIds": {
          "music.isrc": "GBDUW0500001"
        },
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      [...]
    ],
    "ContinuationToken": "AodrKUUZCQQIAA8ACWRhZnQgcHVuawABAAIyNQ",
    "TotalItemCount": 660
  },
  "Playlists": {
    "Items": [
      {
        "Description": "The ultimate driving mix",
        "IsReadOnly": true,
        "IsPublished": true,
        "Provider": "Groove Editors",
        "Id": "music.playlist.69255db1-802e-00fe-25c1-288f1e85a6d3",
        "Name": "Driving Tracks Selected By Groove",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.69255db1-802e-00fe-25c1-288f1e85a6d3/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/playlist/driving-tracks-selected-by-groove/69255db1-802e-00fe-25c1-288f1e85a6d3?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      {
        "Description": "Grind it out with these big beats",
        "IsReadOnly": true,
        "IsPublished": true,
        "Provider": "Groove Editors",
        "Id": "music.playlist.e7c0842d-3529-00fe-0340-dc416484bcd3",
        "Name": "EDM Grind",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.e7c0842d-3529-00fe-0340-dc416484bcd3/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/playlist/edm-grind/e7c0842d-3529-00fe-0340-dc416484bcd3?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      [...]
    ],
    "TotalItemCount": 21
  },
  "Culture": "en-US"
}
```

### Searching for only albums and tracks
#### Request
```http
GET /1/content/music/search?q=daft+punk&filters=Albums+tracks

Authorization: Bearer [...]
```

#### Response
```json
{
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "01:14:24",
        "TrackCount": 13,
        "IsExplicit": false,
        "LabelName": "Columbia",
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "AlbumType": "Album",
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Random Access Memories",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "R  2749955"
        },
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2001-01-01T00:00:00Z",
        "Duration": "01:01:09",
        "TrackCount": 14,
        "IsExplicit": false,
        "LabelName": "Parlophone France",
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "AlbumType": "Album",
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.3E362806-0100-11DB-89CA-0019B92A3933",
        "Name": "Discovery",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.3E362806-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/3E362806-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "R   522606"
        },
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AYdrKUUZCQQBAAYACWRhZnQgcHVuawEAAjI1",
    "TotalItemCount": 54
  },
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "00:06:09",
        "TrackNumber": 8,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Subtitle": "feat. Pharrell Williams",
        "Album": {
          "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
          "Name": "Random Access Memories",
          "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Get Lucky",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/A83EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "T 29381286"
        },
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "00:04:34",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Album": {
          "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
          "Name": "Random Access Memories",
          "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.AA3EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Give Life Back to Music",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.AA3EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/AA3EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "T 29381293"
        },
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AYdrKUUZCQQIAAYACWRhZnQgcHVuawEAAjI1",
    "TotalItemCount": 288
  }
}
```

### Searching in both the Collection and the Catalog
The response for a Collection+Catalog search will contain for each item type (artists, albums, tracks, playlists) up to 25 (or maxItems if specified to a lower value) results per source (except for "playlists" which results will be coming from catalog only). Collection items are returned before Catalog items, and if a continuation token is present for an incomplete list it is common to both sources if they have remaining items (which means the continuation response may also contain up to 25 Collection and 25 Catalog items). In this particular example, our user's collection is quite small and the only Collection result is one artist, followed by up to 10 Catalog artists, albums and tracks. Using one of the response continuation token would then produce only Catalog results because all Collection results are included in the first response.

#### Request
```http
GET /1/content/music/search?q=daft+punk&source=collection+catalog&maxItems=10

Authorization: Bearer eyJlbmMiOiJBMTI4Q0JDK0hTMjU2IiwiYWxnIjoiUlNBLU9[...]
```

#### Response
```json
{
  "Artists": {
    "Items": [
      {
        "Id": "music.AQILAAAcxgAC3GpkUPzr8EQ",
        "Name": "Daft Punk",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
      {
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
        "Name": "Daft Punk",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "P   168791"
        },
        "Source": "Catalog"
      },
      {
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "Id": "music.5C780000-0200-11DB-89CA-0019B92A3933",
        "Name": "Stardust",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.5C780000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/5C780000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "P   361992"
        },
        "Source": "Catalog"
      },
      {
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "Id": "music.8F130500-0200-11DB-89CA-0019B92A3933",
        "Name": "Busy P",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.8F130500-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/8F130500-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "P   912342"
        },
        "Source": "Catalog"
      }
    ],
    "TotalItemCount": 4
  },
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "01:14:24",
        "TrackCount": 13,
        "IsExplicit": false,
        "LabelName": "Columbia",
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "AlbumType": "Album",
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Random Access Memories",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "R  2749955"
        },
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2001-01-01T00:00:00Z",
        "Duration": "01:01:09",
        "TrackCount": 14,
        "IsExplicit": false,
        "LabelName": "Parlophone France",
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "AlbumType": "Album",
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.3E362806-0100-11DB-89CA-0019B92A3933",
        "Name": "Discovery",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.3E362806-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/3E362806-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "R   522606"
        },
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AYdrKUUKCQQBAAcACWRhZnQgcHVuawEAAjEw",
    "TotalItemCount": 54
  },
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "00:06:09",
        "TrackNumber": 8,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Subtitle": "feat. Pharrell Williams",
        "Album": {
          "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
          "Name": "Random Access Memories",
          "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Get Lucky",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/A83EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "T 29381286"
        },
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "00:04:34",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Contemporary Pop"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Album": {
          "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
          "Name": "Random Access Memories",
          "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.AA3EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Give Life Back to Music",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.AA3EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/AA3EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "T 29381293"
        },
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AYdrKUUKCQQIAAcACWRhZnQgcHVuawEAAjEw",
    "TotalItemCount": 288
  },
  "Playlists": {
    "Items": [
      {
        "Description": "The ultimate driving mix",
        "IsReadOnly": true,
        "IsPublished": true,
        "Provider": "Groove Editors",
        "Id": "music.playlist.69255db1-802e-00fe-25c1-288f1e85a6d3",
        "Name": "Driving Tracks Selected By Groove",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.69255db1-802e-00fe-25c1-288f1e85a6d3/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/playlist/driving-tracks-selected-by-groove/69255db1-802e-00fe-25c1-288f1e85a6d3?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      {
        "Description": "Grind it out with these big beats",
        "IsReadOnly": true,
        "IsPublished": true,
        "Provider": "Groove Editors",
        "Id": "music.playlist.e7c0842d-3529-00fe-0340-dc416484bcd3",
        "Name": "EDM Grind",
        "ImageUrl": "https://musicimage.dnet.xboxlive.com/content/music.e7c0842d-3529-00fe-0340-dc416484bcd3/image?locale=en-US",
        "Link": "https://music-ppe.microsoft.com/playlist/edm-grind/e7c0842d-3529-00fe-0340-dc416484bcd3?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      [...]
    ],
    "TotalItemCount": 21
  }
}
```

#### Parent
[Groove Service REST Reference](overview.md)
