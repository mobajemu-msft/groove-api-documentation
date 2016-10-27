# SubscriptionState (JSON)
Subscription information for the user.

## SubscriptionState
The SubscriptionState object has the following specification.

| **Member** | **Type**    | **Description**                                                                                                   |
|------------|-------------|-------------------------------------------------------------------------------------------------------------------|
| Type       | string      | The user's subscription type (for example, "Paid" or "Trial").                                                    |
| Region     | string      | Two-letter region code of the subscription. This usually matches the user's account country, but not necessarily. |
| EndDate    | DateTime    | Estimated expiration date of the current subscription (can be null if subscription is automatically renewed).     |

## Sample JSON syntax
```json
{
  "Type": "Paid",
  "Region": "FR",
  "EndDate": "2017-07-18T12:38:12.349Z"
}
```

#### Parent
[Groove Service REST Reference](overview.md)
