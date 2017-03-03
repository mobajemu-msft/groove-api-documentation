---
title: CreateRadioRequest JSON object | Groove Services
description:  Learn about CreateRadioRequest JSON object in Groove Music API.
keywords: groove music, groove api, groove createradiorequest json, groove radio
author: bfreydier
ms.assetid:  
---

# CreateRadioRequest (JSON)  
The input element for a radio station creation request of the [Create Radio Station](uri-create-radio.md) API

A CreateRadioRequest contains **strictly one** seed to create a radio, it can be a Genre or an Artist Id.

## CreateRadioRequest
The CreateRadioRequest object has the following specification.

| **Member**   | **Type**                                           | **Description**                    |
|--------------|----------------------------------------------------|------------------------------------|
| Seeds        | List of [Seed](JSON-Seed.md)                       | Seed for the radio                 |

## Sample JSON syntax
```json
{
	"Seeds" : [{
			"Id" : "music.24540000-0200-11db-89ca-0019b92a3933",
			"Type" : "Artist"
		}
	]
}
```

#### Parent
[Groove Service REST Reference](overview.md)
