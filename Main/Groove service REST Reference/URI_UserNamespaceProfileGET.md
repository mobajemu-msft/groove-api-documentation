#GET (/1/user/{namespace}/profile) 

Retrieve a user's profile or the features available in a given region.

-   [Remarks](#remarks)

-   [Examples](#examples)

##Remarks


The full request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
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
```
GET /1/user/music/profile?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org
%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner
%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07
%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer
%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256
%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1 

Authorization: XBL3.0 x=847278487;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw[...] ```
#### Response
```
GET (/1/user/{namespace}/profile)
Retrieve a user's profile or the features available in a given region. 
Remarks
Examples
Remarks
The full request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
/1/user/{namespace}/profile?language={language}&country={country}&accessToken={accessToken}&contentType={contentType}&jsonp={jsonp}
For parameters common to every Groove RESTful API, see Parameters common to every Groove RESTful API. For a table of error codes, see Error (JSON). For HTTP status codes, see Groove RESTful API HTTP Status Codes.
Note 
Accessing a user's profile requires user authentication.
Examples
User doesn't have a Groove Pass
Request
GET /1/user/music/profile?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org
%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner
%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07
%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer
%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256
%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1 

Authorization: XBL3.0 x=847278487;eyJlbmMiOiJBMTI4Q0JDK0hTMjU2Iiw[...] 
      
Response
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
```
GET /1/user/music/profile?country=fr&accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org%
252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a
%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider
%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f
%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f
%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3
%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1
```
#### Response
```
{
  "IsSubscriptionAvailableForPurchase": true,
  "Culture": "fr-FR"
}
```
###Check if your region is supported by Groove


#### Request
```
GET /1/user/music/profile?accessToken=Bearer+http%253a%252f%252fschemas.xmlsoap.org
%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner
%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07
%252fclaims%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer
%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3d0pVJ3
%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1
```
#### Response
```
{
   "IsSubscriptionAvailableForPurchase": true,
   "Culture": "en-US"
}
```
###See also


#### Parent
