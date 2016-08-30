#GET (/1/user/{namespace}/profile) 

Retrieve a user's profile or the features available in a given region.

-   [Remarks](#remarks)
-   [Examples](#examples)

##Remarks


The full request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```http
/1/user/{namespace}/profile?
language={language}&country={country}&accessToken={accessToken}&contentType={contentType}&jsonp={jsonp}
```

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

| Important                                                                        |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using the Groove RESTful Services/User Authentication.md) is mandatory for this API. |

##Examples

### User doesn't have a Groove Pass


#### Request
```http
GET /1/user/music/profile?accessToken=Bearer+[...]

Authorization: XBL3.0 x=847278487;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw[...] 
```
###Response
```json
{
  "HasSubscription": false,
  "IsSubscriptionAvailableForPurchase": true,
  "Culture": "en-US",
  "Collection": {
    "Token": "3.0.0.0.7.7.7",
    "PlaylistCount": 2,
    "RemainingPlaylistCount": 98,
    "TrackCount": 3,
    "RemainingTrackCount": 49997
  }
}
```
###Check Groove Pass availability in France
#### Request
```http
GET /1/user/music/profile?country=fr&accessToken=Bearer+[...]
```
#### Response
```json
{
  "IsSubscriptionAvailableForPurchase": true,
  "Culture": "fr-FR"
}
```
###Check if your region is supported by Groove


#### Request
```http
GET /1/user/music/profile?accessToken=Bearer+[...]
```
#### Response
```json
{
   "IsSubscriptionAvailableForPurchase": true,
   "Culture": "en-US"
}
```
###See also


#### Parent
