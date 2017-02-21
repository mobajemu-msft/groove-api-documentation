---
title: Get available moods for a given locale| Groove Services
description:  Learn how to browse available moods in Groove Music with the APIs.
keywords: groove music, groove api, groove user collection, groove moods api, moods
author: bfreydier
ms.assetid: 882780e0-1a96-4ae9-8558-db1c5eaa477f
---

# GET (/1/content/{namespace}/catalog/moods)
Get a list of moods available for a locale.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [Examples](#examples)

## Remarks
The BrowseMoods request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
/1/content/{namespace}/catalog/moods?language={language}&country={country}
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

## Response object
[ContentResponse (JSON)](JSON-ContentResponse.md)

## Examples
### Browse moods
#### Request
```http
GET /1/content/music/catalog/moods

Authorization: Bearer [...]
```

#### Response
```json   
{
  "CatalogMoods": [
    {
      "Id": "Happy",
      "Name": "Happy",
      "Description": "Mood-boosting music",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Happy/image?locale=en-GB"
    },
    {
      "Id": "Chill",
      "Name": "Chill",
      "Description": "Kick back, relax, unwind",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Chill/image?locale=en-GB"
    },
    {
      "Id": "Energetic",
      "Name": "Energetic",
      "Description": "Can't stop, won't stop",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Energetic/image?locale=en-GB"
    },
    {
      "Id": "Throwback",
      "Name": "Throwback",
      "Description": "Time machine tunes",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Throwback/image?locale=en-GB"
    },
    {
      "Id": "Rage",
      "Name": "Rage",
      "Description": "Shout it out with aggro anthems",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Rage/image?locale=en-GB"
    },
    {
      "Id": "Sleepy",
      "Name": "Sleepy",
      "Description": "Drift off to dreamland",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Sleepy/image?locale=en-GB"
    },
    {
      "Id": "Romantic",
      "Name": "Romantic",
      "Description": "Feel the love",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Romantic/image?locale=en-GB"
    },
    {
      "Id": "Melancholy",
      "Name": "Melancholy",
      "Description": "Feeling blue?",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Melancholy/image?locale=en-GB"
    }
  ],
  "Culture": "en-GB"
}
```

#### Browse moods for a specific locale
#### Request
```http
GET /1/content/music/catalog/moods?country=fr&language=fr

Authorization: Bearer [...]
```

#### Response
```json
{
  "CatalogMoods": [
    {
      "Id": "Happy",
      "Name": "Heureux",
      "Description": "Que du bonheur",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Happy/image?locale=fr-FR"
    },
    {
      "Id": "Chill",
      "Name": "Détente",
      "Description": "Détendez-vous, relaxez-vous, déconnectez-vous",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Chill/image?locale=fr-FR"
    },
    {
      "Id": "Energetic",
      "Name": "Dynamique",
      "Description": "Toujours en mouvement",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Energetic/image?locale=fr-FR"
    },
    {
      "Id": "Throwback",
      "Name": "Nostalgique",
      "Description": "Remontez le temps",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Throwback/image?locale=fr-FR"
    },
    {
      "Id": "Rage",
      "Name": "Enervé",
      "Description": "Fureur de vivre",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Rage/image?locale=fr-FR"
    },
    {
      "Id": "Sleepy",
      "Name": "Sommeil",
      "Description": "Faites de beaux rêves",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Sleepy/image?locale=fr-FR"
    },
    {
      "Id": "Romantic",
      "Name": "Romantique",
      "Description": "De l'amour comme s'il en pleuvait",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Romantic/image?locale=fr-FR"
    },
    {
      "Id": "Melancholy",
      "Name": "Triste",
      "Description": "Coup de blues",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.mood.Melancholy/image?locale=fr-FR"
    }
  ],
  "Culture": "fr-FR"
}
```

### Parent
[Groove Service REST Reference](overview.md)
