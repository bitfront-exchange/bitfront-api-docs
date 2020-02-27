# Market trade history

Retrieves the recent trade records under the given conditions in BITFRONT. You can set the conditions through the query parameters. <br/>
See the parameter descriptions.

> **Note**
>
> - This API can be used without API KEY.
> - It only provides trade records over the last 3 months.
> - The result records will be stored in `responseData` and sorted in descending order of `responseData[].createAt`.

## Endpoint URI

```
GET https://openapi.bitfront.me/v1/market/public/tradeHistory?coinPair={coinPair}&startTime={startTime}&endTime={endTime}&max={max}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `coinPair` |A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'. <br/>For example, BCH.ETH means buying or selling BCH with ETH.|String|query| |
| `startTime` |The earliest time of trades to retrieve. It is in milliseconds in UTC.|Integer|query| |
| `endTime` |The latest time of trades to retrieve. It is a timestamp in milliseconds since Unix Epoch in UTC.|Integer|query| |
| `max` |The maximum number of trades to retrieve. It should be in the range of 1-100. The default is 100. Note that the returned records can be less than `max` because it only provides data over the last 3 months.|Integer|query| |

## Response

| Name | Description | Type | Included |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`     | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime` | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O                             |
| `statusCode`   | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | Integer | O        |
| `statusMessage` | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String                        | O        |
| `responseData` | See the reference object. | [responseData](#responsedata) |          |

### responseData

  - Type: array

The recent trade records in BITFRONT

Array of [history](#history)

### history

  - Type: object

| Name            | Description | Type   | Included |
| --------------- | ---------------------------------------------------------------------------------------------------- | ------ | -------- |
| `transactionID` | The transaction ID | Long   |          |
| `market`        | A [coin code](/5_Terms.md#coin-code) of the [Market](/5_Terms.md#market-for-coin-trading) | String |          |
| `currency`      | A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading) | String |          |
| `price`         | A unit price | Double |          |
| `amount`        | An amount | Double |          |
| `totalValue`    | `amount` * `price` | Double |          |
| `orderSide`     | A side of the order. It is one of the following: <br/>- "BUY": buy side <br/>- "SELL": sell side | String |          |
| `createAt`      | The time when the transaction is created. It is a timestamp in milliseconds since Unix Epoch in UTC. | Long   |          |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1528358968115,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": [
      {
          "transactionID": 10100000046610,
          "market": "ETH",
          "currency": "BCH",
          "price": 0.0008,
          "amount": 11,
          "totalValue": 0.0088,
          "orderSide": "BUY",
          "createdAt": 1528354656926
      },
      {
          "transactionID": 10100000046609,
          "market": "ETH",
          "currency": "BCH",
          "price": 0.0008,
          "amount": 11,
          "totalValue": 0.0088,
          "orderSide": "BUY",
          "createdAt": 1528354382338
      },
      {
          "transactionID": 10100000046606,
          "market": "BTC",
          "currency": "ETH",
          "price": 0.024001,
          "amount": 10,
          "totalValue": 0.24001,
          "orderSide": "SELL",
          "createdAt": 1528348471297
      },
      {
          "transactionID": 10100000046599,
          "market": "BTC",
          "currency": "BCH",
          "price": 0.158136,
          "amount": 4.982,
          "totalValue": 0.787833552,
          "orderSide": "SELL",
          "createdAt": 1528338502467
      },
      {
          "transactionID": 10100000046597,
          "market": "BTC",
          "currency": "BCH",
          "price": 0.158137,
          "amount": 0.02,
          "totalValue": 0.00316274,
          "orderSide": "SELL",
          "createdAt": 1528338502467
      }
  ]
}
```
