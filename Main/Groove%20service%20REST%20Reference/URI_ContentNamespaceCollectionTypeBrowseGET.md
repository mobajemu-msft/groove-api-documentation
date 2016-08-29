|                                                       |
|-------------------------------------------------------|
| GET (/1/content/{namespace}/collection/{type}/browse) |
| [See Also](#seeAlsoToggle)                            |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Browse a user's collection or playlists.

-   [Remarks](#remarks)

-   [Response object](#response-object)

-   [Query string parameters](#query-string-parameters)

-   [Examples](#examples)

Remarks
=======

The full browse request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

/1/content/{namespace}/collection/{type}/browse?orderBy={orderBy}&maxItems={maxItems} &page={page}&continuationToken={continuationToken}&accessToken={accessToken}&jsonp={jsonp}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

| **Note **                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| You must provide a valid [user authentication](http://msdn.microsoft.com/en-us/library/dn768189.aspx%20) token for that user in the authorization header. |

Response object
===============

[ContentResponse (JSON)](../Endpointdocumentation/JSON_ContentResponse.htm)

Query string parameters
=======================

The following parameters are not available on the Common Parameters page.

| **Parameter** | **Type**              | **Description**                                                                                                        |
|---------------|-----------------------|------------------------------------------------------------------------------------------------------------------------|
| type          | string                | Required. The type of item to browse. The following values are supported: "albums", "artists", "playlists", "tracks".  |
| orderBy       | string                | Optional. Ordering chosen for that content (**orderBy** field). If incompatible, an HTTP 400 error will be emitted.    |
| maxItems      | 32-bit signed integer | Optional. The number of items to browse per page. The default value is 25, and it's the maximum value allowed as well. |
| page          | 32-bit signed integer | Optional. The page to browse (will skip **page**\***maxItems** items). The first (and default) page is page 0.         |

Examples
========

Browse artists
--------------

#### Request

GET /1/content/music/collection/artists/browse?orderBy=ArtistName

&accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05

%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252f

schemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252f

music.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252f

datamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4

%253d HTTP/1.1

Authorization: XBL3.0 x=1852535598;eyJlbmMiOiJB\[...\]

#### Response

{

"Artists": {

"Items": \[

{

"Id": "music.AQIPAATsXwACH-HZ7I1TxZk",

"Name": "Boris Brejcha",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"Id": "music.AQIPAAdbyQACHfwgGCrXS\_0",

"Name": "Gesaffelstein",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

\]

}

}

Browse artists with invalid orderBy
-----------------------------------

#### Request

GET /1/content/music/collection/artists/browse?orderBy=AlbumTitle&accessToken=

Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity

%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com

%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f

%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com

%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

#### Response

400 BadRequest

{

"Error": {

"ErrorCode": "INCOMPATIBLE\_INPUT\_PARAMETERS",

"Description": "Incompatible parameters",

"Message": "Invalid ordering for this content"

}

}

Browse albums
-------------

#### Request

GET /1/content/music/collection/albums/browse?orderBy=AlbumTitle&accessToken=

Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity

%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com

%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps

%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f

%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f

%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3

%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

#### Response

{

"Albums": {

"Items": \[

{

"ReleaseDate": "2013-09-27T02:00:00+02:00",

"TrackCount": 1,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Artists": \[

{

"Role": "AlbumArtist",

"Artist": {

"Id": "music.AQIPAAdbyQACHfwgGCrXS\_0",

"Name": "Gesaffelstein",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

}

\],

"Id": "music.AQEPB-rrJgABM-vDUQcGa74",

"Name": "Aleph",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.26ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/26ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"ReleaseDate": "2013-06-07T02:00:00+02:00",

"TrackCount": 1,

"IsExplicit": false,

"Genres": \[

"Electronic / Dance"

\],

"Artists": \[

{

"Role": "AlbumArtist",

"Artist": {

"Id": "music.AQIPAATsXwACH-HZ7I1TxZk",

"Name": "Boris Brejcha",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

}

\],

"Id": "music.AQEPB75BmAABHDnC5GmB7\_s",

"Name": "Der Alchemyst",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.9841be07-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/9841be07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"ReleaseDate": "2013-05-09T02:00:00+02:00",

"TrackCount": 1,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Artists": \[

{

"Role": "AlbumArtist",

"Artist": {

"Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

}

\],

"Id": "music.AQEPB7k-sQABsrFst-olnIY",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

\]

}

}

Browse playlists
----------------

This request specifies maxItems=1 and uses the continuation token to get the second one afterwards.

#### Request

GET /1/content/music/collection/playlists/browse?maxItems=1&

accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252f

identity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com

%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f

%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com

%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

#### Response

{

"Playlists": {

"Items": \[

{

"TrackCount": 2,

"UserIsOwner": true,

"Id": "music.AQMhT-EZaoD-AHqGpBl9GuHQ",

"Name": "Playlist1",

"Link": "http://music.xbox.com/Playlist/19e14f21-806a-00fe-7a86-a4197d1ae1d0?partnerID=AwesomePartner",

"Source": "Collection"

}

\],

"ContinuationToken": "ASQ6p3IBCQQADQcDAgABMQ"

}

}

#### Continuation Request

GET /1/content/music/collection/playlists/browse?continuationToken=ASQ6p3IBCQQADQcDAgABMQ

&accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05

%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252f

schemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f

%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252f

datamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTz

SEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

#### Continuation Response

{

"Playlists": {

"Items": \[

{

"TrackCount": 0,

"UserIsOwner": true,

"Id": "music.AQOMEscya4D-AHofn2p9GuHQ",

"Name": "EmptyPlaylist",

"Link": "http://music.xbox.com/Playlist/32c7128c-806b-00fe-7a1f-9f6a7d1ae1d0?partnerID=AwesomePartner",

"Source": "Collection"

}

\]

}

}

Browse tracks
-------------

#### Request

GET /1/content/music/collection/tracks/browse?orderBy=TrackTitle&accessToken=

Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity

%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com

%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a

%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com

%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

#### Response

{

"Tracks": {

"Items": \[

{

"ReleaseDate": "2013-06-07T02:00:00+02:00",

"Duration": "00:08:51",

"TrackNumber": 1,

"IsExplicit": false,

"Genres": \[

"Electronic / Dance"

\],

"Album": {

"ReleaseDate": "2013-06-07T02:00:00+02:00",

"Genres": \[

"Electronic / Dance"

\],

"Id": "music.AQEPB75BmAABHDnC5GmB7\_s",

"Name": "Der Alchemyst",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.9841be07-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/9841be07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

"Artists": \[

{

"Role": "PrimaryArtist",

"Artist": {

"Id": "music.AQIPAATsXwACH-HZ7I1TxZk",

"Name": "Boris Brejcha",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

},

{

"Role": "AlbumArtist",

"Artist": {

"Id": "music.AQIPAATsXwACH-HZ7I1TxZk",

"Name": "Boris Brejcha",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.5fec0400-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/5fec0400-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

}

\],

"Id": "music.AQQfmed5A3bItEOZE7BO8k2nxQe-QZkAAQ",

"Name": "Der Alchemyst",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.9941be07-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/9941be07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"ReleaseDate": "2013-05-09T02:00:00+02:00",

"Duration": "00:06:07",

"TrackNumber": 8,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Rights": \[

"Purchase",

"FreeStream"

\],

"Album": {

"ReleaseDate": "2013-05-09T02:00:00+02:00",

"Genres": \[

"Pop"

\],

"Id": "music.AQEPB7k-sQABsrFst-olnIY",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.b13eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/b13eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

"Artists": \[

{

"Role": "PrimaryArtist",

"Artist": {

"Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

},

{

"Role": "ContributingArtist",

"Artist": {

"Id": "music.AQIPAABnCAACp2B24PJn-q4",

"Name": "Pharrell Williams",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.08670000-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/08670000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

},

{

"Role": "AlbumArtist",

"Artist": {

"Id": "music.AQIPAAAcxgAC3GpkUPzr8EQ",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

}

\],

"Id": "music.AQQfFbq8mTyjiEem8FCgKBVfbQe5PqgAAQ",

"Name": "Get Lucky (feat. Pharrell Williams)",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.a83eb907-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/a83eb907-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"ReleaseDate": "2013-09-27T02:00:00+02:00",

"Duration": "00:04:07",

"TrackNumber": 2,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Album": {

"ReleaseDate": "2013-09-27T02:00:00+02:00",

"Genres": \[

"Pop"

\],

"Id": "music.AQEPB-rrJgABM-vDUQcGa74",

"Name": "Aleph",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.26ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/26ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

"Artists": \[

{

"Role": "PrimaryArtist",

"Artist": {

"Id": "music.AQIPAAdbyQACHfwgGCrXS\_0",

"Name": "Gesaffelstein",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

},

{

"Role": "AlbumArtist",

"Artist": {

"Id": "music.AQIPAAdbyQACHfwgGCrXS\_0",

"Name": "Gesaffelstein",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c95b0700-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c95b0700-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

}

\],

"Id": "music.AQQfF79vCNAqFku67NfthZPYEQfq6ycAAQ",

"Name": "Pursuit",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.27ebea07-0100-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/27ebea07-0100-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

}

\]

}

}

Browse tracks with invalid maxItems
-----------------------------------

#### Request

GET /1/content/music/collection/tracks/browse?maxItems=42&accessToken=Bearer+http%253a%252f%252f

schemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner

%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims

%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp

%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f

%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3

%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

#### Response

400 BadRequest

{

"Error": {

"ErrorCode": "INVALID\_INPUT\_PARAMETER",

"Description": "Invalid parameter value",

"Message": "Parameter maxItems must have a value of at most 25"

}

}

See also
========

#### Parent

[/1/content/{namespace}/collection/{type}/browse](../Endpointdocumentation/URI_ContentNamespaceCollectionTypeBrowse.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
