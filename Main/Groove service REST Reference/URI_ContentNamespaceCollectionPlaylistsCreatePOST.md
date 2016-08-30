# POST (/1/content/{namespace}/collection/playlists/create) 

Create a playlist on behalf of a user.

-   [Remarks](#remarks)
-   [Examples](#examples)

##Remarks


The full create request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

```
/1/content/{namespace}/collection/playlists/create?accessToken={accessToken}
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

| Important                                                                        |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using the Groove RESTful Services/User Authentication.md) is mandatory for this API. |

In case of partial failure (when some of the tracks aren't added), the API will return an HTTP 200 error and you will need to parse the results to see which actions failed and why.

The number of tracks per batch is limited to 100. Playlist names are restricted to 256 characters and cannot be empty.

##Examples


Request object: [PlaylistAction (JSON)](JSON_PlaylistAction.md).

Response object: [PlaylistActionResponse (JSON)](JSON_PlaylistActionResponse.md).

###Create a playlist without tracks


You can use this API to create a playlist with only its metadata. For this, you must provide at least a name for the playlist. The API will then return the ID of the newly-created playlist.

#### Request
```
POST /1/content/music/collection/playlists/create?accessToken=Bearer+http%253a%252f%252f
schemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier
%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice
%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.
accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f
%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1 

Authorization: XBL3.0 x=1291659333;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Ii[...] 

Content-Type: application/json 

{
  "Name": "Groove is awesome",
  "IsPublished": false
}
```
      
####Response
```
{
  "PlaylistActionResult": {
    "Id": "music.playlist.72d0fb33-8027-00fe-746f-abe4d8374ad1",
    "Name": "Groove is awesome",
    "IsPublished": false
  }
}
```
      
###Create a playlist with tracks
You can also use this API to create a playlist and directly add tracks to it, with track IDs received from other Platform calls. In order to match your request to the API's response, the response contains InputId fields that are exactly the track IDs you provided. Along with this field, if the add operation was successful, the API also returns the new ID of that track in the playlist.

####Request
```
POST /1/content/music/collection/playlists/create?accessToken=Bearer+http%253a%252f%252f
schemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier
%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice
%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.
windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer
%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI
27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1 

Authorization: XBL3.0 x=1291659333;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Ii[...] 

Content-Type: application/json 

{
  "Name": "Groove APIs rock!",
  "IsPublished": false,
  "TrackActions": [
    {
      "Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
      "Action": "Add"
    },
    {
      "Id": "music.9941BE07-0100-11DB-89CA-0019B92A3933",
      "Action": "Add"
    }
  ]
}
```
      
####Response
```
{
  "PlaylistActionResult": {
    "Id": "music.playlist.d7e2d6b8-8028-00fe-a58d-423bda374ad1",
    "Name": "Groove APIs rock!",
    "IsPublished": false,
    "TrackActionResults": [
      {
        "InputId": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
        "Id": "music.AQQf4QwRv9XTc0enTqGcoGW-Dwe5PqgAAQ"
      },
      {
        "InputId": "music.9941BE07-0100-11DB-89CA-0019B92A3933",
        "Id": "music.AQQfjw6CZhj_6Ua4uRjTbuDD0we-QZkAAQ"
      }
    ]
  }
}
```
      
###Create a playlist with some invalid tracks
As with other edit APIs, when some sub-operations fail, you will receive an HTTP 200 error with failure details for each sub-operation. Here we'll create a playlist adding a valid track and an invalid one with a randomly-generated ID.

####Request
```
POST /1/content/music/collection/playlists/create?accessToken=Bearer+
http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity
%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252f
schemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims
%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199
%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256
%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1 

Authorization: XBL3.0 x=1291659333;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Ii[...] 

Content-Type: application/json 

{
  "Name": "Please take my money!",
  "IsPublished": false,
  "TrackActions": [
    {
      "Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
      "Action": "Add"
    },
    {
      "Id": "music.9F41BE07-357E-23A5-7B54-0019B92A3933",
      "Action": "Add"
    }
  ]
}
```
      
####Response
```
{
  "PlaylistActionResult": {
    "Id": "music.playlist.f5d71c61-8029-00fe-acee-09c6db374ad1",
    "Name": "Please take my money!",
    "IsPublished": false,
    "TrackActionResults": [
      {
        "InputId": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
        "Id": "music.AQQfzeBk5subH0uw8YDu5URcvAe5PqgAAQ"
      },
      {
        "InputId": "music.9F41BE07-357E-23A5-7B54-0019B92A3933",
        "Error": {
          "ErrorCode": "COLLECTION_INVALID_ID",
          "Description": "Invalid collection id for this operation",
          "Message": "Collection ErrorCode=ArgumentInvalid, Details=ContentId"
        }
      }
    ]
  },
  "Error": {
    "ErrorCode": "COLLECTION_SOME_OPERATIONS_FAILED",
    "Description": "Some of the operations failed"
  }
}
```
###See also


#### Parent
