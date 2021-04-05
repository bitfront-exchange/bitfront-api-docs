# User trade history v2

Retrieves your recent trade records under the given conditions. <br/>
You can set the conditions through the query parameters. See the parameter descriptions.

> **Note**
>
> - The maximum period for the date condition is 30 days. In other words, the number of days from `startTime` to `endTime` MUST NOT exceed 30.
> - The result records will be stored in `responseData` and sorted in descending order of `responseData[].createAt`.
> - The number of this API call is allowed for 1 time per second and 30 times per minute.

## Endpoint URI

```
GET https://openapi.bitfront.me/v2/account/tradeHistory?coinPair={coinPair}&startTime={startTime}&endTime={endTime}&max={max}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `coinPair` |The cryptocurrencies for the trades to retrieve. <br/>A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'. <br/>For example, BCH.ETH means buying or selling BCH with ETH. | String | query | √ |
| `startTime` |The start time of the period condition for retrieving trade records. It is a timestamp in milliseconds since Unix Epoch in UTC.|Integer|query|O|
| `endTime` |The end time of the period condition for retrieving trade records. It is a timestamp in milliseconds since Unix Epoch in UTC. <br/>If unassigned, the default value of `startTime`+24hrs is used.|Integer|query| |
| `max` |The maximum number of trades to retrieve. It should be in the range of 1-100. The default is 100. <br/>Note that the returned records can be less than `max` because the API returns only the trades that had been made in the given period.|Integer|query| |

## Response

| Name            | Description                                                                                                | Type                          | Included |
| --------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime`  | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O        |
| `statusCode`    | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | Integer | O        |
| `statusMessage` | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String                        | O        |
| `responseData`  | See the reference object. | [responseData](#responsedata) |          |

### responseData

  - Type: array

A list of the trade records

Array of [history](#history)

### history

  - Type: object

| Name                 | Description                                                                                   | Type   | Included |
| -------------------- | --------------------------------------------------------------------------------------------- | ------ | -------- |
| `transactionID`      | The ID of a transaction | Long   |          |
| `orderID`            | The ID of an order | Long   |          |
| `market`             | A [coin code](/5_Terms.md#coin-code) of the [Market](/5_Terms.md#market-for-coin-trading)     | String |          |
| `currency`           | A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading) | String |          |
| `price`              | A unit price | Double |          |
| `amount`             | An amount | Double |          |
| `fee`                | A trading fee | Double |          |
| `totalConsideration` | price * amount + `fee` | Double |          |
| `orderSide`          | A side of the order. It is one of the following: <br/>- "BUY": buy side <br/>- "SELL": sell side | String| |
| `fillType` |A type of fill. It is one of the following: <br/>- "FULL": The transaction is fully filled <br/>- "PARTIAL": The transaction is partially filled | String| |
| `createAt` |The time when the transaction is created. It is a timestamp in milliseconds since Unix Epoch in UTC.|Long| |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1528359043142,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "transactionID": 10100000046610,
            "orderID": 10100000030913,
            "market": "ETH",
            "currency": "BCH",
            "price": 0.0008,
            "amount": 11,
            "fee": 0.00088,
            "totalConsideration": 0.00968,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1528354656926
        },
        {
            "transactionID": 10100000046609,
            "orderID": 10100000030912,
            "market": "ETH",
            "currency": "BCH",
            "price": 0.0008,
            "amount": 11,
            "fee": 0.00088,
            "totalConsideration": 0.00968,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1528354382338
        },
        {
            "transactionID": 10100000046591,
            "orderID": 10100000030830,
            "market": "ETH",
            "currency": "BCH",
            "price": 0.0008,
            "amount": 1,
            "fee": 0.00008,
            "totalConsideration": 0.00088,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1528337226919
        },
        {
            "transactionID": 10100000029950,
            "orderID": 10100000021826,
            "market": "BTC",
            "currency": "ETH",
            "price": 0.077845,
            "amount": 0.1,
            "fee": 0.00077845,
            "totalConsideration": 0.00856295,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1527672213108
        },
        {
            "transactionID": 10100000029948,
            "orderID": 10100000021825,
            "market": "BTC",
            "currency": "ETH",
            "price": 0.077845,
            "amount": 0.1,
            "fee": 0.00077845,
            "totalConsideration": 0.00856295,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1527672213108
        }
    ]
}
```
