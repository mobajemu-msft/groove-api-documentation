|                            |
|----------------------------|
| TrackAction (JSON)         |
| [See Also](#seeAlsoToggle) |

|  Collapse All    Expand All     |
|---------------------------------|

Visual Basic (Usage)
Visual Basic (Declaration)
C\#
C++
JavaScript

An action (such as add or delete) on a specific track. <span id="ID4EN" class="anchor"></span>

TrackAction
===========

The TrackAction object has the following specification.

| **Member** | **Type** | **Description**                                                                                                      |
|------------|----------|----------------------------------------------------------------------------------------------------------------------|
| Id         | string   | ID of the track on which the action should be performed. (You can get the ID by browsing the catalog or collection.) |
| Action     | string   | Action to perform ("add", "delete", and "remove").                                                                   |

Sample JSON syntax
==================

{

"Id": "music.A83EB907-0100-11DB-89CA-0019B92A3933",

"Action": "Add"

}

See also
========

#### Parent

[Groove Service REST Reference](../Endpointdocumentation/atoc_xbm_reference.htm)

© 2016 Microsoft Corporation. All rights reserved.
Submit feedback on <https://forums.xboxlive.com/>.
Version: 2.0.100825.0 \[private build\]
