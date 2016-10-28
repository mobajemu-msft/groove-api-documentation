---
title: TrackAction JSON object | Groove Services
description:  Learn about TrackAction JSON object in Groove Music API.
keywords: groove music, groove api, groove trackaction json
author: sakley
ms.assetid: 
---

# TrackAction (JSON)        
An action (such as add or delete) on a specific track.

## TrackAction
The TrackAction object has the following specification.

| **Member** | **Type** | **Description**                                                                                                      |
|------------|----------|----------------------------------------------------------------------------------------------------------------------|
| Id         | string   | ID of the track on which the action should be performed. (You can get the ID by browsing the catalog or collection.) |
| Action     | string   | Action to perform ("add", "delete", and "remove").                                                                   |

## Sample JSON syntax
```json
{
   "Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",
   "Action": "Add"
}
```

#### Parent  
[Groove Service REST Reference](overview.md)
