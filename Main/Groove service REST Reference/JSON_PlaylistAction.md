|                            |
|----------------------------|
| PlaylistAction (JSON)      |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

The input element for every playlist action request: create, update, and delete.

A PlaylistAction contains playlist metadata and a list of actions to perform on the tracks in the playlist.

PlaylistAction
==============

The PlaylistAction object has the following specification.

| **Member**           | **Type**                                                             | **Description**                                                                                                                                                                        |
|----------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Id                   | string                                                               | Required. ID of the playlist (required for update and delete).                                                                                                                         |
| CollectionStateToken | string                                                               | Optional. Token indicating the current version of the collection.                                                                                                                      |
| Name                 | string                                                               | Optional. Name of the playlist.                                                                                                                                                        |
| IsPublished          | Boolean value                                                        | Optional. Whether the playlist is public or not.                                                                                                                                       |
| InsertBeforeTrackId  | string                                                               | (Optional) When reordering tracks, track before which you want to insert the tracks specified in the TrackActions field. Can be null if you want to insert at the end of the playlist. |
| TrackActions         | List of [TrackAction](../Endpointdocumentation/JSON_TrackAction.htm) | Optional. List of actions to perform on the playlist's tracks.                                                                                                                         |

Sample JSON syntax
==================

{

"Id": "music.playlist.56c99764-800a-00fe-552f-ee11db9370d1",

"TrackActions": \[

{

"Id": "music.AQQfj2DtARB5ZkGFCMHea2k8Xge5PqgAAQ",

"Action": "Delete"

},

{

"Id": "music.2DEBEA07-0100-11DB-89CA-0019B92A3933",

"Action": "Add"

}

\]

}

See also
========

#### Parent

[Groove Service REST Reference](../Endpointdocumentation/atoc_xbm_reference.htm)

#### Reference

[/1/content/{namespace}/collection/playlists/create](../Endpointdocumentation/URI_ContentNamespaceCollectionPlaylistsCreate.htm)
[/1/content/{namespace}/collection/playlists/delete](../Endpointdocumentation/URI_ContentNamespaceCollectionPlaylistsDelete.htm)
[/1/content/{namespace}/collection/playlists/update](../Endpointdocumentation/URI_ContentNamespaceCollectionPlaylistsUpdate.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
