|                            |
|----------------------------|
| ContentItem (JSON)         |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

An item of content (either an **Album** or an **Artist**). <span id="ID4ES" class="anchor"></span>

ContentItem
===========

The ContentItem object has the following specification.

| **Member** | **Type**                                           | **Description**                                        |
|------------|----------------------------------------------------|--------------------------------------------------------|
| Type       | ItemType                                           | The type of the content element wrapped in this item.  |
| Album      | [Album](../Endpointdocumentation/JSON_Album.htm)   | Album item if **Type** is **Albums**, null otherwise   |
| Artist     | [Artist](../Endpointdocumentation/JSON_Artist.htm) | Artist item if **Type** is **Artists**, null otherwise |

Sample JSON syntax
==================

{

"Type": "Artists",

"Artist": {

"Genres": \[

"Pop"

\],

"Subgenres": \[

"Dance Pop"

\],

"Id": "music.26BA0500-0200-11DB-89CA-0019B92A3933",

"Name": "Miley Cyrus",

"ImageUrl": "http://musicimage.xboxlive.com/content/music.26BA0500-0200-11DB-89CA-0019B92A3933/image?locale=en-US",

"Link": "http://music.xbox.com/Artist/26BA0500-0200-11DB-89CA-0019B92A3933?partnerID=AwesomePartner",

"OtherIds": {

"music.amg": "P 823418"

},

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
