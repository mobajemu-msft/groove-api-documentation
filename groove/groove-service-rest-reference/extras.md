---
title: Extra parameters for Groove Music lookup API| Groove Services
description:  Learn about extra parameters for Groove Music lookup API requests.
keywords: groove music, groove api, groove api extra parameters
author: sakley
ms.assetid: aad6d784-ffce-4291-b9ae-b29de455ed33
---

| Notice to customers|
|----- |
|Starting Oct 2nd, the onboarding to the Groove Music API is disabled. As part of the partnership, the Groove Music Pass service will be discontinued on December 31, 2017.
After that date, Groove Music Pass content will not stream or play and our API features will not be accessible.
Please check our FAQ on <https://aka.ms/groovepartnerfaq> . All features of the Music API will be supported until Dec 31st.|


# Extra parameters for Lookup API
The lookup API offers an optional query parameter **extras** that allows requesting a list of extra fields that are by default not included in the responses. Multiple values in that list must be separated with **+**. Some combinations of extras and sources are not supported, in that case the extra is ignored.

Be aware that these extras don't come for free; each of them has a negative impact on the response time of the Lookup API. Only request them if you need them.

## Possible values
| **Item type** | **"Extras" value** | **Available in data sources** | **Corresponding extra information**                                                                 |
|---------------|--------------------|-------------------------------|-----------------------------------------------------------------------------------------------------|
| [Artist](JSON-Artist.md)      | albums             | Catalog, Collection           | The artist's paginated list of albums                                                               |
|               | topTracks          | Catalog                       | The artist's paginated list of top tracks                                                           |
| [Album](JSON-Album.md)         | tracks             | Catalog, Collection           | The album's paginated list of tracks                                                                |
|               | artistDetails      | Catalog                       | Extra fields in the album's artist list (level of detail equivalent to a Lookup call on the artist) |
| [Track](JSON-Track.md)         | albumDetails       | Catalog                       | Extra fields in the track's album (level of detail equivalent to a Lookup call on the album)        |
|               | artistDetails      | Catalog                       | Extra fields in the track's artist (level of detail equivalent to a Lookup call on the artist)      |

#### Parent
[Groove Service REST Reference](overview.md)
