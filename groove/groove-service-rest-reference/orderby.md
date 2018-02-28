---
title: OrderBy parameter for Groove Music APIs | Groove Services
description:  Learn about the use of orderBy parameter for Catalog and Collection Browse APIs.
keywords: groove music, groove api, groove orderby parameter
author: sakley
ms.assetid: 1a8c2302-d30c-4359-99c0-c775ea5f0109
---

# orderBy parameter for Catalog and Collection Browse APIs
The Catalog Browse and Collection Browse APIs offer an optional query parameter **orderBy** that allows ordering the results in a specific order.

When you don't specify a value for **orderBy**, we choose the default value depending on what type of content you are browsing.

If you specify an invalid value for a specific content, we will issue an HTTP 400 Bad Request error (for example, ordering Artists by ReleaseDate makes no sense).

## Possible values in the Collection Browse API

| **Item type**                                   | **orderBy value** | **Description**                                                      |
|-------------------------------------------------|-------------------|----------------------------------------------------------------------|
| [Artist](JSON-Artist.md)                        | ArtistName        | Default. The artist's name, sorted alphabetically.                   |
|                                                 | CollectionDate    | Date when the artist was added to the collection, most recent first. |
| [Album](JSON-Album.md)                          | AlbumTitle        | Default. The album's title, sorted alphabetically.                   |
|                                                 | ArtistName        | Name of the main artist of the album, sorted alphabetically.         |
|                                                 | GenreName         | Genre of the album, sorted alphabetically.                           |
|                                                 | ReleaseDate       | Release date of the album, most recent first.                        |
|                                                 | CollectionDate    | Date when the album was added to the collection, most recent first   |
| [Playlist](JSON-Playlist.md)                    | CollectionDate    | Default. Date when the playlist was created, most recent first       |
| [Track](JSON-Track.md)                          | TrackTitle        | Default. The track's title, sorted alphabetically                    |
|                                                 | AlbumTitle        | Title of the album containing the track, sorted alphabetically.      |
|                                                 | ArtistName        | Name of the main artist of the track, sorted alphabetically          |
|                                                 | GenreName         | Genre of the track, sorted alphabetically                            |
|                                                 | ReleaseDate       | Release date of the track, most recent first                         |
|                                                 | CollectionDate    | Date when the track was added to the collection, most recent first   |
|                                                 | TrackNumber       | Track number                                                         |

## Possible values in the Catalog Browse API

| **Item type**                                                                  | **orderBy value** | **Description**                               |
|--------------------------------------------------------------------------------|-------------------|-----------------------------------------------|
| [Artist](JSON-Artist.md), [Album](JSON-Album.md), or [Track](JSON-Track.md)    | AllTimePlayCount  | The number of times the item has been played. |
|                                                                                | ReleaseDate       | Default. Release date.                        |
|                                                                                | MostPopular       | Popularity.                                   |

#### Parent
[Groove Service REST Reference](overview.md)

