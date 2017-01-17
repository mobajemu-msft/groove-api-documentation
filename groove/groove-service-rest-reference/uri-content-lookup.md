---
title: Lookup items from the catalog| Groove Services
description:  Learn how to lookup items from a media catalog with Groove Music API.
keywords: groove music, groove api, groove user collection, groove api lookup
author: sakley
ms.assetid: 
---

# GET (/1/content/{id}/lookup)
Look up one or several items from a media catalog and/or user's collection.

-   [Remarks](#remarks)
-   [URI parameters](#uri-parameters)
-   [Response object](#response-object)
-   [Query string parameters](#query-string-parameters)
-   [Catalog lookup examples](#catalog-lookup-examples)
-   [Lookup by ISRC](#lookup-by-isrc)
-   [Lookup by ICPN](#lookup-by-icpn)
-   [Collection lookup examples](#collection-lookup-examples)

## Remarks
A lookup request is composed of mandatory and optional URL parts and query parameters, as described in the following table. A lookup request containing all parameters would look like the following string:
```http
/1/content/{id1+id2+id3}/lookup?language={language}&country={country}&extras={extras}&source={source}
&contentType={contentType}&continuationToken={continuationToken}&accessToken={accessToken}&jsonp={jsonp}
```

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

| Note                                                                                                |
|---------------------------------------------------------------------------------------------------------|
| Using the **collection** source requires [user authentication](../Using-the-Groove-RESTful-Services/User-Authentication.md). |

## URI parameters
| **Parameter** | **Type** | **Description**                                                                                                                                                                                   |
|---------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ids           | string   | Required. The ID or IDs to be looked up. Each ID is prefixed by a namespace and ".". Multiple IDs are separated by "+". The total length of all IDs must be less than or equal to 250 characters.

| Note|                       
|------------------------|                  
| ISRC and ICPN external IDs are accepted as input by the Lookup API (see [Namespaces supported](Namespace.md)), but only when the source is Catalog. |                  

## Response object
[ContentResponse (JSON)](JSON-ContentResponse.md)

## Query string parameters
| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|---------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| source        | string   | *Optional*. One or more data source(s), in case the client is interested in lookup up data in specific sources. Multiple sources may be passed in this parameter by separating them with "+". Possible values for the "music" namespace are "catalog", "collection", and "collection+catalog". The use of the "collection" source requires passing a valid user authentication token. If this parameter is not provided, the lookup will be performed in the "catalog" if no user authentication token is provided and "collection+catalog" if one is provided. |
| extras        | string   | *Optional.* List of extra fields that can be optionally requested (at the cost of performance). Multiple values must be separated with "+".                                                                                                                                                                                                                                                                                                                                                                                                                     |

## Catalog lookup examples
### Artist lookup
#### Request
```http
GET /1/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/lookup

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
      }
    ]
  }
}
```

### Album lookup
#### Request
```http
GET /1/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/lookup

Authorization: Bearer [...]
```

#### Response
```json
{
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
        "Duration": "01:14:26",
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
      }
    ]
  }
}
```

### Track lookup
#### Request
```http
GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/lookup

Authorization: Bearer [...]
```

#### Response
```json
{
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
              "Id": "music.CFDD6300-0200-11DB-89CA-0019B92A3933",
              "Name": "Daft Punk feat. Pharrell Williams and Nile Rodgers",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.CFDD6300-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/CFDD6300-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
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
      }
    ]
  }
}
```

### Catalog Playlist lookup
#### Request
```http
GET /1/content/music.playlist.ae8d3746-8039-00fe-8f53-dcedda4728d4/lookup?source=catalog

Authorization: Bearer [...]
```

#### Response
```json
{
  "Playlists": {
    "Items": [
      {
        "Description": "1990s throwback hits, from Britney Spears to Pearl Jam and more!",
        "IsReadOnly": true,
        "IsPublished": true,
        "Tracks": {
          "Items": [
            {
              "ReleaseDate": "1999-02-22T00:00:00Z",
              "Duration": "00:03:34",
              "TrackNumber": 5,
              "IsExplicit": false,
              "Genres": [
                "R&B / Soul"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-02-22T00:00:00Z",
                "Genres": [
                  "R&B / Soul"
                ],
                "Id": "music.8D6KGX65DHCG",
                "Name": "Fanmail",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.2341db01-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/tlc/fanmail/2341db01-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.7F7B0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "TLC",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.7f7b0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/tlc/7f7b0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.7F7B0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "TLC",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.7f7b0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/tlc/7f7b0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX65DHCN",
              "Name": "No Scrubs",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.2341db01-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/tlc/fanmail/no-scrubs/2d41db01-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2015-06-24T00:00:00Z",
              "Duration": "00:03:33",
              "TrackNumber": 3,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase"
              ],
              "Album": {
                "ReleaseDate": "2015-06-24T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX05N54Q",
                "Name": "Magic Mike XXL: Original Motion Picture Soundtrack",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.b5d50d09-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/backstreet-boys/magic-mike-xxl-original-motion-picture-soundtrack/b5d50d09-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.3C0A0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Backstreet Boys",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.3c0a0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/backstreet-boys/3c0a0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.09890000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Various Artists",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.09890000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/various-artists/09890000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX05N555",
              "Name": "I Want It That Way",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.b5d50d09-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/backstreet-boys/magic-mike-xxl-original-motion-picture-soundtrack/i-want-it-that-way/b8d50d09-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-01-12T00:00:00Z",
              "Duration": "00:03:31",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-01-12T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX51SGL8",
                "Name": "...Baby One More Time (Digital Deluxe Version)",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.6b1c3a00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/britney-spears/baby-one-more-time-digital-deluxe-version/6b1c3a00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.BF100000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Britney Spears",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.bf100000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/britney-spears/bf100000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.BF100000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Britney Spears",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.bf100000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/britney-spears/bf100000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX5K15D4",
              "Name": "...Baby One More Time",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.6b1c3a00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/britney-spears/baby-one-more-time-digital-deluxe-version/baby-one-more-time/8f3ac600-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-01-01T00:00:00Z",
              "Duration": "00:04:28",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "R&B / Soul"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-01-01T00:00:00Z",
                "Genres": [
                  "R&B / Soul"
                ],
                "Id": "music.8D6KGX5C6WS0",
                "Name": "Say My Name",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.fb708e00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/destinys-child/say-my-name/fb708e00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.66200000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Destiny's Child",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.66200000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/destinys-child/66200000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.66200000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Destiny's Child",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.66200000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/destinys-child/66200000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX5C6WRX",
              "Name": "Say My Name (Album Version)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.fb708e00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/destinys-child/say-my-name/say-my-name-album-version/fd708e00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2013-06-11T00:00:00Z",
              "Duration": "00:03:47",
              "TrackNumber": 16,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "2013-06-11T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX7M1FCT",
                "Name": "Hip Hop 100 Hits - Urban rap & R n B anthems inc. Jay Z, A$ap Rocky, Wu-Tang Clan & Nas",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.b882c407-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/will-smith/hip-hop-100-hits-urban-rap-r-n-b-anthems-inc-jay-z-a-a/b882c407-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.4A8C0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Will Smith",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.4a8c0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/will-smith/4a8c0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.09890000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Various Artists",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.09890000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/various-artists/09890000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX7M1F9R",
              "Name": "Gettin' Jiggy Wit It",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.b882c407-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/will-smith/hip-hop-100-hits-urban-rap-r-n-b-anthems-inc-jay-z-a-a/gettin-jiggy-wit-it/c682c407-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1996-11-04T00:00:00Z",
              "Duration": "00:02:53",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1996-11-04T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX6F8CP4",
                "Name": "Spice",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.91943a06-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/spice-girls/spice/91943a06-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.E8770000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Spice Girls",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.e8770000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/spice-girls/e8770000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.E8770000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Spice Girls",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.e8770000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/spice-girls/e8770000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX6GTDNR",
              "Name": "Wannabe (Radio Edit)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.91943a06-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/spice-girls/spice/wannabe-radio-edit/10f72f06-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1972-01-01T00:00:00Z",
              "Duration": "00:03:22",
              "TrackNumber": 30,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1972-01-01T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX568510",
                "Name": "The Essential Michael Jackson",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.55094300-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/michael-jackson/the-essential-michael-jackson/55094300-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.89590000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Michael Jackson",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.89590000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/michael-jackson/89590000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.89590000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Michael Jackson",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.89590000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/michael-jackson/89590000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX56857J",
              "Name": "Black or White (Single Version)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.55094300-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/michael-jackson/the-essential-michael-jackson/black-or-white-single-version/91094300-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2014-11-18T00:00:00Z",
              "Duration": "00:04:17",
              "TrackNumber": 42,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "2014-11-18T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGWZWJ185",
                "Name": "100 Hits of the '90s",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.ae39a908-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/spin-doctors/100-hits-of-the-90s/ae39a908-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.EF770000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Spin Doctors",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.ef770000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/spin-doctors/ef770000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.09890000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Various Artists",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.09890000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/various-artists/09890000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGWZWJ17T",
              "Name": "Two Princes",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.ae39a908-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/spin-doctors/100-hits-of-the-90s/two-princes/d839a908-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2014-07-25T00:00:00Z",
              "Duration": "00:03:28",
              "TrackNumber": 3,
              "IsExplicit": false,
              "Genres": [
                "Dance"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "2014-07-25T00:00:00Z",
                "Genres": [
                  "Dance"
                ],
                "Id": "music.8D6KGWZQB7WH",
                "Name": "The Essential *NSYNC",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.62ea7608-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/nsync/the-essential-nsync/62ea7608-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.25000000-0200-11DB-89CA-0019B92A3933",
                    "Name": "NSYNC",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.25000000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/nsync/25000000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.25000000-0200-11DB-89CA-0019B92A3933",
                    "Name": "NSYNC",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.25000000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/nsync/25000000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGWZQB7WD",
              "Name": "Tearin' up My Heart (Radio Edit)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.62ea7608-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/nsync/the-essential-nsync/tearin-up-my-heart-radio-edit/65ea7608-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1990-01-01T00:00:00Z",
              "Duration": "00:04:52",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Rock / Indie"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1990-01-01T00:00:00Z",
                "Genres": [
                  "Rock / Indie"
                ],
                "Id": "music.8D6KGWZSJGXF",
                "Name": "The Razors Edge",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.ca5d9208-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/ac-dc/the-razors-edge/ca5d9208-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.D6040100-0200-11DB-89CA-0019B92A3933",
                    "Name": "AC/DC",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.d6040100-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ac-dc/d6040100-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.D6040100-0200-11DB-89CA-0019B92A3933",
                    "Name": "AC/DC",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.d6040100-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ac-dc/d6040100-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGWZSJGXD",
              "Name": "Thunderstruck",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.ca5d9208-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/ac-dc/the-razors-edge/thunderstruck/cb5d9208-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2015-06-24T00:00:00Z",
              "Duration": "00:04:10",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "R&B / Soul"
              ],
              "Rights": [
                "Purchase"
              ],
              "Album": {
                "ReleaseDate": "2015-06-24T00:00:00Z",
                "Genres": [
                  "R&B / Soul"
                ],
                "Id": "music.8D6KGX05N530",
                "Name": "Magic Mike XXL: Original Motion Picture Soundtrack",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.f9d50d09-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/ginuwine/magic-mike-xxl-original-motion-picture-soundtrack/f9d50d09-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.20300000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Ginuwine",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.20300000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ginuwine/20300000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.09890000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Various Artists",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.09890000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/various-artists/09890000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX05N52Z",
              "Name": "Pony",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.f9d50d09-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/ginuwine/magic-mike-xxl-original-motion-picture-soundtrack/pony/fad50d09-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1996-01-01T00:00:00Z",
              "Duration": "00:05:46",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1996-01-01T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX0KZ2MH",
                "Name": "My Boo (Hitman's Club Mix)",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.9ea8b509-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/ghost-town-djs/my-boo-hitmans-club-mix/9ea8b509-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.B94C0F00-0200-11DB-89CA-0019B92A3933",
                    "Name": "Ghost Town DJs",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.b94c0f00-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ghost-town-djs/b94c0f00-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.B94C0F00-0200-11DB-89CA-0019B92A3933",
                    "Name": "Ghost Town DJs",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.b94c0f00-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ghost-town-djs/b94c0f00-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX0KZ2MG",
              "Name": "My Boo (Hitman's Club Mix)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.9ea8b509-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/ghost-town-djs/my-boo-hitmans-club-mix/my-boo-hitmans-club-mix/9fa8b509-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-08-24T00:00:00Z",
              "Duration": "00:03:37",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-08-24T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX6GCKXL",
                "Name": "Christina Aguilera",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.01252806-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/christina-aguilera/christina-aguilera/01252806-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.8E170000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Christina Aguilera",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.8e170000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/christina-aguilera/8e170000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.8E170000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Christina Aguilera",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.8e170000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/christina-aguilera/8e170000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX6FXXLG",
              "Name": "Genie in a Bottle",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.01252806-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/christina-aguilera/christina-aguilera/genie-in-a-bottle/adef3206-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-11-01T00:00:00Z",
              "Duration": "00:04:30",
              "TrackNumber": 5,
              "IsExplicit": true,
              "Genres": [
                "Rap / Hip-Hop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-11-01T00:00:00Z",
                "Genres": [
                  "Rap / Hip-Hop"
                ],
                "Id": "music.8D6KGX51CFXL",
                "Name": "Stankonia",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.c1be0400-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/outkast/stankonia/c1be0400-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.DF620000-0200-11DB-89CA-0019B92A3933",
                    "Name": "OutKast",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.df620000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/outkast/df620000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.DF620000-0200-11DB-89CA-0019B92A3933",
                    "Name": "OutKast",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.df620000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/outkast/df620000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX51CFXS",
              "Name": "Ms. Jackson",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.c1be0400-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/outkast/stankonia/ms-jackson/cbbe0400-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1998-04-07T00:00:00Z",
              "Duration": "00:04:05",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1998-04-07T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX659TD0",
                "Name": "Torn/Wishing I Was There",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.732ed801-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/natalie-imbruglia/torn-wishing-i-was-there/732ed801-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.115E0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Natalie Imbruglia",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.115e0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/natalie-imbruglia/115e0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.115E0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Natalie Imbruglia",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.115e0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/natalie-imbruglia/115e0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX659TCX",
              "Name": "Torn",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.732ed801-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/natalie-imbruglia/torn-wishing-i-was-there/torn/752ed801-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1995-09-26T00:00:00Z",
              "Duration": "00:04:18",
              "TrackNumber": 5,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1995-09-26T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX50PWJL",
                "Name": "Daydream",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.718b0c00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/mariah-carey/daydream/718b0c00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.BE550000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Mariah Carey",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.be550000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/mariah-carey/be550000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.BE550000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Mariah Carey",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.be550000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/mariah-carey/be550000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX50MMVB",
              "Name": "Always Be My Baby",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.718b0c00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/mariah-carey/daydream/always-be-my-baby/4da50d00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1975-01-01T00:00:00Z",
              "Duration": "00:04:58",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Rock / Indie"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1975-01-01T00:00:00Z",
                "Genres": [
                  "Rock / Indie"
                ],
                "Id": "music.8D6KGX5C765G",
                "Name": "Armageddon - The Album",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.73968e00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/aerosmith/armageddon-the-album/73968e00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.5B020000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Aerosmith",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.5b020000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/aerosmith/5b020000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.CBB21F00-0200-11DB-89CA-0019B92A3933",
                    "Name": "Armageddon - The Album",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.cbb21f00-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/armageddon-the-album/cbb21f00-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX5C765N",
              "Name": "I Don't Want to Miss a Thing",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.73968e00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/aerosmith/armageddon-the-album/i-dont-want-to-miss-a-thing/7d968e00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-06-15T00:00:00Z",
              "Duration": "00:04:55",
              "TrackNumber": 5,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-06-15T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX6SK4RC",
                "Name": "Supernatural (Legacy Edition)",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.e206b606-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/santana/supernatural-legacy-edition/e206b606-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.63C41800-0200-11DB-89CA-0019B92A3933",
                    "Name": "Santana",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.63c41800-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/santana/63c41800-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.63C41800-0200-11DB-89CA-0019B92A3933",
                    "Name": "Santana",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.63c41800-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/santana/63c41800-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX6SK4R6",
              "Name": "Smooth",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.e206b606-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/santana/supernatural-legacy-edition/smooth/e706b606-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2013-06-09T00:00:00Z",
              "Duration": "00:04:58",
              "TrackNumber": 68,
              "IsExplicit": false,
              "Genres": [
                "R&B / Soul"
              ],
              "Rights": [
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "2013-06-09T00:00:00Z",
                "Genres": [
                  "R&B / Soul"
                ],
                "Id": "music.8D6KGX7M0J6X",
                "Name": "R&B - 100 Hits - The Greatest R n B album - 100 R & B Classics featuring Usher, Pitbull and Justin Timberlake",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.072dc407-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/the-fugees/r-b-100-hits-the-greatest-r-n-b-album-100-r-b-classi/072dc407-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.747F0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "The Fugees",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.747f0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/the-fugees/747f0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.09890000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Various Artists",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.09890000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/various-artists/09890000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX7M0J58",
              "Name": "Killing Me Softly with His Song",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.072dc407-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/the-fugees/r-b-100-hits-the-greatest-r-n-b-album-100-r-b-classi/killing-me-softly-with-his-song/492dc407-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1998-11-16T00:00:00Z",
              "Duration": "00:03:08",
              "TrackNumber": 4,
              "IsExplicit": false,
              "Genres": [
                "Rock / Indie"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1998-11-16T00:00:00Z",
                "Genres": [
                  "Rock / Indie"
                ],
                "Id": "music.8D6KGWX29TMB",
                "Name": "Americana",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.a7cd1c0a-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/the-offspring/americana/a7cd1c0a-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.12C20000-0200-11DB-89CA-0019B92A3933",
                    "Name": "The Offspring",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.12c20000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/the-offspring/12c20000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.12C20000-0200-11DB-89CA-0019B92A3933",
                    "Name": "The Offspring",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.12c20000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/the-offspring/12c20000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGWX29TMQ",
              "Name": "Pretty Fly (For A White Guy)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.a7cd1c0a-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/the-offspring/americana/pretty-fly-for-a-white-guy/abcd1c0a-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1995-01-01T00:00:00Z",
              "Duration": "00:04:03",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "Rock / Indie"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1995-01-01T00:00:00Z",
                "Genres": [
                  "Rock / Indie"
                ],
                "Id": "music.8D6KGX508BHB",
                "Name": "Ricky Martin",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.73120900-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/ricky-martin/ricky-martin/73120900-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.E86D0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Ricky Martin",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.e86d0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ricky-martin/e86d0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.E86D0000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Ricky Martin",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.e86d0000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/ricky-martin/e86d0000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX508CPB",
              "Name": "Livin' la Vida Loca",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.73120900-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/ricky-martin/ricky-martin/livin-la-vida-loca/2b1e0900-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1992-03-17T00:00:00Z",
              "Duration": "00:03:15",
              "TrackNumber": 2,
              "IsExplicit": false,
              "Genres": [
                "Rap / Hip-Hop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1992-03-17T00:00:00Z",
                "Genres": [
                  "Rap / Hip-Hop"
                ],
                "Id": "music.8D6KGX50BRR4",
                "Name": "Totally Krossed Out",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.c51d0800-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/kris-kross/totally-krossed-out/c51d0800-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.29480000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Kris Kross",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.29480000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/kris-kross/29480000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.29480000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Kris Kross",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.29480000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/kris-kross/29480000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX508JZQ",
              "Name": "Jump",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.c51d0800-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/kris-kross/totally-krossed-out/jump/bb080900-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-01-12T00:00:00Z",
              "Duration": "00:03:18",
              "TrackNumber": 2,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-01-12T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGX51SGL8",
                "Name": "...Baby One More Time (Digital Deluxe Version)",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.6b1c3a00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/britney-spears/baby-one-more-time-digital-deluxe-version/6b1c3a00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.BF100000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Britney Spears",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.bf100000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/britney-spears/bf100000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.BF100000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Britney Spears",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.bf100000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/britney-spears/bf100000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX5K1554",
              "Name": "(You Drive Me) Crazy",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.6b1c3a00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/britney-spears/baby-one-more-time-digital-deluxe-version/you-drive-me-crazy/713ac600-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "2014-11-18T00:00:00Z",
              "Duration": "00:03:40",
              "TrackNumber": 41,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "2014-11-18T00:00:00Z",
                "Genres": [
                  "Pop"
                ],
                "Id": "music.8D6KGWZWJ185",
                "Name": "100 Hits of the '90s",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.ae39a908-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/lou-bega/100-hits-of-the-90s/ae39a908-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.F0500000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Lou Bega",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.f0500000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/lou-bega/f0500000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.09890000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Various Artists",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.09890000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/various-artists/09890000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGWZWJ17B",
              "Name": "Mambo No. 5 (A Little Bit of...)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.ae39a908-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/lou-bega/100-hits-of-the-90s/mambo-no-5-a-little-bit-of/d739a908-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            },
            {
              "ReleaseDate": "1999-01-01T00:00:00Z",
              "Duration": "00:03:47",
              "TrackNumber": 1,
              "IsExplicit": false,
              "Genres": [
                "R&B / Soul"
              ],
              "Rights": [
                "Purchase",
                "Stream"
              ],
              "Album": {
                "ReleaseDate": "1999-01-01T00:00:00Z",
                "Genres": [
                  "R&B / Soul"
                ],
                "Id": "music.8D6KGX5C6WFG",
                "Name": "Jumpin', Jumpin'",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.07718e00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
                "Link": "https://music.microsoft.com/album/destinys-child/jumpin-jumpin/07718e00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                "Source": "Catalog",
                "CompatibleSources": "Catalog, Collection"
              },
              "Artists": [
                {
                  "Role": "Main",
                  "Artist": {
                    "Id": "music.66200000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Destiny's Child",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.66200000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/destinys-child/66200000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.66200000-0200-11DB-89CA-0019B92A3933",
                    "Name": "Destiny's Child",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.66200000-0200-11db-89ca-0019b92a3933/image?locale=en-GB",
                    "Link": "https://music.microsoft.com/artist/destinys-child/66200000-0200-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
                    "Source": "Catalog",
                    "CompatibleSources": "Catalog, Collection"
                  }
                }
              ],
              "Id": "music.8D6KGX5C6WFX",
              "Name": "Jumpin', Jumpin' (Album Version)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.07718e00-0100-11db-89ca-0019b92a3933/image?locale=en-GB",
              "Link": "https://music.microsoft.com/track/destinys-child/jumpin-jumpin/jumpin-jumpin-album-version/09718e00-0100-11db-89ca-0019b92a3933?partnerID=AppId:00000000401C1787",
              "Source": "Catalog",
              "CompatibleSources": "Catalog, Collection"
            }
          ],
          "ContinuationToken": "Au6v09MACQgIAAcBAS1wbGF5bGlzdC5hZThkMzc0Ni04MDM5LTAwZmUtOGY1My1kY2VkZGE0NzI4ZDQAAQACMjU",
          "TotalItemCount": 151
        },
        "TrackCount": 151,
        "Id": "music.playlist.ae8d3746-8039-00fe-8f53-dcedda4728d4",
        "Name": "90s SMASH HITS",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.playlist.ae8d3746-8039-00fe-8f53-dcedda4728d4/image?locale=en-GB",
        "Link": "https://music.microsoft.com/playlist/90s-smash-hits/ae8d3746-8039-00fe-8f53-dcedda4728d4?partnerID=AppId:00000000401C1787",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
      }
    ]
  }
}
```

### Lookup of a nonexistent ID
#### Request
```http
GET /1/content/music.00000000-0000-0000-0000-000000000000/lookup?accessToken=Bearer+[...]
```

#### Response
```json
HTTP/1.1 404 Not Found
{
 "Error": {
   "ErrorCode": "CATALOG-NO-RESULT",
   "Description": "Item does not exist"
 }
}
```

### More complex example
The following examples use the following optional features:

-   Batching: requests three music IDs at the same time

-   Choosing XML content-type instead of JSON

-   Passing the developer authentication token as a header instead of query parameter

#### Request
```http
GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933+music.B13EB907-0100-11DB-89CA-0019B92A3933
+music.C61C0000-0200-11DB-89CA-0019B92A3933/lookup HTTP/1.1

Accept: application/xml

Authorization: Bearer http%3a%2f%2fschemas.xmlsoap.org%2fws%2f2005%2f05%2fidentity%2fclaims%2fnameidentifier=AwesomePartner  	
&http%3a%2f%2fschemas.microsoft.com%2faccesscontrolservice%2f2010%2f07%2fclaims%2fidentityprovider=
https%3a%2f%2fdatamarket.accesscontrol.windows.net&Audience=http%3a%2f%2fmusic.xboxlive.com%2f&ExpiresOn=1609459199
&Issuer=https%3a%2f%2fdatamarket.accesscontrol.windows.net&HMACSHA256=0pVJ3%2fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%3d
```

#### Response
```xml
<ContentResponse xmlns="http://schemas.microsoft.com/xboxmusic/2013/10/platform" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Albums>
    <Items>
      <Album>
        <Id>music.B13EB907-0100-11DB-89CA-0019B92A3933</Id>
        <ImageUrl>https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US</ImageUrl>
        <Link>https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner</Link>
        <Name>Random Access Memories</Name>
        <OtherIds>
          <OtherId>
            <Namespace>music.amg</Namespace>
            <Id>R  2749955</Id>
          </OtherId>
        </OtherIds>
        <Source>Catalog</Source>
        <AlbumType>Album</AlbumType>
        <Artists>
          <Contributor>
            <Artist>
              <Id>music.C61C0000-0200-11DB-89CA-0019B92A3933</Id>
              <ImageUrl>https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US</ImageUrl>
              <Link>https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner</Link>
              <Name>Daft Punk</Name>
              <Source>Catalog</Source>
            </Artist>
            <Role>Main</Role>
          </Contributor>
        </Artists>
        <Duration>PT1H14M24S</Duration>
        <Genres>
          <Genre>Pop</Genre>
        </Genres>
        <IsExplicit>false</IsExplicit>
        <LabelName>Columbia</LabelName>
        <ReleaseDate>2013-05-09T00:00:00Z</ReleaseDate>
        <Subgenres>
          <Genre>Contemporary Pop</Genre>
        </Subgenres>
        <TrackCount>13</TrackCount>
      </Album>
    </Items>
  </Albums>
  <Artists>
    <Items>
      <Artist>
        <Id>music.C61C0000-0200-11DB-89CA-0019B92A3933</Id>
        <ImageUrl>https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US</ImageUrl>
        <Link>https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner</Link>
        <Name>Daft Punk</Name>
        <OtherIds>
          <OtherId>
            <Namespace>music.amg</Namespace>
            <Id>P   168791</Id>
          </OtherId>
        </OtherIds>
        <Source>Catalog</Source>
        <Genres>
          <Genre>Electronic / Dance</Genre>
        </Genres>
        <Subgenres>
          <Genre>Dance</Genre>
        </Subgenres>
      </Artist>
    </Items>
  </Artists>
  <Tracks>
    <Items>
      <Track>
        <Id>music.A83EB907-0100-11DB-89CA-0019B92A3933</Id>
        <ImageUrl>https://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US</ImageUrl>
        <Link>https://music.microsoft.com/Track/A83EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner</Link>
        <Name>Get Lucky</Name>
        <OtherIds>
          <OtherId>
            <Namespace>music.amg</Namespace>
            <Id>T 29381286</Id>
          </OtherId>
        </OtherIds>
        <Source>Catalog</Source>
        <Album>
          <Id>music.B13EB907-0100-11DB-89CA-0019B92A3933</Id>
          <ImageUrl>https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US</ImageUrl>
          <Link>https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner</Link>
          <Name>Random Access Memories</Name>
          <Source>Catalog</Source>
        </Album>
        <Artists>
          <Contributor>
            <Artist>
              <Id>music.C61C0000-0200-11DB-89CA-0019B92A3933</Id>
              <ImageUrl>https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US</ImageUrl>
              <Link>https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner</Link>
              <Name>Daft Punk</Name>
              <Source>Catalog</Source>
            </Artist>
            <Role>Main</Role>
          </Contributor>
        </Artists>
        <Duration>PT6M7S</Duration>
        <Genres>
          <Genre>Pop</Genre>
        </Genres>
        <IsExplicit>false</IsExplicit>
        <ReleaseDate>2013-05-09T00:00:00Z</ReleaseDate>
        <Rights>
          <Right>Purchase</Right>
          <Right>Stream</Right>
          <Right>FreeStream</Right>
        </Rights>
        <Subgenres>
          <Genre>Contemporary Pop</Genre>
        </Subgenres>
        <Subtitle>feat. Pharrell Williams</Subtitle>
        <TrackNumber>8</TrackNumber>
      </Track>
    </Items>
  </Tracks>
</ContentResponse>
```

### Batch lookup with extra details
#### Request
```http
GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933+
music.B13EB907-0100-11DB-89CA-0019B92A3933+music.C61C0000-0200-11DB-89CA-0019B92A3933/lookup?
extras=Albums+TopTracks+ArtistDetails+Tracks+AlbumDetails
&accessToken=Bearer+[...] HTTP/1.1
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
        "Subgenres": [
          "Dance"
        ],
        "Albums": {
          "Items": [
            {
              "ReleaseDate": "2013-07-03T00:00:00Z",
              "Duration": "00:10:31",
              "TrackCount": 1,
              "IsExplicit": false,
              "LabelName": "Columbia",
              "Genres": [
                "Pop"
              ],
              "Subgenres": [
                "Contemporary Pop"
              ],
              "AlbumType": "Single",
              "Subtitle": "Daft Punk Remix",
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
              "Id": "music.E368C707-0100-11DB-89CA-0019B92A3933",
              "Name": "Get Lucky",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.E368C707-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Album/E368C707-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            },
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
              [...]
            }
          ],
          "ContinuationToken": "AYEDERwACQQBCAcCAQAAHMYAAtsRicoAGbkqOTMBAAIyNQ",
          "TotalItemCount": 37
        },
        "TopTracks": {
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
              "ReleaseDate": "2006-03-31T00:00:00Z",
              "Duration": "00:03:44",
              "TrackNumber": 8,
              "IsExplicit": false,
              "Genres": [
                "Electronic / Dance"
              ],
              "Subgenres": [
                "Dance"
              ],
              "Rights": [
                "Purchase",
                "Stream",
                "FreeStream"
              ],
              "Album": {
                "Id": "music.F2E82706-0100-11DB-89CA-0019B92A3933",
                "Name": "Musique",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.F2E82706-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
                "Link": "https://music.microsoft.com/Album/F2E82706-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
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
              "Id": "music.5BAF3206-0100-11DB-89CA-0019B92A3933",
              "Name": "Harder, Better, Faster, Stronger",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.5BAF3206-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Track/5BAF3206-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            },
            {
              [...]
            }
          ],
          "ContinuationToken": "AYEDERwACQQCAQcCAQAAHMYAAtsRicoAGbkqOTMBAAIyNQ",
          "TotalItemCount": 194
        },
        "Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",
        "Name": "Daft Punk",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "P   168791"
        },
        "Source": "Catalog"
      }
    ]
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
            }
          }
        ],
        "Tracks": {
          "Items": [
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
              "ReleaseDate": "2013-05-09T00:00:00Z",
              "Duration": "00:05:21",
              "TrackNumber": 2,
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
              "Id": "music.AB3EB907-0100-11DB-89CA-0019B92A3933",
              "Name": "The Game of Love",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.AB3EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Track/AB3EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "OtherIds": {
                "music.amg": "T 29381292"
              },
              "Source": "Catalog"
            },
            {
              [...]
            }
          ],
          "TotalItemCount": 13
        },
        "Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",
        "Name": "Random Access Memories",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "R  2749955"
        },
        "Source": "Catalog"
      }
    ]
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
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
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
      }
    ]
  }
}
```

## Lookup by ISRC
ISRC is a standard music identifier that can be used as input to the Lookup API by prefixing it with the namespace music.isrc.

### Request
```json
GET /1/content/music.isrc.GBDJQ8800006/lookup?accessToken=Bearer+[...]
```

### Response
```json
{
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "1988-11-21T00:00:00Z",
        "Duration": "00:11:54",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Rock"
        ],
        "Subgenres": [
          "Classic Rock"
        ],
        "Rights": [
          "Purchase",
          "Stream"
        ],
        "Album": {
          "Id": "music.51025806-0100-11DB-89CA-0019B92A3933",
          "Name": "Delicate Sound Of Thunder",
          "ImageUrl": "https://musicimage.xboxlive.com/content/music.51025806-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/51025806-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.D6670000-0200-11DB-89CA-0019B92A3933",
              "Name": "Pink Floyd",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.D6670000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/D6670000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.0EE73B06-0100-11DB-89CA-0019B92A3933",
        "Name": "Shine On You Crazy Diamond (Parts 1-5)",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.0EE73B06-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/0EE73B06-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "T  1530616",
          "music.isrc": "GBDJQ8800006"
        },
        "Source": "Catalog"
      }
    ]
  }
}
```

## Lookup by ICPN
ICPN is a standard music identifier that can be used as input to the Lookup API by prefixing it with the namespace music.icpn.

### Request
```http
GET /1/content/music.icpn.886443927087/lookup?accessToken=Bearer+[...]
```

### Response
```json
{
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T00:00:00Z",
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
          "music.amg": "R  2749955",
          "music.icpn": "886443927087"
        },
        "Source": "Catalog"
      }
    ]
  }
}
```

## Collection lookup examples
### Collection album lookup
#### Request
```http
GET /1/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/lookup?source=collection&accessToken=Bearer+[...]

Authorization: Bearer eyJlbmMiOiJBMTI4Q0JDK0hTMjU2IiwiYWxnIjoiUlNBLU9[...]
```

#### Response
```json
{
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-05-09T02:00:00+02:00",
        "Genres": [
          "Pop"
        ],
        "Id": "music.AQEPB7k-sQABsrFst-olnIY",
        "Name": "Random Access Memories",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  }
}
```

### Collection playlist lookup
#### Request
```http
GET /1/content/music.AQM2egu7ioD-AI-GF3usCeHQ/lookup?source=collection&accessToken=Bearer+[...]

Authorization: Bearer eyJlbmMiOiJBMTI4Q0JDK0hTMjU2IiwiYWxnIjoiUlNBLU9[...]
```

#### Response
```json
{
  "Playlists": {
    "Items": [
      {
        "TrackCount": 2,
        "UserIsOwner": true,
        "Tracks": {
          "Items": [
            {
              "ReleaseDate": "2013-05-09T02:00:00+02:00",
              "Duration": "00:06:07",
              "TrackNumber": 8,
              "IsExplicit": false,
              "Genres": [
                "Pop"
              ],
              "Rights": [
                "Purchase",
                "FreeStream"
              ],
              "Subtitle": "feat. Pharrell Williams",
              "Album": {
                "ReleaseDate": "2013-05-09T02:00:00+02:00",
                "Genres": [
                  "Pop"
                ],
                "Subtitle": "",
                "Id": "music.AQEDB7k-sQABAA",
                "Name": "Random Access Memories",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
                "Link": "https://music.microsoft.com/Album/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                "Source": "Collection"
              },
              "Artists": [
                {
                  "Role": "PrimaryArtist",
                  "Artist": {
                    "Id": "music.AQIDAAAcxgACAA",
                    "Name": "Daft Punk",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
                    "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                    "Source": "Collection"
                  }
                },
                {
                  "Role": "ContributingArtist",
                  "Artist": {
                    "Id": "music.AQIDAABnCAACAA",
                    "Name": "Pharrell Williams",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.08670000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
                    "Link": "https://music.microsoft.com/Artist/08670000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                    "Source": "Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.AQIDAAAcxgACAA",
                    "Name": "Daft Punk",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
                    "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                    "Source": "Collection"
                  }
                }
              ],
              "Id": "music.AQQfHgTT3DD6Vkyk1Tk-HDsRBQe5PqgAAQ",
              "Name": "Get Lucky (feat. Pharrell Williams)",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.a83eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Track/a83eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            },
            {
              "ReleaseDate": "2013-09-27T02:00:00+02:00",
              "Duration": "00:04:46",
              "TrackNumber": 7,
              "IsExplicit": false,
              "Genres": [
                "Electronic / Dance"
              ],
              "Subtitle": "",
              "Album": {
                "ReleaseDate": "2013-09-27T02:00:00+02:00",
                "Genres": [
                  "Electronic / Dance"
                ],
                "Subtitle": "",
                "Id": "music.AQEDB-rrJgABAA",
                "Name": "Aleph",
                "ImageUrl": "https://musicimage.xboxlive.com/content/music.26ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
                "Link": "https://music.microsoft.com/Album/26ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                "Source": "Collection"
              },
              "Artists": [
                {
                  "Role": "PrimaryArtist",
                  "Artist": {
                    "Id": "music.AQIDAAdbyQACAA",
                    "Name": "Gesaffelstein",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
                    "Link": "https://music.microsoft.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                    "Source": "Collection"
                  }
                },
                {
                  "Role": "AlbumArtist",
                  "Artist": {
                    "Id": "music.AQIDAAdbyQACAA",
                    "Name": "Gesaffelstein",
                    "ImageUrl": "https://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
                    "Link": "https://music.microsoft.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
                    "Source": "Collection"
                  }
                }
              ],
              "Id": "music.AQQf3-wXiuSFS0yqPmC-ZUazfgfq6y0AAQ",
              "Name": "Aleph",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.2debea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Track/2debea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          ]
        },
        "Id": "music.AQM2egu7ioD-AI-GF3usCeHQ",
        "Name": "Playlist1",
        "Link": "https://music.microsoft.com/Playlist/bb0b7a36-808a-00fe-8f86-177bac09e1d0?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  }
}
```

### Collection+Catalog batch lookup
Each of the input IDs is looked up in the collection first, and then in the catalog if not found in the collection. The "Source" field of each returned item indicates whether the item comes from the Collection or the Catalog.

#### Request
```http
GET /1/content/music.3770F306-0100-11DB-89CA-0019B92A3933+music.AQIPAAAcxgAC3GpkUPzr8EQ/lookup?source=collection+catalog
&accessToken=Bearer+[...] HTTP/1.1

Authorization: Bearer eyJlbmMiOiJBMTI4Q0JDK0hTMjU2IiwiYWxnIjoiUlNBLU9[...]
```

#### Response
```json
{
  "Artists": {
    "Items": [
      {
        "Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",
        "Name": "Daft Punk",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  },
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2011-09-20T00:00:00Z",
        "Duration": "00:03:26",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Electronic / Dance"
        ],
        "Subgenres": [
          "Dance"
        ],
        "Subtitle": "Radio Edit",
        "Album": {
          "Id": "music.3370F306-0100-11DB-89CA-0019B92A3933",
          "Name": "Trust You Again",
          "ImageUrl": "https://musicimage.xboxlive.com/content/music.3370F306-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/3370F306-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.2E860300-0200-11DB-89CA-0019B92A3933",
              "Name": "Muttonheads",
              "ImageUrl": "https://musicimage.xboxlive.com/content/music.2E860300-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/2E860300-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.3770F306-0100-11DB-89CA-0019B92A3933",
        "Name": "Trust You Again",
        "ImageUrl": "https://musicimage.xboxlive.com/content/music.3770F306-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/3770F306-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "T 23642758"
        },
        "Source": "Catalog"
      }
    ]
  }
}
```

#### Parent
[Groove Service REST Reference](overview.md)
