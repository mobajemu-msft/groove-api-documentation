|                                               |
|-----------------------------------------------|
| GET (/1/content/{namespace}/search?q={query}) |
| [See Also](#seeAlsoToggle)                    |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Search for items in a media catalog, user's collection, or both.

-   [Remarks](#remarks)

-   [URI parameters](#uri-parameters)

-   [Response object](#response-object)

-   [Query string parameters](#query-string-parameters)

-   [Examples](#examples)

Remarks
=======

A Search request is composed of mandatory and optional URL parts and query parameters, as described in the following table. A Search request containing all parameters would look like the following string:

/1/content/{namespace}/search?q={query}&language={language}&country={country}&maxItems={maxItems}&filters={filters}&source={source}&contentType={contentType}&continuationToken={continuationToken}&accessToken={accessToken}&jsonp={jsonp}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](../Endpointdocumentation/CommonParameters.htm). For a table of error codes, see [Error (JSON)](../Endpointdocumentation/JSON_Error.htm). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](../Endpointdocumentation/HTTPStatusCodes.htm).

| **Note **                                                                                               |
|---------------------------------------------------------------------------------------------------------|
| Using the **collection** source requires [user authentication](../Endpointdocumentation/user_auth.htm). |

URI parameters
==============

| **Parameter** | **Type** | **Description**                                                           |
|---------------|----------|---------------------------------------------------------------------------|
| namespace     | string   | Required. The namespace in which to perform the search. Example: "music". |

Response object
===============

[ContentResponse (JSON)](../Endpointdocumentation/JSON_ContentResponse.htm)

Query string parameters
=======================

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|---------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| query         | string   | Required unless a **continuationToken** is passed. The search query. Any special characters in the query should be properly URL-encoded (for example, multiple words should be separated by "+").                                                                                                                                                                                                                                                                                                                                                               |
| maxItems      | uint     | Optional. Positive integer from 1 to 25, inclusive. The maximum number of results that should be returned in the response. If this parameter is not set, the response will be limited to a maximum of 25 results per item type. There is no guarantee that all search results will be returned in a single response; the response may contain a truncated list of responses and a continuation token.                                                                                                                                                           |
| filters       | string   | Optional. A subcategory of item types, in case the client is interested in only one or more specific types of items. Multiple categories may be passed in this parameter by separating them with "+". Possible values for the "music" namespace are "artists", "albums", and "tracks". If this parameter is not provided, the search will be performed in all categories (for the "music" namespace, for example, the default value of the parameter is "artists+albums+tracks").                                                                               |
| source        | string   | Optional. One or more data source(s), in case the client is interested in searching data from specific sources. Multiple sources may be passed in this parameter by separating them with "+". Possible values for the "music" namespace are "catalog", "collection", and "collection+catalog". The use of the "collection" source requires passing a valid user authentication token. If this parameter is not provided, the search will be performed in the "catalog" if no user authentication token is provided and "collection+catalog" if one is provided. |

Examples
========

Simple search
-------------

#### Request

GET /1/content/music/search?q=daft+punk&accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org

%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner

%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07

%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience

%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256

%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

#### Response

{

"Artists": {

"Items": \[

{

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 168791"

},

"Source": "Catalog"

},

{

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Id": "music.5C780000-0200-11DB-89CA-0019B92A3933",

"Name": "Stardust",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.5C780000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/5C780000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 361992"

},

"Source": "Catalog"

},

{

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"Id": "music.8F130500-0200-11DB-89CA-0019B92A3933",

"Name": "Busy P",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.8F130500-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/8F130500-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 912342"

},

"Source": "Catalog"

}

\],

"TotalItemCount": 3

},

"Albums": {

"Items": \[

{

"ReleaseDate": "2013-05-09T00:00:00Z",

"Duration": "01:14:24",

"TrackCount": 13,

"IsExplicit": false,

"LabelName": "Columbia",

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"AlbumType": "Album",

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "R 2749955"

},

"Source": "Catalog"

},

{

"ReleaseDate": "2001-01-01T00:00:00Z",

"Duration": "01:01:09",

"TrackCount": 14,

"IsExplicit": false,

"LabelName": "Parlophone France",

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"AlbumType": "Album",

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.3E362806-0100-11DB-89CA-0019B92A3933",

"Name": "Discovery",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.3E362806-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/3E362806-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "R 522606"

},

"Source": "Catalog"

},

{

\[...\]

}

\],

"ContinuationToken": "AYdrKUUZCQQBAAcACWRhZnQgcHVuawEAAjI1",

"TotalItemCount": 54

},

"Tracks": {

"Items": \[

{

"ReleaseDate": "2013-05-09T00:00:00Z",

"Duration": "00:06:09",

"TrackNumber": 8,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Rights": \[

"Purchase",

"Stream",

"FreeStream"

\],

"Subtitle": "feat. Pharrell Williams",

"Album": {

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

},

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Get Lucky",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/A83EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

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

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Rights": \[

"Purchase",

"Stream",

"FreeStream"

\],

"Album": {

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

},

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.AA3EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Give Life Back to Music",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.AA3EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/AA3EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "T 29381293"

},

"Source": "Catalog"

},

{

\[...\]

}

\],

"ContinuationToken": "AYdrKUUZCQQIAAcACWRhZnQgcHVuawEAAjI1",

"TotalItemCount": 288

}

}

Searching for only albums and tracks
------------------------------------

#### Request

GET /1/content/music/search?q=daft+punk**&filters=Albums+tracks**

&accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005

%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26http

%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07

%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net

%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199

