# POST (/1/content/{namespace}/collection/delete) 

Delete tracks from a user's collection.

-   [Remarks](#remarks)

-   [Response object](#response-object)

-   [URI parameters](#uri-parameters)

-   [Examples](#examples)

##Remarks


| **Important **                                                                           |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using the Groove RESTful services/User Authentication.md) is mandatory for this API. |

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

##Response object


[TrackActionResponse (JSON)](JSON_TrackActionResponse.md)

##URI parameters


The Delete Tracks request is composed of mandatory URL parts and query parameters, described in the table below. A Delete Tracks request containing all parameters would look like the following string:

```
/1/content/{namespace}/collection/delete?accessToken={accessToken}
```

| **Parameter** | **Type** | **Description**                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| namespace     | string   | Required. The [namespace to browse] (Namespace.md).                                                                                                     |
| accessToken   | string   | A valid developer authentication Access Token obtained from Azure Data Market, used to identify the 3rd party application using the Platform APIs. |

A valid user authentication token is also required in the Authorization header to access the user's collection.

##Examples


Request object: [TrackActionRequest (JSON)](JSON_TrackActionRequest.md).

Response object: [TrackActionResponse (JSON)](JSON_TrackActionResponse.md).

###Delete tracks from collection


In this example we delete a valid track (which is in the user's collection), and an invalid one (randomly-generated ID).

#### Request
```
POST /1/content/music/collection/delete?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org
%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26
http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims
%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience
%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a
%252f%252fdatamarket.accesscontrol.windows.net
%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB\[...\]

Content-Type: application/json

{
  "TrackIds": [
    "music.9bb2c5c5-455c-4c15-827c-f9bfd759a458",
    "music.AQQfjl2zcVUd602kG1MvCy4e_Ae-QZkAAQ"
  ]
}
```

#### Response
```
{
  "TrackActionResults": [
    {
      "InputId": "music.9BB2C5C5-455C-4C15-827C-F9BFD759A458",
      "Error": {
        "ErrorCode": "COLLECTION_INVALID_ID",
        "Description": "Invalid collection id for this operation"
      }
    },
    {
      "InputId": "music.AQQfjl2zcVUd602kG1MvCy4e_Ae-QZkAAQ"
    }
  ],
  "Error": {
    "ErrorCode": "COLLECTION_SOME_OPERATIONS_FAILED",
    "Description": "Some of the operations failed"
  }
}
```
###See also


#### Parent
