---
title: Genre JSON object | Groove Services
description:  Learn about Genre JSON object in Groove Music API.
keywords: groove music, groove api, groove genre json, genre
author: bfreydier
---

# Genre (JSON)
Describes a musical *(sub)genre*, a localized (sub)category for track, albums and playlists.

-   [Specification of **genre**](#specification-of-genre)
-   [Sample JSON syntax](#sample-json-syntax)

## Specification of Genre
The **Genre** object has the following specification.

| **Member**            | **Type**                                                             | **Description**                                                                                                                                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Name**              | String                                                               | The localized name of the genre.                                                                                                                                                                                                                                                                                                            |
| **ParentName**              | String                                                               | The localized name of the parent genre (if any).                                                                                                                                                                                                                                                                                                              |
| **HasEditorialPlaylists**       | Boolean                                                        | Determine if there are any editorial playlists associated with this genre.                                                                                                                                                                                                                                          |

## Sample JSON syntax
```json
{
      "ParentName": "Electronic / Dance",
      "HasEditorialPlaylists": true,
      "Name": "Dance"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
