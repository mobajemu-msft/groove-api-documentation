|                            |
|----------------------------|
| ContentResponse (JSON)     |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

The output element for most content APIs. <span id="ID4EN" class="anchor"></span>

ContentResponse
===============

The ContentResponse object has the following specification.

| **Member** | **Type**                                                             | **Description**                                                                                                                                                                                                                                                                                                             |
|------------|----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Error      | [Error](../Endpointdocumentation/JSON_Error.htm)                     | Optional error.                                                                                                                                                                                                                                                                                                             |
| Artists    | List of [Artist](../Endpointdocumentation/JSON_Artist.htm)           | A paginated list of Artists that matched the request criteria.                                                                                                                                                                                                                                                              |
| Albums     | List of [Album](../Endpointdocumentation/JSON_Album.htm)             | A paginated list of Albums that matched the request criteria.                                                                                                                                                                                                                                                               |
| Tracks     | List of [Track](../Endpointdocumentation/JSON_Track.htm)             | A paginated list of Tracks that matched the request criteria.                                                                                                                                                                                                                                                               |
| Playlists  | List of [Playlist](../Endpointdocumentation/JSON_Playlist.htm)       | A paginated list of Playlists that matched the request criteria.                                                                                                                                                                                                                                                            |
| Results    | List of [ContentItem](../Endpointdocumentation/JSON_ContentItem.htm) | A paginated list of ContentItems that matched the request criteria. These items are used for ordered lists mixing multiple types of content such as the [Spotlight](../Endpointdocumentation/URI_ContentNamespaceSpotlightGET.htm) and [NewReleases](../Endpointdocumentation/URI_ContentNamespaceNewreleasesGET.htm) APIs. |
| Genres     | GenreList                                                            | A list of string representing the different possible genres for a given locale. Used in the [Browse Genres](../Endpointdocumentation/URI_ContentNamespaceCatalogGenresGET.htm) API.                                                                                                                                         |
| Culture    | string                                                               | The culture used for processing the [Browse Genres](../Endpointdocumentation/URI_ContentNamespaceCatalogGenresGET.htm) request, computed from Country and Language parameters, user authentication and/or geolocation.                                                                                                      |

Sample JSON syntax
==================

{

"Artists": {

"Items": \[

{

"Genres": \[

"Electronic / Dance"

\],

"Subgenres": \[

"Dance"

\],

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 168791"

},

"Source": "Catalog"

}

\]

}

}

See also
========

#### Parent

[Groove Service REST Reference](../Endpointdocumentation/atoc_xbm_reference.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
