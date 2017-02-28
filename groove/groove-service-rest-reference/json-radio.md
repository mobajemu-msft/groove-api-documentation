---
title: Radio JSON object | Groove Services
description:  Learn about Radio JSON object in Groove Music API.
keywords: groove music, groove api, groove radio json
author: bfreydier
---

# Radio (JSON)
A radio station

## Radio
The Radio object has the following specification.

| **Member**           | **Type**                                                                                                              | **Description**                                                                                                                                                                                                                                                                                                                                                             |
|----------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Id                   | string                                                                                                                | Identifier for this piece of content. All Ids are of the form {namespace}.{actual identifier} and may be used in any API accepting an ID as input.                                                                                                                                                                                                                          |
| Name                 | string                                                                                                                | The name of this piece of content.                                                                                                                                                                                                                                                                                                                                          |
| OtherIds             | Dictionary&lt;*string*,*string*&gt;                                                                                   | An optional collection of IDs on top of the main ID, which identify this piece of content. Each key is the namespace or sub-namespace in which the ID belongs, and each value is a secondary ID for this piece of content                                                                                                                                                   |
| Source               | string                                                                                                                | An indication of the data source for this piece of content. Possible values are **Collection** and **Catalog**.                                                                                                                                                                                                                                                             |
| CompatibleSources    | string                                                                                                                | An indication of the categories of APIs and actions that this piece of content can be used with. Comma-separated list of one or multiple values among "Catalog", "Collection".                                |

## Sample JSON syntax
```json
 {
        "Id": "music.radio.63c1349a-7c4e-4ff4-a223-0daacab58d65",
        "Name": "Muse",
        "Source": "Catalog",
        "CompatibleSources": "Catalog"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
