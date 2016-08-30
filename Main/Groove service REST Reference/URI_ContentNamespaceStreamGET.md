# GET (/1/content/{id}/stream)
Request streaming.

-   [Remarks](#remarks)
-   [Query string parameters](#query-string-parameters)
-   [Response object](#response-object)
-   [Examples](#examples)

##Remarks


| Important                                                                        |
|------------------------------------------------------------------------------------------|
| [User authentication](../Using the Groove RESTful Services/User Authentication.md) is mandatory for this API. |

The full streaming request is composed of mandatory and optional URL parts and query parameters. A streaming request containing all parameters would resemble the following string:

/1/content/{id}/stream?clientInstanceId={clientInstanceId} &contentType={contentType}&accessToken={accessToken}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](CommonParameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

Please make sure your usage of the streaming API follows the [guidelines](guidelines.md).

For playing streams from your application on windows versions prior to Windows 10, you can use the [Microsoft HLS SDK](http://github.com/MicrosoftDX/MicrosoftHLSSDK).

##Query string parameters


| **Parameter**    | **Type** | **Description**                                                                                             |
|------------------|----------|-------------------------------------------------------------------------------------------------------------|
| clientInstanceId | string   | Required. Unique client identifier. Should be persisted client-side. Can be from 32 to 128 characters long. |

##Response object


[StreamResponse (JSON)](JSON_StreamResponse.md)

##Examples


###Unauthorized stream

Only Groove Pass subscribers may play full streams.

#### Request
```
GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/stream
?clientInstanceId=5b559245-96ed-4cf2-a4de-e0a13d66609c&accessToken=Bearer
+http%253a%252f%252fschemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity
%252fclaims%252fnameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com
%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f
%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com
%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26HMACSHA256%3dLagMcZR0PUeZGILbC0yREl40VqDBiJg1QE43joplt18%253d HTTP/1.1 

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```
#### Response
```
403 Forbidden 

{
  "Error": {
    "ErrorCode": "NO_MUSIC_PASS_SUBSCRIPTION",
    "Description": "The user does not have an Groove subscription"
  }
}
```

###Authorized stream


The user authentication token identifies a user who has a Music Pass.

#### Request
```
GET /1/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/stream?clientInstanceId=
5b559245-96ed-4cf2-a4de-e0a13d66609c&accessToken=Bearer+http%253a%252f%252fschemas.
xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier%3dAwesomePartner
%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice%252f2010%252f07%252fclaims
%252fidentityprovider%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience
%3dhttp%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a
%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256%3dLagMcZR0PUeZGILbC0yREl40VqDBiJ
g1QE43joplt18%253d HTTP/1.1 

Authorization: XBL3.0 x=218686063;eyJlbmMiOiJB[...]
```
#### Response
```
{
  "Url": "https://webstream-vh.akamaihd.net/i/129/580/712/155/audio.mp4/master.m3u8?
rid=40117aff-3edc-432a-a81d-1967a61e826d_i2_fr-FR_music_asset_location&hdnea=exp=1398443951~
acl=/i/129/580/712/155/audio.mp4*~hmac=22d99f90d60f28e9c12e618027dc611f973c9ba614ad04c7210570d807e6398c",
  "ContentType": "application/vnd.apple.mpegurl",
  "ExpiresOn": "2014-04-25T16:39:11.132Z"
}
```
##See also


#### Parent