%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3

%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

#### Response

{

"Albums": {

"Items": \[

{

"ReleaseDate": "2013-05-09T00:00:00Z",

"Duration": "01:14:24",

"TrackCount": 13,

"IsExplicit": false,

"LabelName": "Columbia",

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"AlbumType": "Album",

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "R 2749955"

},

"Source": "Catalog"

},

{

"ReleaseDate": "2001-01-01T00:00:00Z",

"Duration": "01:01:09",

"TrackCount": 14,

"IsExplicit": false,

"LabelName": "Parlophone France",

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"AlbumType": "Album",

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.3E362806-0100-11DB-89CA-0019B92A3933",

"Name": "Discovery",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.3E362806-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/3E362806-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "R 522606"

},

"Source": "Catalog"

},

{

\[...\]

}

\],

"ContinuationToken": "AYdrKUUZCQQBAAYACWRhZnQgcHVuawEAAjI1",

"TotalItemCount": 54

},

"Tracks": {

"Items": \[

{

"ReleaseDate": "2013-05-09T00:00:00Z",

"Duration": "00:06:09",

"TrackNumber": 8,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Rights": \[

"Purchase",

"Stream",

"FreeStream"

\],

"Subtitle": "feat. Pharrell Williams",

"Album": {

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

},

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Get Lucky",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/A83EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

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

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Rights": \[

"Purchase",

"Stream",

"FreeStream"

\],

"Album": {

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

},

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.AA3EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Give Life Back to Music",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.AA3EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/AA3EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "T 29381293"

},

"Source": "Catalog"

},

{

\[...\]

}

\],

"ContinuationToken": "AYdrKUUZCQQIAAYACWRhZnQgcHVuawEAAjI1",

"TotalItemCount": 288

}

}

Searching in both the Collection and the Catalog
------------------------------------------------

The response for a Collection+Catalog search will contain for each item type (artists, albums, tracks) up to 25 (or maxItems if specified to a lower value) results per source. Collection items are returned before Catalog items, and if a continuation token is present for an incomplete list it is common to both sources if they have remaining items (which means the continuation response may also contain up to 25 Collection and 25 Catalog items). In this particular example, our user's collection is quite small and the only Collection result is one artist, followed by up to 10 Catalog artists, albums and tracks. Using one of the response continuation token would then produce only Catalog results because all Collection results are included in the first response.

#### Request

GET /1/content/music/search?q=daft+punk&**source=collection+catalog**&maxItems=10&accessToken=Bearer+

http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3d

AwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07

%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience

%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer

%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256

%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=1047956662;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2IiwiYWxnIjoiUlNBLU9\[...\]

#### Response

{

"Artists": {

"Items": \[

{

"Id": "music.AQILAAAcxgAC3GpkUPzr8EQ",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.c61c0000-0200-11db-89ca-0019b92a3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/c61c0000-0200-11db-89ca-0019b92a3933?partnerID=AwesomePartner",

"Source": "Collection"

},

{

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 168791"

},

"Source": "Catalog"

},

{

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Id": "music.5C780000-0200-11DB-89CA-0019B92A3933",

"Name": "Stardust",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.5C780000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/5C780000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 361992"

},

"Source": "Catalog"

},

{

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"Id": "music.8F130500-0200-11DB-89CA-0019B92A3933",

"Name": "Busy P",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.8F130500-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/8F130500-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 912342"

},

"Source": "Catalog"

}

\],

"TotalItemCount": 4

},

"Albums": {

"Items": \[

{

"ReleaseDate": "2013-05-09T00:00:00Z",

"Duration": "01:14:24",

"TrackCount": 13,

"IsExplicit": false,

"LabelName": "Columbia",

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"AlbumType": "Album",

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "R 2749955"

},

"Source": "Catalog"

},

{

"ReleaseDate": "2001-01-01T00:00:00Z",

"Duration": "01:01:09",

"TrackCount": 14,

"IsExplicit": false,

"LabelName": "Parlophone France",

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"AlbumType": "Album",

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.3E362806-0100-11DB-89CA-0019B92A3933",

"Name": "Discovery",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.3E362806-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/3E362806-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "R 522606"

},

"Source": "Catalog"

},

{

\[...\]

}

\],

"ContinuationToken": "AYdrKUUKCQQBAAcACWRhZnQgcHVuawEAAjEw",

"TotalItemCount": 54

},

"Tracks": {

"Items": \[

{

"ReleaseDate": "2013-05-09T00:00:00Z",

"Duration": "00:06:09",

"TrackNumber": 8,

"IsExplicit": false,

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Rights": \[

"Purchase",

"Stream",

"FreeStream"

\],

"Subtitle": "feat. Pharrell Williams",

"Album": {

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

},

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Get Lucky",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/A83EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

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

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Contemporary Pop"

\],

"Rights": \[

"Purchase",

"Stream",

"FreeStream"

\],

"Album": {

"Id": "music.B13EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Random Access Memories",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.B13EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Album/B13EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

},

"Artists": \[

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

\],

"Id": "music.AA3EB907-0100-11DB-89CA-0019B92A3933",

"Name": "Give Life Back to Music",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.AA3EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Track/AA3EB907-0100-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "T 29381293"

},

"Source": "Catalog"

},

{

\[...\]

}

\],

"ContinuationToken": "AYdrKUUKCQQIAAcACWRhZnQgcHVuawEAAjEw",

"TotalItemCount": 288

}

}

See also
========

#### Parent

[/1/content/{namespace}/search?q={query}](../Endpointdocumentation/URI_ContentSearch.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
