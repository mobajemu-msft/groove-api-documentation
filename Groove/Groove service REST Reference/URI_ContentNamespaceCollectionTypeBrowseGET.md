# GET (/1/content/{namespace}/collection/{type}/browse) 

Browse a user's collection or playlists.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [Query string parameters](#query-string-parameters)
-   [Examples](#examples)

##Remarks


The full browse request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
/1/content/{namespace}/collection/{type}/browse?orderBy={orderBy}&maxItems={maxItems} 
&page={page}&continuationToken={continuationToken}&accessToken={accessToken}&jsonp={jsonp}
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

| Note                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| You must provide a valid [user authentication](../Using the Groove RESTful Services/User Authentication.md) token for that user in the authorization header. |

##Response object


[ContentResponse (JSON)](JSON_ContentResponse.md)

##Query string parameters

The following parameters are not available on the Common Parameters page.

| **Parameter** | **Type**              | **Description**                                                                                                        |
|---------------|-----------------------|------------------------------------------------------------------------------------------------------------------------|
| type          | string                | Required. The type of item to browse. The following values are supported: "albums", "artists", "playlists", "tracks".  |
| orderBy       | string                | Optional. Ordering chosen for that content (**orderBy** field). If incompatible, an HTTP 400 error will be emitted.    |
| maxItems      | 32-bit signed integer | Optional. The number of items to browse per page. The default value is 25, and it's the maximum value allowed as well. |
| page          | 32-bit signed integer | Optional. The page to browse (will skip **page**\***maxItems** items). The first (and default) page is page 0.         |

##Examples


###Browse artists


#### Request
```http
GET /1/content/music/collection/artists/browse?orderBy=ArtistName
&accessToken=Bearer+[...]

Authorization: XBL3.0 x=1852535598;eyJlbmMiOiJB[...]
```
      
####Response
```json
{
  "Artists": {
    "Items": [
      {
        "Id": "music.AQIPAATsXwACH-HZ7I1TxZk",
        "Name": "Boris Brejcha",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
      {
        "Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",
        "Name": "Daft Punk",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
      {
        "Id": "music.AQIPAAdbyQACHfwgGCrXS_0",
        "Name": "Gesaffelstein",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  }
}
```
###Browse artists with invalid orderBy
####Request
```http
GET /1/content/music/collection/artists/browse?orderBy=AlbumTitle&accessToken=
Bearer+[...]

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```
      
####Response
```json
400 BadRequest 

{
  "Error": {
    "ErrorCode": "INCOMPATIBLE_INPUT_PARAMETERS",
    "Description": "Incompatible parameters",
    "Message": "Invalid ordering for this content"
  }
}
```

###Browse albums
####Request
```http
GET /1/content/music/collection/albums/browse?orderBy=AlbumTitle&accessToken=
Bearer+[...] 

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```
      
####Response
```json
{
  "Albums": {
    "Items": [
      {
        "ReleaseDate": "2013-09-27T02:00:00+02:00",
        "TrackCount": 1,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Artists": [
          {
            "Role": "AlbumArtist",
            "Artist": {
              "Id": "music.AQIPAAdbyQACHfwgGCrXS_0",
              "Name": "Gesaffelstein",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          }
        ],
        "Id": "music.AQEPB-rrJgABM-vDUQcGa74",
        "Name": "Aleph",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.26ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/26ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
      {
        "ReleaseDate": "2013-06-07T02:00:00+02:00",
        "TrackCount": 1,
        "IsExplicit": false,
        "Genres": [
          "Electronic / Dance"
        ],
        "Artists": [
          {
            "Role": "AlbumArtist",
            "Artist": {
              "Id": "music.AQIPAATsXwACH-HZ7I1TxZk",
              "Name": "Boris Brejcha",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          }
        ],
        "Id": "music.AQEPB75BmAABHDnC5GmB7_s",
        "Name": "Der Alchemyst",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.9841be07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/9841be07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
      {
        "ReleaseDate": "2013-05-09T02:00:00+02:00",
        "TrackCount": 1,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Artists": [
          {
            "Role": "AlbumArtist",
            "Artist": {
              "Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",
              "Name": "Daft Punk",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          }
        ],
        "Id": "music.AQEPB7k-sQABsrFst-olnIY",
        "Name": "Random Access Memories",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Album/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  }
}
```      

###Browse playlists
This request specifies maxItems=1 and uses the continuation token to get the second one afterwards.
####Request
```http
GET /1/content/music/collection/playlists/browse?maxItems=1&
accessToken=Bearer+[...]

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```
     
####Response
```json
{
  "Playlists": {
    "Items": [
      {
        "TrackCount": 2,
        "UserIsOwner": true,
        "Id": "music.AQMhT-EZaoD-AHqGpBl9GuHQ",
        "Name": "Playlist1",
        "Link": "https://music.microsoft.com/Playlist/19e14f21-806a-00fe-7a86-a4197d1ae1d0?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ],
    "ContinuationToken": "ASQ6p3IBCQQADQcDAgABMQ"
  }
}
```
####Continuation Request
```http
GET /1/content/music/collection/playlists/browse?continuationToken=ASQ6p3IBCQQADQcDAgABMQ
&accessToken=Bearer+[...]

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```
      
####Continuation Response
```json
{
  "Playlists": {
    "Items": [
      {
        "TrackCount": 0,
        "UserIsOwner": true,
        "Id": "music.AQOMEscya4D-AHofn2p9GuHQ",
        "Name": "EmptyPlaylist",
        "Link": "https://music.microsoft.com/Playlist/32c7128c-806b-00fe-7a1f-9f6a7d1ae1d0?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  }
}
```
      
###Browse tracks
####Request
```http
GET /1/content/music/collection/tracks/browse?orderBy=TrackTitle&accessToken=
Bearer+[...]

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```     

####Response
```json
{
  "Tracks": {
    "Items": [
      {
        "ReleaseDate": "2013-06-07T02:00:00+02:00",
        "Duration": "00:08:51",
        "TrackNumber": 1,
        "IsExplicit": false,
        "Genres": [
          "Electronic / Dance"
        ],
        "Album": {
          "ReleaseDate": "2013-06-07T02:00:00+02:00",
          "Genres": [
            "Electronic / Dance"
          ],
          "Id": "music.AQEPB75BmAABHDnC5GmB7_s",
          "Name": "Der Alchemyst",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.9841be07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/9841be07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
          "Source": "Collection"
        },
        "Artists": [
          {
            "Role": "PrimaryArtist",
            "Artist": {
              "Id": "music.AQIPAATsXwACH-HZ7I1TxZk",
              "Name": "Boris Brejcha",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          },
          {
            "Role": "AlbumArtist",
            "Artist": {
              "Id": "music.AQIPAATsXwACH-HZ7I1TxZk",
              "Name": "Boris Brejcha",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          }
        ],
        "Id": "music.AQQfmed5A3bItEOZE7BO8k2nxQe-QZkAAQ",
        "Name": "Der Alchemyst",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.9941be07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/9941be07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
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
        "Album": {
          "ReleaseDate": "2013-05-09T02:00:00+02:00",
          "Genres": [
            "Pop"
          ],
          "Id": "music.AQEPB7k-sQABsrFst-olnIY",
          "Name": "Random Access Memories",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
          "Source": "Collection"
        },
        "Artists": [
          {
            "Role": "PrimaryArtist",
            "Artist": {
              "Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",
              "Name": "Daft Punk",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          },
          {
            "Role": "ContributingArtist",
            "Artist": {
              "Id": "music.AQIPAABnCAACp2B24PJn-q4",
              "Name": "Pharrell Williams",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.08670000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/08670000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          },
          {
            "Role": "AlbumArtist",
            "Artist": {
              "Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",
              "Name": "Daft Punk",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          }
        ],
        "Id": "music.AQQfFbq8mTyjiEem8FCgKBVfbQe5PqgAAQ",
        "Name": "Get Lucky (feat. Pharrell Williams)",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.a83eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/a83eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      },
      {
        "ReleaseDate": "2013-09-27T02:00:00+02:00",
        "Duration": "00:04:07",
        "TrackNumber": 2,
        "IsExplicit": false,
        "Genres": [
          "Pop"
        ],
        "Album": {
          "ReleaseDate": "2013-09-27T02:00:00+02:00",
          "Genres": [
            "Pop"
          ],
          "Id": "music.AQEPB-rrJgABM-vDUQcGa74",
          "Name": "Aleph",
          "ImageUrl": "http://musicimage.xboxlive.com/content/music.26ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
          "Link": "https://music.microsoft.com/Album/26ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
          "Source": "Collection"
        },
        "Artists": [
          {
            "Role": "PrimaryArtist",
            "Artist": {
              "Id": "music.AQIPAAdbyQACHfwgGCrXS_0",
              "Name": "Gesaffelstein",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          },
          {
            "Role": "AlbumArtist",
            "Artist": {
              "Id": "music.AQIPAAdbyQACHfwgGCrXS_0",
              "Name": "Gesaffelstein",
              "ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",
              "Link": "https://music.microsoft.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
              "Source": "Collection"
            }
          }
        ],
        "Id": "music.AQQfF79vCNAqFku67NfthZPYEQfq6ycAAQ",
        "Name": "Pursuit",
        "ImageUrl": "http://musicimage.xboxlive.com/content/music.27ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",
        "Link": "https://music.microsoft.com/Track/27ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",
        "Source": "Collection"
      }
    ]
  }
}
```
      
###Browse tracks with invalid maxItems
####Request
```http
GET /1/content/music/collection/tracks/browse?maxItems=42&accessToken=Bearer+[...]

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```      
####Response
```json
400 BadRequest 

{
  "Error": {
    "ErrorCode": "INVALID_INPUT_PARAMETER",
    "Description": "Invalid parameter value",
    "Message": "Parameter maxItems must have a value of at most 25"
  }
}
```

###See also


#### Parent
