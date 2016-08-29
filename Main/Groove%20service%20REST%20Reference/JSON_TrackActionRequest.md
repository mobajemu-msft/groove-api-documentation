|                            |
|----------------------------|
| TrackActionRequest (JSON)  |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

The input element for every track action request: add and delete. <span id="ID4EN" class="anchor"></span>

TrackActionRequest
==================

The TrackActionRequest object has the following specification.

| **Member** | **Type**       | **Description**                                                                                                                                                                                                                                                       |
|------------|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TrackIds   | List of string | List of track IDs to add to the user's collection. These IDs can be found through [/1/content/{id}/lookup](../Endpointdocumentation/URI_ContentLookup.htm) or [/1/content/{namespace}/search?q={query}](../Endpointdocumentation/URI_ContentSearch.htm), for example. |

Sample JSON syntax
==================

{

"TrackIds": \[

"music.873FB507-0100-11DB-89CA-0019B92A3933",

"music.A83EB907-0100-11DB-89CA-0019B92A3933"

\]

}

See also
========

#### Parent

[Groove Service REST Reference](../Endpointdocumentation/atoc_xbm_reference.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
