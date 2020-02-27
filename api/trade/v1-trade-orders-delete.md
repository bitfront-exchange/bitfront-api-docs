# Cancellation

Requests to cancel a single order. <br/>
If the order is partially filled, it only tries to cancel the remaining amount.

> **Caution**
>
> `statusCode` of 1000 means the cancellation is NOT successfully done BUT requested well. If you want to check whether the order has been cancelled, use [`/v2/account/orders/{orderID}`](/api/account/v2-account-orders-orderID-get.md#order-information-v2).

## Endpoint URI

```
DELETE https://openapi.bitfront.me/v1/trade/orders/{orderID}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `orderID` | The ID of the order to request to cancel. You can get the ID whenever you place an order or retrieve your order list. | Long | path | √ |

## Response

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `timezone` |The time standard for the `responseTime`. It is always "UTC".|String|O|
| `responseTime` |The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | √ |
| `statusCode` |The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).|Integer|O|
| `statusMessage` |The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).|String|O|
| `responseData` |See the reference object.|[responseData](#responsedata)| |

### responseData

  - Type: object

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `orderID` | The order ID | Long | |
| `requestAt` | The time when the order is requested. It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1525080581,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderID": 10100000000561,
        "requestAt": 1525080581
    }
}
```
