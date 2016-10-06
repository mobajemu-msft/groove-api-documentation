#POST (/1/content/{namespace}/collection/add) 

Add tracks to a user's collection.

-   [Remarks](#remarks)
-   [URI parameters](#uri-parameters)
-   [Examples](#examples)

##Remarks


| Important                                                                            |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using-the-Groove-RESTful-Services/User-Authentication.md) is mandatory for this API. |

Provide a batch of IDs and the API will try to add them to the user's collection. In case of partial failure (when some of the tracks aren't added), the API will return an HTTP 200 error and you will need to parse the results to see which actions failed and why.

The number of tracks per batch is limited to 100.

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

##URI parameters


| **Parameter** | **Type** | **Description**                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| namespace     | string   | Required. The namespace to browse (Namespace).                                                                                                     |
| accessToken   | string   | A valid developer authentication Access Token obtained from Azure Data Market, used to identify the 3rd party application using the Platform APIs. |

##Examples


Request object: [TrackActionRequest (JSON)](JSON_TrackActionRequest.md).

Response object: [TrackActionResponse (JSON)](JSON_TrackActionResponse.md).

###Add tracks to collection

We will add one valid track ID, and one invalid ID (random-generated).

#### Request
```http
POST /1/content/music/collection/add?accessToken=Bearer+[...]

Authorization: XBL3.0 x=945039495;eyJlbmMiOiJB\[...\]

Content-Type: application/json
{
  "TrackIds": [
    "music.9bb2c5c5-455c-4c15-827c-f9bfd759a458",
    "music.A83EB907-0100-11DB-89CA-0019B92A3933"
  ]
}
```
#### Response
```json
{
  "TrackActionResults": [
    {
      "InputId": "music.9BB2C5C5-455C-4C15-827C-F9BFD759A458",
      "Error": {
        "ErrorCode": "COLLECTION_INVALID_ID",
        "Description": "Invalid collection id for this operation",
        "Message": "Collection ErrorCode=ArgumentInvalid, Details=ContentId"
      }
    },
    {
      "InputId": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
      "Id": "music.AQQfZ78ml185KUqtiDc9dx6i6Ae5PqgAAQ"
    }
  ],
  "Error": {
    "ErrorCode": "COLLECTION_SOME_OPERATIONS_FAILED",
    "Description": "Some of the operations failed"
  }
}
```

###Add too many tracks at once

The batch size is limited to 100 items.

#### Request
```http
POST /1/content/music/collection/add?accessToken=Bearer+[...]

Authorization: XBL3.0 x=663179813;eyJlbmMiOiJB\[...\]

Content-Type: application/json

{
"TrackIds": \[
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933",
"music.A83EB907-0100-11DB-89CA-0019B92A3933"
\]

}
```

#### Response
```json
400 BadRequest

{
  "Error": {
    "ErrorCode": "COLLECTION_INVALID_OPERATION",
    "Description": "This operation is not supported",
    "Message": "Number of tracks for this operation is limited to 100"
  }
}
```

### Add a track using XML instead of JSON


#### Request
```http
POST /1/content/music/collection/add?accessToken=Bearer+[...]

Authorization: XBL3.0 x=663179813;eyJlbmMiOiJB[...]

Content-Type: application/xml

&lt;TrackActionRequest xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/xboxmusic/2013/10/platform"&gt;
  &lt;TrackIds xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays"&gt;
    &lt;d2p1:string&gt;music.873FB507-0100-11DB-89CA-0019B92A3933&lt;/d2p1:string&gt;
  &lt;/TrackIds&gt;
&lt;/TrackActionRequest&gt;
```

#### Response
```xml
&lt;TrackActionResponse xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/xboxmusic/2013/10/platform"&gt;
  &lt;TrackActionResults&gt;
    &lt;TrackActionResult&gt;
      &lt;Id&gt;music.AQQfuiqlXWaDzk-j0Ht9qB6EWwe1P4cAAQ&lt;/Id&gt;
      &lt;InputId&gt;music.873FB507-0100-11DB-89CA-0019B92A3933&lt;/InputId&gt;
    &lt;/TrackActionResult&gt;
  &lt;/TrackActionResults&gt;
&lt;/TrackActionResponse&gt;
```
###Access is denied if the user authentication token is missing or invalid


The batch size is limited to 100 items.

#### Request
```http
POST /1/content/music/collection/add?accessToken=Bearer+[...] 

Content-Type: application/json 

{
  "TrackIds": [
    "music.A83EB907-0100-11DB-89CA-0019B92A3933"
  ]
}
```

#### Response
```json
401 Unauthorized

{
  "Error": {
    "ErrorCode": "INVALID_AUTHORIZATION_HEADER",
    "Description": "Missing or invalid authorization header",
    "Message": "You need user authentication to use this API"
  }
}
```
###See also


#### Parent
[Groove Service REST Reference](Groove-Service-REST-Reference.md)