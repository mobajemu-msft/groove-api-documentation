---
title: Mood JSON object | Groove Services
description:  Learn about Mood JSON object in Groove Music API.
keywords: groove music, groove api, groove mood json
author: bfreydier
ms.assetid: 
---

# Mood (JSON)
Describes an *mood*, a category for playlists.

This topic describes an *mood*, a category for playlists.

-   [Specification of **mood**](#specification-of-mood)
-   [Sample JSON syntax](#sample-json-syntax)

## Specification of Mood
The **Mood** object has the following specification.

| **Member**            | **Type**                                                             | **Description**                                                                                                                                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Id**                | String                                                               | Identifier for this category. All Ids may be used in any API accepting an ID as input.                                                                                                                                                                                             |
| **Name**              | String                                                               | The localized name of this category.                                                                                                                                                                                                                                                                                                             |
| **ImageUrl**          | String                                                               | A direct link to the default image associated with this category. For more information about how these links may be customized to produce different images, see [Image Service](../Using-the-Groove-RESTful-Services/Image-Service.md).                                                                                                                |
| **Description**       | string                                                               | The localized description of this category                                                                                                                                                                                                                                                                                                                          |

## Sample JSON syntax
```json
{
    "Id": "Focus",
    "Name": "Focus",
    "Description": "Turn up the music, tune out the noise",
    "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Focus/image?locale=en-US"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
