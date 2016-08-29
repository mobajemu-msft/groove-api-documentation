|                            |
|----------------------------|
| StreamResponse (JSON)      |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

Response to all stream APIs. <span id="ID4EN" class="anchor"></span>

StreamResponse
==============

The StreamResponse object has the following specification.

| **Member**  | **Type**                                         | **Description**                                                                           |
|-------------|--------------------------------------------------|-------------------------------------------------------------------------------------------|
| Error       | [Error](../Endpointdocumentation/JSON_Error.htm) | Error returned.                                                                           |
| Url         | string                                           | The URL of the stream.                                                                    |
| ContentType | string                                           | The stream's content type. Can be one of the following:                                   
                                                                                                                                                             
                                                                  -   "application/vnd.apple.mpegurl": HLS MPEG-TS AAC 128-kbit stream with AES encryption.  
                                                                                                                                                             
                                                                  -   "audio/mpeg": MP3 HTTP progressive download.                                           |
| ExpiresOn   | DateTime                                         | GMT expiry time of the stream URL.                                                        |

Sample JSON syntax
==================

{

"Url": "https://webstream-vh.akamaihd.net/i/129/580/712/155/audio.mp4/

master.m3u8?rid=b56194dd-1720-4984-a9e8-0666cb717a5d-i2-fr-FR-music-asset-location&

hdnea=exp=1405687092~acl=/i/129/580/712/155/audio.mp4\*~

hmac=4fd5bc2e422b8cb152cc40169f9f4a883c6cda372236f6a12e3985061bcdfa31",

"ContentType": "application/vnd.apple.mpegurl",

"ExpiresOn": "2014-07-18T12:38:12.349Z"

}

See also
========

#### Parent

[Groove Service REST Reference](../Endpointdocumentation/atoc_xbm_reference.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
