#GET (/1/content/{namespace}/catalog/genres) 

Get a list of genres available for a locale.

-   [Remarks](#remarks)

-   [Response object](#response-object)

-   [Examples](#examples)

##Remarks


The BrowseGenres request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:

/1/content/{namespace}/catalog/genres?language={language}&country={country}&accessToken={accessToken}

For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](Common Parameters.md). For a table of error codes, see [Error (JSON)](JSON_Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](HTTPStatusCodes.md).

##Response object


[ContentResponse (JSON)](JSON_ContentResponse.md)

##Examples

###Browse genres


#### Request
```
GET /1/content/music/catalog/genres?accessToken=Bearer+http%253a%252f%252f
schemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252f
nameidentifier%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com
%252faccesscontrolservice%252f2010%252f07%252fclaims%252fidentityprovider%3d
https%253a%252f%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp
%253a%252f%252fmusic.xboxlive.com%252f%26ExpiresOn%3d1609459199%26Issuer
%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net%26HMACSHA256
%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1
```
#### Response
```   
{
"Genres": \[  
"Blues / Folk",  
"Christian / Gospel",
"Classical",
"Comedy / Spoken Word",
"Country",
"Electronic / Dance",
"Hip Hop",
"Jazz",
"Kids",
"Latin",
"Pop",
"R&B / Soul",
"Reggae / Dancehall",
"Rock",
"Soundtracks",
"World",
"More"
\],
"Culture": "en-US"
}
```
####Browse genres for a specific locale


#### Request
```
GET /1/content/music/catalog/genres?country=tr&language=tr&accessToken=Bearer+http%253a%252f%252f
schemas.xmlsoap.org%252fws%252f2005%252f05%252fidentity%252fclaims%252fnameidentifier
%3dAwesomePartner%26http%253a%252f%252fschemas.microsoft.com%252faccesscontrolservice
%252f2010%252f07%252fclaims%252fidentityprovider%3dhttps%253a%252f
%252fdatamarket.accesscontrol.windows.net%26Audience%3dhttp%253a%252f%252fmusic.xboxlive.com
%252f%26ExpiresOn%3d1609459199%26Issuer%3dhttps%253a%252f%252fdatamarket.accesscontrol.windows.net
%26HMACSHA256%3d0pVJ3%252fUig7mgeMtlM2wI27SmQItFOQXTzSEbEmmDFG4%253d HTTP/1.1
```
#### Response
```
{
"Genres": \[
"Alternatif",
"Caz",
"Elektronik / Dans",
"Film müzikleri",
"Hip Hop / Soul",
"Klasik",
"Pop",
"Rock",
"Daha fazla müzik türü"
\],
"Culture": "tr-TR"
}
``` 
##See also
