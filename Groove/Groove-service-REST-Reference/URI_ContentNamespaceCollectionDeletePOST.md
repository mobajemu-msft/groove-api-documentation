# POST (/1/content/{namespace}/collection/delete)
Delete tracks from a user's collection.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [URI parameters](#uri-parameters)
-   [Examples](#examples)

## Remarks
| Important                                                                            |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using-the-Groove-RESTful-services/User-Authentication.md) is mandatory for this API. |

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

## Response object
[TrackActionResponse (JSON)](JSON-TrackActionResponse.md)

## URI parameters
The Delete Tracks request is composed of mandatory URL parts and query parameters, described in the table below. A Delete Tracks request containing all parameters would look like the following string:

```
/1/content/{namespace}/collection/delete?accessToken={accessToken}
```

| **Parameter** | **Type** | **Description**                                                                                                                                    |
|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| namespace     | string   | Required. The namespace to browse (music for example).                                                                                                     |
| accessToken   | string   | A valid developer authentication Access Token obtained from Azure Data Market, used to identify the 3rd party application using the Groove APIs. |

A valid user authentication token is also required in the Authorization header to access the user's collection.

## Examples
Request object: [TrackActionRequest (JSON)](JSON-TrackActionRequest.md).

Response object: [TrackActionResponse (JSON)](JSON-TrackActionResponse.md).

### Delete tracks from collection
In this example we delete a valid track (which is in the user's collection), and an invalid one (randomly-generated ID).

#### Request
```http
POST /1/content/music/collection/delete?accessToken=Bearer+[...]

Authorization: Bearer eyJlbmMiOiJB[...]

Content-Type: application/json

{
  "TrackIds": [
    "music.9bb2c5c5-455c-4c15-827c-f9bfd759a458",
    "music.AQQfjl2zcVUd602kG1MvCy4e-Ae-QZkAAQ"
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
        "ErrorCode": "COLLECTION-INVALID-ID",
        "Description": "Invalid collection id for this operation"
      }
    },
    {
      "InputId": "music.AQQfjl2zcVUd602kG1MvCy4e-Ae-QZkAAQ"
    }
  ],
  "Error": {
    "ErrorCode": "COLLECTION-SOME-OPERATIONS-FAILED",
    "Description": "Some of the operations failed"
  }
}
```

#### Parent
[Groove Service REST Reference](overview.md)
