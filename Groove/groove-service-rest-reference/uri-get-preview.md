# GET (/1/content/{id}/preview)
Request preview streaming.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [Query string parameters](#query-string-parameters)
-   [Examples](#examples)

## Remarks
The preview streaming request is composed of mandatory and optional URL parts and query parameters. A preview request containing all parameters would resemble the following string:
```http
/1/content/{namespace.id}/preview?country={country}&clientInstanceId={clientInstanceId} &contentType={contentType}&accessToken={accessToken}
```

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

## Response object
[StreamResponse (JSON)](JSON-StreamResponse.md)

## Query string parameters
| **Parameter**    | **Type** | **Description**                                                                                             |
|------------------|----------|-------------------------------------------------------------------------------------------------------------|
| clientInstanceId | string   | Required. Unique client identifier. Should be persisted client-side. Can be from 32 to 128 characters long. |

## Examples
### Preview example
#### Request
```http
GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/preview?clientInstanceId=fa624b17-412c-454a-a5a5-950bb06ae019&
accessToken=Bearer+[...]
```

#### Response
```json
{
  "Url": "http://progdownload.zune.net/129/580/712/170/audio.mp3?rid=052d12ef-2084-45c4-9f02-c552ef834463-i2-en-US-music-asset-location",
  "ContentType": "audio/mp3"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
