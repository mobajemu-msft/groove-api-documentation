---
title: CollectionStateJSON object | Groove Services
description:  Learn about CollectionState JSON object in Groove Music API.
keywords: groove music, groove api, groove collectionstate json
author: sakley
ms.assetid: cdfd1422-260d-48e5-937b-f7d8b0503679
---

# CollectionState (JSON)     
The state of the user's collection (if the request was user-authenticated).

## CollectionState
The CollectionState object has the following specification.

| **Member**             | **Type**              | **Description**                                             |
|------------------------|-----------------------|-------------------------------------------------------------|
| Token                  | string                | A token which indicates the version of the collection.      |
| PlaylistCount          | 32-bit signed integer | The number of playlists in the collection.                  |
| RemainingPlaylistCount | 32-bit signed integer | The number of playlists the user can add to the collection. |
| TrackCount             | 32-bit signed integer | The number of tracks in the collection.                     |
| RemainingTrackCount    | 32-bit signed integer | The number of tracks the user can add to the collection.    |

#### Parent
[Groove Service REST Reference](overview.md)
