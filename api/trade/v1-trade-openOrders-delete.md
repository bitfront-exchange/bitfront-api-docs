# Cancellation of all open orders

Request to cancel your all open orders. It will returns the list of orders you requested to cancel. <br/>
For each order, if the order is partially filled, it only tries to cancel the remaining amount.

> **Caution**
>
> `statusCode` of 1000 means the cancellation is NOT successfully done BUT requested well.
> If you want to check whether the order has been cancelled, use [`/v2/account/orders/{orderID}`](/api/account/v2-account-orders-orderID-get.md#order-information-v2).

## Endpoint URI

```
DELETE https://openapi.bitfront.me/v1/trade/openOrders/{coinPair}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `coinPair` | A [coin pair](/5_Terms.md#coin-pair) for the orders to request to cancel. <br/>A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'. <br/>For example, BCH.ETH means buying or selling BCH with ETH.|String|path|O|

## Response

| Name            | Description | Type                          | Included |
| --------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime`  | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O        |
| `statusCode`    | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | Integer | O        |
| `statusMessage` | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String | O        |
| `responseData`  | See the reference object. | [responseData](#responsedata) |          |

### responseData

  - Type: object

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `orderIDList` |Array of Long. the list of the order IDs|array| |
| `requestAt` |The time when the order is requested. It is a timestamp in milliseconds since Unix Epoch in UTC.|Long| |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1525080718,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderIDList": [
            10100000000561,
            10100000000563,
            10100000000564,
            10100000000565
        ],
        "requestAt": 1525080718
    }
}
```
