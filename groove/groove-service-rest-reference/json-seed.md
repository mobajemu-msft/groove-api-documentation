---
title: Seed JSON object | Groove Services
description:  Learn about Seed JSON object in Groove Music API.
keywords: groove music, groove api, groove sedd json
author: bfreydier
---

# Seed (JSON)  
The seed object is used to create a radio, it can contain an artist id or a genre.

## Seed
The Seed object has the following specification.

| **Member**   | **Type**                | **Description**                                                               |
|--------------|-------------------------|-------------------------------------------------------------------------------|
| Id           | string                  | Genre (from [Get Genres API](uri-get-genres.md)) or Artist Id                 |
| Type         | string                  | "Artist" or "Genre"                                                           |

## Sample JSON syntax
```json
{
    "Id" : "music.24540000-0200-11db-89ca-0019b92a3933",
    "Type" : "Artist"
}
```
```json
{
    "Id" : "Pop",
    "Type" : "Genre"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
