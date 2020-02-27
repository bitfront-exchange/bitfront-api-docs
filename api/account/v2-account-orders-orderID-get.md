# Order information v2

Gets the detailed information of a single order. <br/>
You can check whether the order has been cancelled by using the following formula:

`filledAmount` + `remainAmount` < `initialRequestAmount`.

- If `filledAmount` + `remainAmount` < `initialRequestAmount`, <br/>
  it means `initialRequestAmount` - (`filledAmount` + `remainAmount`) has been cancelled.
- If `filledAmount` + `remainAmount` = `initialRequestAmount`, <br/>
  nothing has been cancelled.

> **Note**
>
> This API returns "LN", LINK's ticker symbol, in the `currency` field when Currency of the order is LINK.

## Endpoint URI

```
GET https://openapi.bitfront.me/v2/account/orders/{orderID}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `orderID` | The ID of the order to get. You can get the ID whenever you place an order or retrieve your order list. | Long | path | √ |

## Response

| Name                                                       | Description                                                                                                | Type                          | Included |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`     | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime` | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O                             |
| `statusCode`   | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).    | Integer | O        |
| `statusMessage` | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String | O        |
| `responseData` | See the reference object. | [responseData](#responsedata) |          |

### responseData

  - Type: object

| Name        | Description                                                                                   | Type   | Included |
| ----------- | --------------------------------------------------------------------------------------------- | ------ | -------- |
| `orderID`   | The ID of the order                                                                           | Long   |          |
| `market`    | A [coin code](/5_Terms.md#coin-code) of the [Market](/5_Terms.md#market-for-coin-trading)     | String |          |
| `currency`  | A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading) | String |          |
| `orderType` | A type of the order. It is one of the following: <br/>- "MARKET": Market order <br/>- "LIMIT": Limit order <br/>- "STOPLIMIT": Stop-Limit order | String | |
| `orderSide` | A side of the order. It is one of the following: <br/>- "BUY": buy side <br/>- "SELL": sell side | String | |
| `price` | The limit price | Double| |
| `stopPrice` | The price at which the limit order is triggered. It is included only if `orderType` is "STOPLIMIT". | Double | |
| `initialRequestAmount` |The amount requested for the first time|Double| |
| `requestAmount` |The amount after cancellation|Double| |
| `remainAmount` |The amount that are not filled or cancelled|Double| |
| `filledAmount` |The amount filled|Double| |
| `reservedValue` |The reserved value for the order. <br/>For example, in "XRP" Currency and "BTC" Market, <br/>- When `orderSide` is "BUY", `reservedValue` in BTC is `requestAmount` * `price` * (1 + _fee rate_). <br/>- When `orderSide` is "SELL", `reservedValue` in XRP is `requestAmount`.|Double| |
| `reserveRemainingValue` |The reserved value for the remaining amount of the order. <br/>For example, in "XRP" Currency and "BTC" Market, <br/>- When `orderSide` is "BUY", `reserveRemainingValue` in BTC is `remainAmount` * `price` * (1 + _fee rate_). <br/>- When `orderSide` is "SELL", `reserveRemainingValue` in XRP is `remainAmount`.|Double| |
| `makerFeeRate` |Fee rate for a [Maker](/5_Terms.md#maker) order. <br/>Fee rate is not an absolute value. i. e. If the value is 0.001, this indicates that the fee rate is 0.1%. | Double | |
| `takerFeeRate` |Fee rate for a [Taker](/5_Terms.md#taker) order. <br/>Fee rate is not an absolute value. i. e. If the value is 0.001, this indicates that the fee rate is 0.1%. | Double | |
| `enableLnFee` |Whether to pay the fee with LN. <br/>Refer to the [Transaction fees](https://www.bitfront.me/fees/) for further information on how to pay the transaction fee with LN. | Boolean | |
| `makerLnFeeRate` |Fee rate for a [Maker](/5_Terms.md#maker) order when paying fees with LN. <br/>If `enableLnFee` is set as false, this value is '0'. | Double | |
| `takerLnFeeRate` |Fee rate for a [Taker](/5_Terms.md#taker) order when paying fees with LN. <br/>If `enableLnFee` is set as false, this value is '0'.|Double| |
| `status` |The status of the order. It is one of the following: <br/>- "CREATE": The order is created. <br/>- “PENDING”: A Stop-Limit order is created, but not executed yet. <br/>- "REQUEST": The order is registered to the order book. <br/>- "PROCESS": The order is partially cancelled or filled. <br/>- "COMPLETE": The order is [completed](/5_Terms.md#completed-order) (including cancellation).|String| |
| `createAt` |The time when the transaction is created. It is a timestamp in milliseconds since Unix Epoch in UTC.|Long| |
| `completedAt` |The time when the order is [completed](/5_Terms.md#completed-order). <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. <br/>If the order is not yet completed, it is 0.|Long| |
| `averageFillPrice` |The average price of filled amount|Double| |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1530167599398,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderID": 10100000042564,
        "market": "ETH",
        "currency": "XRP",
        "orderType": "STOPLIMIT",
        "orderSide": "BUY",
        "price": 0.00100915,
        "stopPrice": 0.00101,
        "initialRequestAmount": 200,
        "requestAmount": 200,
        "remainAmount": 0,
        "filledAmount": 200,
        "reservedValue": 0.222013,
        "reserveRemainingValue": 0,
        "makerFeeRate": 0.001,
        "takerFeeRate": 0.001,
        "enableLnFee": false,
        "makerLnFeeRate": 0,
        "takerLnFeeRate": 0,
        "status": "COMPLETE",
        "createdAt": 1528998406713,
        "completedAt": 1528998406907,
        "averageFillPrice": 0.00100915
    }
}
```
