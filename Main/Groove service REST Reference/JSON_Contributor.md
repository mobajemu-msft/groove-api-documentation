|                            |
|----------------------------|
| Contributor (JSON)         |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

An artist and the artist's role <span id="ID4EN" class="anchor"></span>

Contributor
===========

The Contributor object has the following specification.

| **Member** | **Type**                                           | **Description**                                         |
|------------|----------------------------------------------------|---------------------------------------------------------|
| Artist     | [Artist](../Endpointdocumentation/JSON_Artist.htm) | The contributing artist.                                |
| Role       | string                                             | The type of contribution, such as "Main" or "Featured". |

Sample JSON syntax
==================

{

"Role": "Main",

"Artist": {

"Id": "music.C61C0000-0200-11DB-89CA-0019B92A3933",

"Name": "Daft Punk",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.C61C0000-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/C61C0000-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"Source": "Catalog"

}

}

See also
========

#### Parent

[Groove Service REST Reference](../Endpointdocumentation/atoc_xbm_reference.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
