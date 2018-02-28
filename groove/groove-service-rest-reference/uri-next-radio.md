---
title: Continue a radio station| Groove Services
description:  Continue a recently played radio station
keywords: groove music, groove api, groove radio station, radio, continue radio, next
author: bfreydier
ms.assetid:  
---

# GET (/1/content/{namespace}/radio/{id}/next)
Continue a radio station that was previously created.

-   [Remarks](#remarks)
-   [URI parameters](#uri-parameters)
-   [Response object](#response-object)
-   [Examples](#examples)

## Remarks
The continue radio request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would look like the following string:
```
GET /1/content/{namespace}/radio/{id}/next?maxItems={maxItems}

Authorization: Bearer [...]
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

## URI parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id          | string | **Radio Id** (from the [ContentResponse](JSON-contentresponse.md) of TODO ) or **Session Id** (from the [RadioResponse](JSON-radioresponse.md) of [/content/radio/create](uri-create-radio.md) & [/content/radio/next](uri-next-radio.md)) |
| maxItems          | 32-bit signed integer | *Optional*. The number of items to browse per page. The default value is 25, and it's the maximum value allowed as well.                                                                                                                                          |

## Response object
[RadioResponse (JSON)](JSON-radioresponse.md)

## Examples
### Continue a session
If you have a Session Id (less than 24h old) from the latest radio response, then you should pass it to resume the same listening session instead of restarting the radio.

#### Request
```http
GET /1/content/music/radio/AwEAB1vJAALbEYnKABm5KjkzAAABAIfZxlXoJL1OpH4l/next?maxItems=5 HTTP/1.1

Authorization: Bearer EwA4A0Z+BAAUXK[...]
```

#### Response
```json
{
  "SessionId": "AwEAB1vJAALbEYnKABm5KjkzAAABAIfZxlXoJL1OpH4lCA",
  "Tracks": [
    {
      "ReleaseDate": "2012-11-13T12:00:00",
      "Duration": "00:02:36",
      "TrackNumber": 4,
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
        "Id": "music.8D6KGX78WQRQ",
        "Name": "(III)",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.0f6f7907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/crystal-castles/iii/0f6f7907-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.C52D0500-0200-11DB-89CA-0019B92A3933",
            "Name": "Crystal Castles",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.c52d0500-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/crystal-castles/c52d0500-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX78WQS4",
      "Name": "Affection",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.136f7907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/crystal-castles/iii/affection/136f7907-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2014-11-24T12:00:00",
      "Duration": "00:05:45",
      "TrackNumber": 1,
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
        "Id": "music.8D6KGWZWZ4W9",
        "Name": "Early Worx",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.cc81ac08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/trentemoller/early-worx/cc81ac08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.A36B0300-0200-11DB-89CA-0019B92A3933",
            "Name": "Trentemøller",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.a36b0300-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/trentemoller/a36b0300-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGWZWZ4W8",
      "Name": "The Forest",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.cd81ac08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/trentemoller/early-worx/the-forest/cd81ac08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2009-05-11T12:00:00",
      "Duration": "00:04:32",
      "TrackNumber": 2,
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
        "Id": "music.8D6KGX6DCTD9",
        "Name": "Moderat",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.1a870106-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/moderat/moderat/1a870106-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.D7E80400-0200-11DB-89CA-0019B92A3933",
            "Name": "Moderat",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.d7e80400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/moderat/d7e80400-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX91WN6R",
      "Name": "Rusty Nails",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.d495f605-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/moderat/moderat/rusty-nails/d495f605-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2013-10-28T12:00:00",
      "Duration": "00:04:33",
      "TrackNumber": 13,
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
        "Id": "music.8D6KGX033XLC",
        "Name": "Aleph",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.484fec08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/gesaffelstein/aleph/484fec08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.C95B0700-0200-11DB-89CA-0019B92A3933",
            "Name": "Gesaffelstein",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/gesaffelstein/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX033XL8",
      "Name": "Trans",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.4b4fec08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/gesaffelstein/aleph/trans/4b4fec08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2006-10-30T12:00:00",
      "Duration": "00:04:40",
      "TrackNumber": 6,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "Dubstep"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGWZMQ0G8",
        "Name": "Skream!",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.2bd75608-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/skream/skream/2bd75608-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.BDFC0500-0200-11DB-89CA-0019B92A3933",
            "Name": "Skream",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.bdfc0500-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/skream/bdfc0500-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGWZMQ0GL",
      "Name": "Stagger",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.31d75608-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/skream/skream/stagger/31d75608-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    }
  ]
}
```

### Restart a recently played radio
With the Radio Id from the RecentlyPlayed response (/content/radio/recentlyplayed), you can resume a listening session. 
#### Request
```http
GET /1/content/music/radio/music.radio.2011c75e-dddd-dddd-dddd-27c6ce3d2f26/next?maxItems=5 HTTP/1.1

Authorization: Bearer EwA4A0Z+BAAUXKAI8P6g2eY6bwX56kprzA+fwpcA[...]
```

#### Response
```json
{
  "SessionId": "AwEAB1vJAALbEYnKABm5KjkzAAABAIgSIFcnRXxAlDotp",
  "Tracks": [
    {
      "ReleaseDate": "2013-10-28T12:00:00",
      "Duration": "00:03:50",
      "TrackNumber": 8,
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
        "Id": "music.8D6KGX033XLC",
        "Name": "Aleph",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.484fec08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/gesaffelstein/aleph/484fec08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.C95B0700-0200-11DB-89CA-0019B92A3933",
            "Name": "Gesaffelstein",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/gesaffelstein/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX033XL5",
      "Name": "Wall Of Memories",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.4e4fec08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/gesaffelstein/aleph/wall-of-memories/4e4fec08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2009-05-11T12:00:00",
      "Duration": "00:06:14",
      "TrackNumber": 3,
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
        "Id": "music.8D6KGX6DCTD9",
        "Name": "Moderat",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.1a870106-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/moderat/moderat/1a870106-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.D7E80400-0200-11DB-89CA-0019B92A3933",
            "Name": "Moderat",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.d7e80400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/moderat/d7e80400-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX90S7F0",
      "Name": "Seamonkey",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.25aef805-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/moderat/moderat/seamonkey/25aef805-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2011-09-27T12:00:00",
      "Duration": "00:03:33",
      "TrackNumber": 1,
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
        "Id": "music.8D6KGWZKKC42",
        "Name": "The Devil's Walk",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.29352c08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/apparat/the-devils-walk/29352c08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.044F0400-0200-11DB-89CA-0019B92A3933",
            "Name": "Apparat",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.044f0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/apparat/044f0400-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGWZKKC41",
      "Name": "Sweet Unrest",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.2a352c08-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/apparat/the-devils-walk/sweet-unrest/2a352c08-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2011-03-01T12:00:00",
      "Duration": "00:04:00",
      "TrackNumber": 10,
      "IsExplicit": false,
      "Genres": [
        "More"
      ],
      "Subgenres": [
        "Miscellaneous"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX6S8813",
        "Name": "Mosaik",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.a67cb206-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/siriusmo/mosaik/a67cb206-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.11E80400-0200-11DB-89CA-0019B92A3933",
            "Name": "Siriusmo",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.11e80400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/siriusmo/11e80400-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX6S8989",
      "Name": "Einmal In Der Woche Schreien",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.7a7bb206-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/siriusmo/mosaik/einmal-in-der-woche-schreien/7a7bb206-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2011-10-11T12:00:00",
      "Duration": "00:06:38",
      "TrackNumber": 10,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "IDM / Experimental"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX7602ZZ",
        "Name": "Monkeytown",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.6c482507-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/modeselektor/monkeytown/6c482507-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.87DC0200-0200-11DB-89CA-0019B92A3933",
            "Name": "Modeselektor",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.87dc0200-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/modeselektor/87dc0200-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX760305",
      "Name": "This",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.76482507-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/modeselektor/monkeytown/this/76482507-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    }
  ]
}
```

#### Parent
[Groove Service REST Reference](overview.md)
