---
title: RadioResponse JSON object | Groove Services
description:  Learn about RadioResponse JSON object in Groove Music API.
keywords: groove music, groove api, groove radioresponse json
author: bfreydier
ms.assetid:  
---

# RadioResponse (JSON)
A list of tracks for a given radio along with the radio session id

## RadioResponse
The RadioResponse object has the following specification.

| **Member**         | **Type**                                                                         | **Description**                                                                                                                                                       |
|--------------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SessionId         | string                         | Identifier of the radio session, it might expire after 24 hours. |
| Tracks            | List of [Track](JSON-Track.md) | A list of the tracks from the radio. |

## Sample JSON syntax
```json
{
  "SessionId": "AwABFgAAAEZvbGsgLyBCbHVlcyAvIENvdW50cnkAAD09NljqvUNBv1OHNEUZa---",
  "Tracks": [
    {
      "ReleaseDate": "2016-05-27T12:00:00",
      "Duration": "00:03:11",
      "TrackNumber": 2,
      "IsExplicit": false,
      "Genres": [
        "Folk / Blues / Country"
      ],
      "Subgenres": [
        "Country"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGX0KZ8TJ",
        "Name": "If I'm Honest",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.a1c6b509-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
        "Link": "https://music.microsoft.com/album/blake-shelton/if-im-honest/a1c6b509-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.460E0000-0200-11DB-89CA-0019B92A3933",
            "Name": "Blake Shelton",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.460e0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
            "Link": "https://music.microsoft.com/artist/blake-shelton/460e0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX0KZ8TG",
      "Name": "She's Got a Way With Words",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.a3c6b509-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
      "Link": "https://music.microsoft.com/track/blake-shelton/if-im-honest/shes-got-a-way-with-words/a3c6b509-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2016-10-21T12:00:00",
      "Duration": "00:03:26",
      "TrackNumber": 9,
      "IsExplicit": false,
      "Genres": [
        "Folk / Blues / Country"
      ],
      "Subgenres": [
        "Folk & Songwriter"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Album": {
        "Id": "music.8D6KGWX35FHR",
        "Name": "You Want It Darker",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.3271090a-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
        "Link": "https://music.microsoft.com/album/leonard-cohen/you-want-it-darker/3271090a-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.464C0000-0200-11DB-89CA-0019B92A3933",
            "Name": "Leonard Cohen",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.464c0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
            "Link": "https://music.microsoft.com/artist/leonard-cohen/464c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGWX35FJ0",
      "Name": "String Reprise / Treaty",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.3b71090a-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
      "Link": "https://music.microsoft.com/track/leonard-cohen/you-want-it-darker/string-reprise-treaty/3b71090a-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    },
    {
      "ReleaseDate": "2008-10-14T12:00:00",
      "Duration": "00:02:49",
      "TrackNumber": 9,
      "IsExplicit": false,
      "Genres": [
        "Folk / Blues / Country"
      ],
      "Subgenres": [
        "Country"
      ],
      "Rights": [
        "Stream",
        "Purchase"
      ],
      "Subtitle": "Live",
      "Album": {
        "Id": "music.8D6KGX68T0WD",
        "Name": "At Folsom Prison (Legacy Edition)",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.c985f501-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
        "Link": "https://music.microsoft.com/album/johnny-cash/at-folsom-prison-legacy-edition/c985f501-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
        "Source": "Catalog",
        "CompatibleSources": "Catalog, Collection"
      },
      "Artists": [
        {
          "Role": "Main",
          "Artist": {
            "Id": "music.A7410000-0200-11DB-89CA-0019B92A3933",
            "Name": "Johnny Cash",
            "ImageUrl": "https://musicimage.xboxlive.com/content/music.a7410000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
            "Link": "https://music.microsoft.com/artist/johnny-cash/a7410000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
            "Source": "Catalog",
            "CompatibleSources": "Catalog, Collection"
          }
        }
      ],
      "Id": "music.8D6KGX68T0WV",
      "Name": "Cocaine Blues",
      "ImageUrl": "https://musicimage.xboxlive.com/content/music.db85f501-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
      "Link": "https://music.microsoft.com/track/johnny-cash/at-folsom-prison-legacy-edition/cocaine-blues/db85f501-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
      "Source": "Catalog",
      "CompatibleSources": "Catalog, Collection"
    }
  ]
}
```

#### Parent
[Groove Service REST Reference](overview.md)
