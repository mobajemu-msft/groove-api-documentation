---
title: ContentItem JSON object | Groove Services
description:  Learn about ContentItem JSON object in Groove Music API.
keywords: groove music, groove api, groove contentitem json
author: sakley
ms.assetid: 32dafb90-9740-405c-ad94-7fac34f36672
---

# ContentItem (JSON)         
A piece of content (either an [**Album**](JSON-Album.md) or an [**Artist**](JSON-Artist.md)).

## ContentItem
The ContentItem object has the following specification.

| **Member** | **Type**                                           | **Description**                                        |
|------------|----------------------------------------------------|--------------------------------------------------------|
| Type       | ItemType                                           | The type of the content element wrapped in this item.  |
| Album      | [Album](JSON-Album.md)   | Album item if **Type** is **Albums**, null otherwise   |
| Artist     | [Artist](JSON-Artist.md) | Artist item if **Type** is **Artists**, null otherwise |

## Sample JSON syntax
```json
{
  "Type": "Artists",
  "Artist": {
    "Genres": [
      "Pop"
    ],
    "Subgenres": [
      "Dance Pop"
    ],
    "Id": "music.26BA0500-0200-11DB-89CA-0019B92A3933",
    "Name": "Miley Cyrus",
    "ImageUrl": "https://musicimage.xboxlive.com/content/music.26BA0500-0200-11DB-89CA-0019B92A3933/image?locale=en-US",
    "Link": "https://music.microsoft.com/Artist/26BA0500-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",
    "OtherIds": {
      "music.amg": "P   823418"
    },
    "Source": "Catalog",
    "CompatibleSources": "Catalog, Collection"
  }
}
```

#### Parent  
[Groove Service REST Reference](overview.md)
