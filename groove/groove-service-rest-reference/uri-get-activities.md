---
title: Get available activities for a given locale| Groove Services
description:  Learn how to browse available activities in Groove Music with the APIs.
keywords: groove music, groove api, groove user collection, groove activities api, activities
author: bfreydier
ms.assetid: 
---

# GET (/1/content/{namespace}/catalog/activities)
Get a list of activities available for a locale.

-   [Remarks](#remarks)
-   [Response object](#response-object)
-   [Examples](#examples)

## Remarks
The BrowseActivities request is composed of mandatory and optional URL parts and query parameters. A request containing all parameters would resemble the following string:
```
/1/content/{namespace}/catalog/activities?language={language}&country={country}
```
For parameters common to every Groove RESTful API, see [Parameters common to every Groove RESTful API](common-parameters.md). For a table of error codes, see [Error (JSON)](JSON-Error.md). For HTTP status codes, see [Groove RESTful API HTTP Status Codes](http-status-codes.md).

## Response object
[ContentResponse (JSON)](JSON-ContentResponse.md)

## Examples
### Browse activities
#### Request
```http
GET /1/content/music/catalog/activities

Authorization: Bearer [...]
```

#### Response
```json   
{
  "CatalogActivities": [
    {
      "Id": "Focus",
      "Name": "Focus",
      "Description": "Turn up the music, tune out the noise",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Focus/image?locale=en-GB"
    },
    {
      "Id": "Game",
      "Name": "Game",
      "Description": "Listen while you play",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Game/image?locale=en-GB"
    },
    {
      "Id": "Party",
      "Name": "Party",
      "Description": "Your party starts here",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Party/image?locale=en-GB"
    },
    {
      "Id": "Workout",
      "Name": "Workout",
      "Description": "Get strong, get focused, get going",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Workout/image?locale=en-GB"
    },
    {
      "Id": "Celebration",
      "Name": "Celebration",
      "Description": "Good tunes for good times",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Celebration/image?locale=en-GB"
    },
    {
      "Id": "Dinner_Party",
      "Name": "Dinner Party",
      "Description": "Instant ambience for a memorable meal",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Dinner_Party/image?locale=en-GB"
    },
    {
      "Id": "Driving",
      "Name": "Driving",
      "Description": "Get your show on the road",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Driving/image?locale=en-GB"
    },
    {
      "Id": "Travel",
      "Name": "Travel",
      "Description": "Songs for a new adventure",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Travel/image?locale=en-GB"
    },
    {
      "Id": "Family_listening",
      "Name": "Family listening",
      "Description": "Jams for the whole fam",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Family_listening/image?locale=en-GB"
    },
    {
      "Id": "Wake_up",
      "Name": "Wake up",
      "Description": "Roll out of bed ready to seize the day",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Wake_up/image?locale=en-GB"
    }
  ],
  "Culture": "en-GB"
}
```

#### Browse activities for a specific locale
#### Request
```http
GET /1/content/music/catalog/activities?country=fr&language=fr

Authorization: Bearer [...]
```

#### Response
```json
{
  "CatalogActivities": [
    {
      "Id": "Focus",
      "Name": "Concentration",
      "Description": "Montez le son, ne vous souciez pas du bruit",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Focus/image?locale=fr-FR"
    },
    {
      "Id": "Workout",
      "Name": "Sport",
      "Description": "Soyez fort, actif, toujours en mouvement",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Workout/image?locale=fr-FR"
    },
    {
      "Id": "Party",
      "Name": "Fête",
      "Description": "C'est ici que la fête commence ",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Party/image?locale=fr-FR"
    },
    {
      "Id": "Game",
      "Name": "Jeux Video",
      "Description": "",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Game/image?locale=fr-FR"
    },
    {
      "Id": "Celebration",
      "Name": "Evènement",
      "Description": "Un bon son pour des moments mémorables",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Celebration/image?locale=fr-FR"
    },
    {
      "Id": "Dinner_Party",
      "Name": "Dîner",
      "Description": "Une belle ambiance pour un repas mémorable",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Dinner_Party/image?locale=fr-FR"
    },
    {
      "Id": "Driving",
      "Name": "En voiture",
      "Description": "Égayez vos déplacements",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Driving/image?locale=fr-FR"
    },
    {
      "Id": "Travel",
      "Name": "Voyage",
      "Description": "Détendez-vous, relaxez-vous, déconnectez-vous",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Travel/image?locale=fr-FR"
    },
    {
      "Id": "Family_listening",
      "Name": "Famille",
      "Description": "De la musique pour toute la famille",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Family_listening/image?locale=fr-FR"
    },
    {
      "Id": "Wake_up",
      "Name": "Réveil",
      "Description": "Réveillez-vous de bonne humeur",
      "ImageUrl": "https://musicimage.xboxlive.com/catalog/music.activity.Wake_up/image?locale=fr-FR"
    }
  ],
  "Culture": "fr-FR"
}
```

### Parent
[Groove Service REST Reference](overview.md)
