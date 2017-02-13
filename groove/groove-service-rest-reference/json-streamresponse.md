---
title: StreamResponse JSON object | Groove Services
description:  Learn about StreamResponse JSON object in Groove Music API.
keywords: groove music, groove api, groove streamresponse json
author: sakley
ms.assetid: 7980017b-453e-45a5-9b77-f69ced8685f7
---

# StreamResponse (JSON)    
Response to all stream APIs.

## StreamResponse
The StreamResponse object has the following specification.

| **Member**  | **Type**                                         | **Description**                                                                           |
|-------------|--------------------------------------------------|-------------------------------------------------------------------------------------------|
| Error       | [Error](JSON-Error.md) | Error returned.                                                                           |
| Url         | string                                           | The URL of the stream.                                                                    |
| ContentType | string                                           | The stream's content type. Can be one of the following: **(1)** application/vnd.apple.mpegurl": HLS MPEG-TS AAC 128-kbit stream with AES encryption. **(2)** "audio/mpeg": MP3 HTTP progressive download.|
| ExpiresOn   | DateTime                                         | GMT expiry time of the stream URL. |

## Sample JSON syntax
```json
{
  "Url": "https://webstream-vh.akamaihd.net/i/129/580/712/155/audio.mp4/
    master.m3u8?rid=b56194dd-1720-4984-a9e8-0666cb717a5d-i2-fr-FR-music-asset-location&
    hdnea=exp=1405687092~acl=/i/129/580/712/155/audio.mp4*~
    hmac=4fd5bc2e422b8cb152cc40169f9f4a883c6cda372236f6a12e3985061bcdfa31",
  "ContentType": "application/vnd.apple.mpegurl",
  "ExpiresOn": "2014-07-18T12:38:12.349Z"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
