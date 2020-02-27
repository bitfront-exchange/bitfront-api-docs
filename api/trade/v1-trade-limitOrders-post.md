# Limit order

Places a limit order with the given conditions. <br/>
You can set the conditions through the query parameters. See the parameter descriptions.

## Endpoint URI

```
POST https://openapi.bitfront.me/v1/trade/limitOrders
```

## Request parameters

| Name | Description | Type   | Loc. | Required |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ---- | -------- |
| `coinPair` | A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'. <br/>For example, BCH.ETH means buying or selling BCH with ETH. | String | body   | O    |
| `quantity` | The maximum or minimum quantity to order. It should be greater than 0. | Double | body | √ |
| `price` | The maximum or minimum price to order. It should be greater than 0. | Double | body | O        |
| `orderSide` | The side of order. It should be one of the following: <br/>- "BUY": buy order <br/>- "SELL": sell order | String | body | √ |

## Response

| Name            | Description | Type                          | Included |
| --------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime`  | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O        |
| `statusCode`    | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | Integer | O        |
| `statusMessage` | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String                        | O        |
| `responseData`  | See the reference object. | [responseData](#responsedata) |          |

### responseData

  - Type: object

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `orderID` |The order ID. Use it to cancel or check the details of the order.|Long| |
| `requestAt` |The time when the order is requested. It is a timestamp in milliseconds since Unix Epoch in UTC.|Long| |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1525079412,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": {
      "orderID": 10100000000565,
      "requestAt": 1525079412
  }
}
```
