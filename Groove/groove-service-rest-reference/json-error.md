---
title: Error JSON object | Groove Services
description:  Learn about Error JSON object in Groove Music API.
keywords: groove music, groove api, groove error json
author: sakley
ms.assetid: 
---

# Error (JSON)
The error structure is the same across all APIs. Noteworthy elements are as follows.

## Error
The Error object has the following specification.

| **Member**  | **Type** | **Description**                                                     |
|-------------|----------|---------------------------------------------------------------------|
| ErrorCode   | String   | The error code, as described in the following table of error codes. |
| Description | String   | A description of the error code. This description is meant to be used by the application developer to understand the issue, but shouldn't be displayed as-is to the end user.                      |
| Message     | String   | A more contextual message describing what may have gone wrong.      |

These error structures can be optionally embedded in any Groove API service response. If an error is reported, the Error.ErrorCode and Error.Description elements will always be provided.

## Error codes
Error codes can be used to display custom error messages to the user.

|**Category**                     | **Name**                                        | **Default HTTP code**     | **Description** |
|---------------------------------|-------------------------------------------------|---------------------------|----------------------------------------------------------------------------------|
| Input validation                | MISSING\-INPUT\-PARAMETER                       | 400 Bad Request           | Missing or empty mandatory parameter.                                                                       |
| Input validation                | INVALID\-INPUT\-PARAMETER                       | 400 Bad Request           | Invalid parameter value.                                                                                    |
| Input validation                | INCOMPATIBLE\-INPUT\-PARAMETERS                 | 400 Bad Request           | Incompatible parameters.                                                                                    |
| Input validation                | INVALID\-COUNTRY                                | 400 Bad Request           | The requested functionality is not available in this region                                                 |
| Input validation                | CONTINUATION\-TOKEN\-INVALID\-ERROR             | 400 Bad Request           | The continuation token provided is incorrect.                                                               |
| Input validation                | UNAUTHORIZED\-INPUT\-PARAMETER                  | 200 OK                    | Unauthorized input parameter                                                                                |
| Input validation                | UNAUTHORIZED\-API\-METHOD                       | 403 Forbidden             | Unauthorized API method                                                                                     |
| Authentication                  | ACCESS\-TOKEN\-MISSING                          | 401 Unauthorized          | Azure Marketplace access token required.                                                                    |
| Authentication                  | ACCESS\-TOKEN\-INVALID                          | 401 Unauthorized          | Invalid Azure Marketplace token.                                                                            |
| Authentication                  | ACCESS\-TOKEN\-EXPIRED                          | 401 Unauthorized          | Expired Azure Marketplace token.                                                                            |
| Authentication                  | ACCESS\-TOKEN\-INVALID\-SUBSCRIPTION            | 401 Unauthorized          | Azure Marketplace client ID is not a subscriber to the Groove data offer.                                   |
| Authentication                  | ACCESS\-TOKEN\-VALIDATION\-ERROR                | 500 Internal Server Error | Unexpected error while validating Azure Marketplace token.                                                  |
| Authentication                  | ACCESS\-TOKEN\-SUBSCRIPTION\-VALIDATION\-ERROR  | 500 Internal Server Error | Unexpected error while validating Azure Marketplace subscription status.                                    |
| Authentication                  | INVALID\-AUTHORIZATION\-HEADER                  | 401 Unauthorized          | Missing or invalid authorization header                                                                     |
| Authentication                  | AUTHORIZATION\-TOKEN\-EXPIRED                   | 401 Unauthorized          | User's authorization token expired. You need to obtain a new one.                                           |
| Authentication                  | MSA\-SCOPE\-REQUIRES\-USER\-CONSENT             | 401 Unauthorized          | User hasn't accepted the necessary Microsoft account scopes. Force the user to sign-in again.               |
| Authentication                  | NO\-MUSIC\-PASS\-SUBSCRIPTION                   | 403 Forbidden             | The user does not have a Groove Music subscription                                                          |
| Catalog errors                  | CATALOG\-INVALID\-DATA                          | 200 OK                    | Error while reading catalog data; some results may be missing.                                              |
| Catalog errors                  | CATALOG\-NO\-RESULT                             | 404 Not Found             | Item does not exist.                                                                                        |
| Catalog errors                  | CATALOG\-UNAVAILABLE                            | 502 Bad Gateway           | No response from catalog.                                                                                   |
| Collection errors               | COLLECTION\-INVALID\-DATA                       | 200 OK                    | Error while reading collection data, some results may be missing or incomplete                              |
| Collection errors               | COLLECTION\-SOME\-OPERATIONS\-FAILED            | 200 OK                    | Some of the operations failed                                                                               |
| Collection errors               | COLLECTION\-INVALID\-PLAYLIST\-REORDER          | 400 Bad Request           | Invalid playlist reorder operation                                                                          |
| Collection errors               | COLLECTION\-FULL                                | 400 BadRequest            | User's collection is full                                                                                   |
| Collection errors               | COLLECTION\-PLAYLIST\-FULL                      | 400 BadRequest            | This playlist is full                                                                                       |
| Collection errors               | COLLECTION\-INVALID\-OPERATION                  | 400 BadRequest            | This operation is not supported                                                                             |
| Collection errors               | COLLECTION\-INVALID\-ID                         | 400 BadRequest            | Invalid collection id for this operation                                                                    |
| Collection errors               | COLLECTION\-INVALID\-PLAYLIST\-INFO             | 400 BadRequest            | Required playlist information is missing                                                                    |
| Collection errors               | COLLECTION\-NO\-RESULT                          | 404 NotFound              | No result in the user's collection                                                                          |
| Collection errors               | COLLECTION\-CONCURRENT\-UPDATE                  | 409 Conflict              | Concurrent update of the collection.                                                                        |
| Collection errors               | COLLECTION\-INVALID\-RESPONSE                   | 502 BadGateway            | Invalid response from the user's collection                                                                 |
| Collection errors               | COLLECTION\-OPERATION\-UNKNOWN\-ERROR           | 502 BadGateway            | The operation failed                                                                                        |
| Discovery errors                | DISCOVERY\-INVALID\-DATA                        | 200 OK                    | Error while reading new releases or spotlight data, some results may be missing or incomplete               |
| Discovery errors                | DISCOVERY\-NO\-RESULT                           | 404 NotFound              | No result from Discovery (New Releases and Spotlight)                                                       |
| Discovery errors                | DISCOVERY\-INVALID\-GENRE                       | 404 NotFound              | No result from Discovery (New Releases and Spotlight), you might want to check if genre is well formatted   |
| Discovery errors                | DISCOVERY\-INVALID\-RESPONSE                    | 502 BadGateway            | Invalid response from Discovery (New Releases and Spotlight)                                                |
| Streaming errors                | DELIVERY\-3RD\-PARTY\-CANNOT\-STREAM\-PURCHASES | 403 Forbidden             | Purchases are not available for streaming through the Groove Developer APIs.                                |
| Streaming errors                | DELIVERY\-UNAVAILABLE\-CONTENT                  | 404 NotFound              | Content is not available for streaming                                                                      |
| Streaming errors                | DELIVERY\-ERROR                                 | 404 NotFound              | Unknown error when trying to stream content                                                                 |
| Streaming errors                | DELIVERY\-CONCURRENT\-STREAMING                 | 409 Conflict              | The user is already streaming on another device                                                             |
| Streaming errors                | DELIVERY\-INVALID\-RESPONSE                     | 502 BadGateway            | Invalid response when trying to stream content                                                              |
| Subscription errors             | SUBSCRIPTION\-INVALID\-RESPONSE                 | 502 BadGateway            | Invalid response when trying to get user's subscription                                                     |
| Server errors                   | TOO\-MANY\-REQUESTS                             | 429 TooManyRequests       | Too Many Requests                                                                                           |
| Server errors                   | INTERNAL\-SERVER\-ERROR                         | 500 Internal Server Error | Oops, something went seriously wrong.                                                                       |

## Sample JSON syntax
```json
{
   "ErrorCode": "CATALOG-NO-RESULT",
   "Description": "Item does not exist"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
