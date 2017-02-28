---
title: Create a new radio station on Groove Music| Groove Services
description:  Create a new radio station for a user,
keywords: groove music, groove api, groove radio, radio
author: bfreydier
---

# POST (/1/content/{namespace}/radio/create)
Create a radio station for the user from a seed, the service will try to find content similar to this seed from the catalog.
2 types of seeds are currently supported: artist or genre, you cannot specify both a genre and an id seed, you need to specify only one of them.
Once a radio station is created for a specific seed, it will provide an infinite stream of tracks that you can consume using the [Continue Radio](uri-next-radio.md) API.

-   [Remarks](#remarks)
-   [URI parameters](#uri-parameters)
-   [Examples](#examples)

## Remarks
The Create Radio request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would look like the following string:
```
GET /1/content/{namespace}/radio/create?maxItems={maxItems}

Authorization: Bearer [...]
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

## URI parameters
| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| maxItems          | 32-bit signed integer | *Optional*. The number of items to browse per page. The default value is 25, and it's the maximum value allowed as well.                                                                                                                                          |


## Examples

Request object: [CreateRadioRequest (JSON)](JSON-CreateRadioRequest.md)

Response object: [RadioResponse (JSON)](JSON-radioresponse.md)

### Create a radio station from a genre
#### Request
```http
POST /1/content/music/radio/create?maxItems=5 HTTP/1.1

Authorization: Bearer EwA4A0Z+BAAUXKAI8P6g2eY6b[...]

{
  "Seeds": [
    {
      "Id": "electronic / dance",
      "Type": "Genre"
    }
  ]
}
```

#### Response
```json
{
  "SessionId": "AwABEgAAAEVsZWN0cm9uaWMgLyBEYW5jZQAAGynLfqec1U6XOVo0ZyG0kQE%3D",
  "Tracks": [
    {
      "ReleaseDate": "2005-05-10T12:00:00",
      "Duration": "00:03:27",
      "TrackNumber": 1,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "Trance"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Subtitle": "- Radio Edit",
      "Album": {
        "Id": "music.8D6KGX6PPKW6",
        "Name": "Adagio For Strings",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.3bc69206-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/tiesto/adagio-for-strings/3bc69206-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.1A964200-0200-11DB-89CA-0019B92A3933",
            "Name": "Tiësto",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.1a964200-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/tiesto/1a964200-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX6PPKX7",
      "Name": "Adagio For Strings",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.1cc69206-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/tiesto/adagio-for-strings/adagio-for-strings/1cc69206-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2016-07-01T12:00:00",
      "Duration": "00:03:38",
      "TrackNumber": 2,
      "IsExplicit": false,
      "Genres": [
        "Hip Hop"
      ],
      "Subgenres": [
        "Contemporary Hip Hop"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX0NCLXZ",
        "Name": "Bobby Tarantino",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.72b4d309-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/logic/bobby-tarantino/72b4d309-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.0CAD0100-0200-11DB-89CA-0019B92A3933",
            "Name": "Logic",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.0cad0100-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/logic/0cad0100-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX0NCLXW",
      "Name": "Flexicution",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.74b4d309-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/logic/bobby-tarantino/flexicution/74b4d309-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "1994-02-10T12:00:00",
      "Duration": "00:07:51",
      "TrackNumber": 1,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "Downtempo"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX6HGT19",
        "Name": "Protection",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.acf42706-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/massive-attack/protection/acf42706-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.57570000-0200-11DB-89CA-0019B92A3933",
            "Name": "Massive Attack",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.57570000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/massive-attack/57570000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX6GN055",
      "Name": "Protection",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.7cb22d06-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/massive-attack/protection/protection/7cb22d06-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2006-12-06T12:00:00",
      "Duration": "00:03:20",
      "TrackNumber": 2,
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
        "Id": "music.8D6KGWZQB81Q",
        "Name": "Soon It Will Be Cold Enough",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.e3ea7608-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/emancipator/soon-it-will-be-cold-enough/e3ea7608-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.51A01200-0200-11DB-89CA-0019B92A3933",
            "Name": "Emancipator",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.51a01200-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/emancipator/51a01200-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGWZQB81N",
      "Name": "Wolf Drawn",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.e5ea7608-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/emancipator/soon-it-will-be-cold-enough/wolf-drawn/e5ea7608-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "1997-04-07T12:00:00",
      "Duration": "00:05:14",
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
        "Id": "music.8D6KGX6HH3KZ",
        "Name": "Dig Your Own Hole",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.b8ea2706-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/the-chemical-brothers/dig-your-own-hole/b8ea2706-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.167E0000-0200-11DB-89CA-0019B92A3933",
            "Name": "The Chemical Brothers",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.167e0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/the-chemical-brothers/167e0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX6FQFNP",
      "Name": "Block Rockin' Beats",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.e6583006-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/the-chemical-brothers/dig-your-own-hole/block-rockin-beats/e6583006-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    }
  ]
}
```

### Create a radio station from an artist
#### Request
```http
POST /1/content/music/radio/create?maxItems=5 HTTP/1.1

Authorization: Bearer EwA4A0Z+BAAUXKAI8P6g2eY6bwX56[...]

Content-Type: application/json
{
  "Seeds": [
    {
      "Id": "music.C95B0700-0200-11DB-89CA-0019B92A3933",
      "Type": "Artist"
    }
  ]
}
```

#### Response
```json
{
  "SessionId": "AwEAB1vJAALbEYnKABm5KjkzAAABAIfZxlXoJL1OpH4lCAyX0zUB",
  "Tracks": [
    {
      "ReleaseDate": "2010-08-09T12:00:00",
      "Duration": "00:03:27",
      "TrackNumber": 8,
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
        "Id": "music.8D6KGWZMKHXQ",
        "Name": "Outside the Box",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.05fc5408-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/skream/outside-the-box/05fc5408-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
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
      "Id": "music.8D6KGWZMKHZ0",
      "Name": "Listenin' to the Records On My Wall",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.0dfc5408-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/skream/outside-the-box/listenin-to-the-records-on-my-wall/0dfc5408-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2011-11-21T12:00:00",
      "Duration": "00:05:56",
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
        "Id": "music.8D6KGWZJK8LS",
        "Name": "Bromance #1 - Single",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.0bae3108-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/gesaffelstein/bromance-1-single/0bae3108-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
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
      "Id": "music.8D6KGWZJK8LR",
      "Name": "Control Movement",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.0cae3108-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/gesaffelstein/bromance-1-single/control-movement/0cae3108-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2013-04-22T12:00:00",
      "Duration": "00:06:11",
      "TrackNumber": 2,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "Breakbeat / Electro"
      ],
      "Rights": [
        "Purchase",
        "Stream"
      ],
      "Album": {
        "Id": "music.8D6KGX7M35TF",
        "Name": "Calling From The Stars",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.2045c707-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/miss-kittin/calling-from-the-stars/2045c707-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.525B0000-0200-11DB-89CA-0019B92A3933",
            "Name": "Miss Kittin",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.525b0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/miss-kittin/525b0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX7M35TC",
      "Name": "Come Into My House",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.2245c707-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/miss-kittin/calling-from-the-stars/come-into-my-house/2245c707-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2013-07-08T12:00:00",
      "Duration": "00:04:46",
      "TrackNumber": 3,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "Electronica"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX7PPZCB",
        "Name": "Tohu Bohu (Deluxe Edition)",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.f7d0e707-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/rone/tohu-bohu-deluxe-edition/f7d0e707-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.085A1500-0200-11DB-89CA-0019B92A3933",
            "Name": "Rone",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.085a1500-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/rone/085a1500-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX7PPZCR",
      "Name": "Fugu Kiss",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.fad0e707-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/rone/tohu-bohu-deluxe-edition/fugu-kiss/fad0e707-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2008-10-28T12:00:00",
      "Duration": "00:07:03",
      "TrackNumber": 6,
      "IsExplicit": false,
      "Genres": [
        "Electronic / Dance"
      ],
      "Subgenres": [
        "House"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX72LPSV",
        "Name": "Schöne Neue Extrawelt",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.098c0b07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/album/extrawelt/schone-neue-extrawelt/098c0b07-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.066C0300-0200-11DB-89CA-0019B92A3933",
            "Name": "Extrawelt",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.066c0300-0200-11db-89ca-0019b92a3933/image?locale=en-US",
            "Link": "https://music.microsoft.com/artist/extrawelt/066c0300-0200-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX72LPSN",
      "Name": "Trümmerfeld",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.0f8c0b07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
      "Link": "https://music.microsoft.com/track/extrawelt/schone-neue-extrawelt/trummerfeld/0f8c0b07-0100-11db-89ca-0019b92a3933?partnerID=AppId:0000000068164C94",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    }
  ]
}
```

#### Parent
[Groove Service REST Reference](overview.md)
