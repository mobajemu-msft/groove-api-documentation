# GET (/1/content/{namespace}/catalog/{type}/browse)
Browse the music catalog.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [Query string parameters](#query-string-parameters)
-   [Examples](#examples)

## Remarks
The Browse Catalog request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

```
/1/content/{namespace}/catalog/{type}/browse?orderBy={orderBy}&genre={genre}&maxItems={maxItems}&page={page}
&continuationToken={continuationToken}&country={country}&language={language}&accessToken={accessToken}
&contentType={contentType}&jsonp={jsonp}
```

| Note                                                                                                                     |
|------------------------------------------------------------------------------------------------------------------------------|
| Pagination is zero-based (the first page is found at page 0), and catalog browse will not return more than 1000 total items. |

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

## Response object
[ContentResponse (JSON)](JSON_ContentResponse.md)

## Query string parameters
The following parameters are not available on the Common Parameters page.

| **Parameter**     | **Type**              | **Description**                                                                                                                                                                                                                                                 |
|-------------------|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| namespace         | string                | The [namespace](Namespace.md) to browse.                                                                                                                                                                                              |
| type              | string                | Required. The type of item to browse. The following values are supported: "albums", "artists", "tracks".                                                                                                                                                        |
| orderBy           | string                | *Optional*. Ordering chosen for that content (**orderBy** field). If incompatible, an HTTP 400 error will be emitted.                                                                                                                                             |
| genre             | string                | *Optional*. Genre name; filters browsing to return only items in a specific genre of content. Possible values can be obtained using the [browse genres API](URI_ContentNamespaceCatalogGenresGET.md), and must be properly URL-encoded. |
| maxItems          | 32-bit signed integer | *Optional*. The number of items to browse per page. The default value is 25, and it's the maximum value allowed as well.                                                                                                                                          |
| page              | 32-bit signed integer | *Optional*. The page to browse (will skip **page**\***maxItems** items). The first (and default) page is page 0.                                                                                                                                                  |
| continuationToken | string                | A [continuation token](JSON_PaginatedList.md) provided in an earlier service response and optionally passed back to the service to request the continuation of an incomplete list of content.                                         |
| extra             | string                | Required. The type of the requested sub-elements (for example, "Tracks" or "Albums"). See [Extras](Extras.md).                                                                                                                        |

## Examples
### Browse the most popular catalog artists in your region
#### Request
```http
GET /1/content/music/catalog/artists/browse?orderBy=MostPopular&accessToken=Bearer+[...]
```      

#### Response
```json
{
  "Artists": {
    "Items": [
      {
        "Genres": [
          "R&B / Soul"
        ],
        "Subgenres": [
          "R&B"
        ],
        "Id": "music.E6950200-0200-11DB-89CA-0019B92A3933",
        "Name": "Trey Songz",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.E6950200-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/E6950200-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "P   686292"
        },
        "Source": "Catalog"
      },
      {
        "Genres": [
          "Hip Hop"
        ],
        "Subgenres": [
          "Contemporary Hip Hop"
        ],
        "Id": "music.1F154700-0200-11DB-89CA-0019B92A3933",
        "Name": "Iggy Azalea",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.1F154700-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/1F154700-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "OtherIds": {
          "music.amg": "P  2703496"
        },
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AZYULjMZCQQADwcDAQACMjU",
    "TotalItemCount": 200
  }
}
```

### Browse the 5 most played albums in your region
#### Request
```http
GET /1/content/music/catalog/albums/browse?orderBy=AllTimePlayCount&maxItems=5&accessToken=Bearer
+[...]
```

#### Response
```json
{
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2014-06-19T00:00:00Z",
        "Duration": "01:13:20",
        "TrackCount": 17,
        "IsExplicit": true,
        "LabelName": "Atlantic Records",
        "Genres": [
          "R&B / Soul"
        ],
        "Subgenres": [
          "R&B"
        ],
        "AlbumType": "Album",
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.E6950200-0200-11DB-89CA-0019B92A3933",
              "Name": "Trey Songz",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.E6950200-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/E6950200-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.73CC6408-0100-11DB-89CA-0019B92A3933",
        "Name": "Trigga (Deluxe)",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.73CC6408-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/73CC6408-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2014-04-09T00:00:00Z",
        "Duration": "00:51:19",
        "TrackCount": 15,
        "IsExplicit": true,
        "LabelName": "Island Records",
        "Genres": [
          "Hip Hop"
        ],
        "Subgenres": [
          "Contemporary Hip Hop"
        ],
        "AlbumType": "Album",
        "Subtitle": "Deluxe Version",
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.1F154700-0200-11DB-89CA-0019B92A3933",
              "Name": "Iggy Azalea",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.1F154700-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/1F154700-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.5C314608-0100-11DB-89CA-0019B92A3933",
        "Name": "The New Classic",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.5C314608-0100-11DB-89CA-0019B92A3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/5C314608-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AUDg68QFCQQAAQcDAQABNQ",
    "TotalItemCount": 200
  }
}
```

### Browse the 50 most played tracks in France
#### Request
```http
GET /1/content/music/catalog/tracks/browse?orderBy=AllTimePlayCount&country=FR&accessToken=Bearer+[...]
```

#### Response
```json
{
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2014-03-25T00:00:00Z",
        "Duration": "00:04:12",
        "TrackNumber": 19,
        "IsExplicit": false,
        "Genres": [
          "Hip Hop / Rap"
        ],
        "Subgenres": [
          "Hip Hop US & Intl."
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Album": {
          "Id": "music.9D9D3D08-0100-11DB-89CA-0019B92A3933",
          "Name": "Les yeux plus gros que le monde",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.9D9D3D08-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
          "Link": "https://music.microsoft.com/Album/9D9D3D08-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.359D2700-0200-11DB-89CA-0019B92A3933",
              "Name": "Black M",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.359D2700-0200-11DB-89CA-0019B92A3933/image?locale=fr-FR",
              "Link": "https://music.microsoft.com/Artist/359D2700-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.B09D3D08-0100-11DB-89CA-0019B92A3933",
        "Name": "Sur ma route",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.B09D3D08-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
        "Link": "https://music.microsoft.com/Track/B09D3D08-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2014-01-22T00:00:00Z",
        "Duration": "00:03:33",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Chanson Française"
        ],
        "Subgenres": [
          "Pop Française"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Album": {
          "Id": "music.97A21B08-0100-11DB-89CA-0019B92A3933",
          "Name": "Mini World",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.97A21B08-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
          "Link": "https://music.microsoft.com/Album/97A21B08-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.F3FC2A00-0200-11DB-89CA-0019B92A3933",
              "Name": "Indila",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.F3FC2A00-0200-11DB-89CA-0019B92A3933/image?locale=fr-FR",
              "Link": "https://music.microsoft.com/Artist/F3FC2A00-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.98A21B08-0100-11DB-89CA-0019B92A3933",
        "Name": "Dernière Danse",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.98A21B08-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
        "Link": "https://music.microsoft.com/Track/98A21B08-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AShFeFoZDAQAAQcDAQACMjU",
    "TotalItemCount": 1000
  }
}
```

#### Continuation Request (using "page=1", but it could also have used the ContinuationToken from the first response instead)
```http
GET /1/content/music/catalog/tracks/browse?orderBy=AllTimePlayCount&country=FR&page=1&accessToken=Bearer+[...]
```

#### Response
```json
{
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2014-06-10T00:00:00Z",
        "Duration": "00:04:45",
        "TrackNumber": 23,
        "IsExplicit": false,
        "Genres": [
          "Alternative"
        ],
        "Subgenres": [
          "Pop Alternative"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Album": {
          "Id": "music.FE5A6008-0100-11DB-89CA-0019B92A3933",
          "Name": "NRJ Summer Hits Only 2014",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.FE5A6008-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
          "Link": "https://music.microsoft.com/Album/FE5A6008-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.0A190000-0200-11DB-89CA-0019B92A3933",
              "Name": "Coldplay",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.0A190000-0200-11DB-89CA-0019B92A3933/image?locale=fr-FR",
              "Link": "https://music.microsoft.com/Artist/0A190000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.1A5B6008-0100-11DB-89CA-0019B92A3933",
        "Name": "Magic",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.1A5B6008-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
        "Link": "https://music.microsoft.com/Track/1A5B6008-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "Source": "Catalog"
      },
      {
        "ReleaseDate": "2014-04-02T00:00:00Z",
        "Duration": "00:03:42",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Subgenres": [
          "Pop Contemporaine"
        ],
        "Rights": [
          "Purchase",
          "Stream",
          "FreeStream"
        ],
        "Album": {
          "Id": "music.1D474208-0100-11DB-89CA-0019B92A3933",
          "Name": "We Are One (Ole Ola) [The Official 2014 FIFA World Cup Song]",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.1D474208-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
          "Link": "https://music.microsoft.com/Album/1D474208-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
          "Source": "Catalog"
        },
        "Artists": [
          {
            "Role": "Main",
            "Artist": {
              "Id": "music.F48A0400-0200-11DB-89CA-0019B92A3933",
              "Name": "Pitbull",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.F48A0400-0200-11DB-89CA-0019B92A3933/image?locale=fr-FR",
              "Link": "https://music.microsoft.com/Artist/F48A0400-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
              "Source": "Catalog"
            }
          }
        ],
        "Id": "music.1E474208-0100-11DB-89CA-0019B92A3933",
        "Name": "We Are One (Ole Ola) [The Official 2014 FIFA World Cup Song]",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.1E474208-0100-11DB-89CA-0019B92A3933/image?locale=fr-FR",
        "Link": "https://music.microsoft.com/Track/1E474208-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
        "Source": "Catalog"
      },
      {
        [...]
      }
    ],
    "ContinuationToken": "AShFeFoZDAQAAQcDAQACNTA",
    "TotalItemCount": 1000
  }
}
```

#### Parent
[Groove Service REST Reference](Groove-Service-REST-Reference.md)
