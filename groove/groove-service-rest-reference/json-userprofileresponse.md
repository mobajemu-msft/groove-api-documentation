---
title: UserProfileResponse JSON object | Groove Services
description:  Learn about UserProfileResponse JSON object in Groove Music API.
keywords: groove music, groove api, groove userprofileresponse json
author: sakley
ms.assetid: 5b62bf5f-a1cd-4669-9bfc-e14c92906912
---

# UserProfileResponse (JSON)
Profile of the user, including subscription, collection, and culture information.

## UserProfileResponse
The UserProfileResponse object has the following specification.

| **Member**                         | **Type**                                                             | **Description**                                                                                                                                                                                       |
|------------------------------------|----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Error                              | [Error](JSON-Error.md)                                               | Optional error object.                                                                                                                |
| HasSubscription                    | Boolean value                                                        | The user's subscription state (if the request was user-authenticated).                                                                                                   |
| IsSubscriptionAvailableForPurchase | Boolean value                                                        | Whether Groove Music subscriptions are available in the request's country or not.                                                                                                                   |
| Culture                            | string                                                               | The culture associated with the request. The culture is obtained from the user authentication token if there is one, the country and language URL parameters if provided, or the caller's IP address. |
| Collection                         | [CollectionState](JSON-CollectionState.md)                           | The state of the user's collection (if the request was user-authenticated).                                                                                                   |
| Subscription                       | [SubscriptionState](JSON-SubscriptionState.md)                       | The state of the user's Groove Music subscription (if any).                                                                                                                  |

## Sample JSON syntax
```json
{
  "HasSubscription": true,
  "IsSubscriptionAvailableForPurchase": true,
  "Culture": "fr-FR",
  "Collection": {
    "Token": "3.0.0.0.0.0.0",
    "RemainingPlaylistCount": 100,
    "RemainingTrackCount": 50000
  },
  "Subscription": {
    "Type": "Paid",
    "Region": "FR"
  }
}
```

#### Parent
[Groove Service REST Reference](overview.md)
