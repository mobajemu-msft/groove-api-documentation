---
title: Activity JSON object | Groove Services
description:  Learn about Activity JSON object in Groove Music API.
keywords: groove music, groove api, groove activity json
author: bfreydier
ms.assetid: 65d5cf33-99c9-4a31-a8ed-77eb5fa33c8e
---

# Activity (JSON)
Describes an *activity*, a category for playlists.

This topic describes an *activity*, a category for playlists.

-   [Specification of **Activity**](#specification-of-activity)
-   [Sample JSON syntax](#sample-json-syntax)

## Specification of Activity
The **Activity** object has the following specification.

| **Member**            | **Type**                                                             | **Description**                                                                                                                                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Id**                | String                                                               | Identifier for this category. All Ids may be used in any API accepting an ID as input.                                                                                                                                                                                             |
| **Name**              | String                                                               | The localized name of this category.                                                                                                                                                                                                                                                                                                             |
| **ImageUrl**          | String                                                               | A direct link to the default image associated with this category. For more information about how these links may be customized to produce different images, see [Image Service](../Using-the-Groove-RESTful-Services/Image-Service.md).                                                                                                                |
| **Description**       | string                                                               | The localized description of this category                                                                                                                                                                                                                                                                                                                          |

## Sample JSON syntax
```json
{
     "Id": "Throwback",
     "Name": "Throwback",
     "Description": "Time machine tunes",
    "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Throwback/image?locale=en-US"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
