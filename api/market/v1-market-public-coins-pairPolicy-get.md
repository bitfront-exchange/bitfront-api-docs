# Market coin pair policy

Shows the latest data on BITFRONT's coin pairs

> **Note**
>
> This API can be used without API KEY.

## Endpoint URI

```
GET https://openapi.bitfront.me/v1/market/public/coins/pairPolicy
```

## Request parameters

None

## Response

| Name            | Description                                                                                                | Type                          | Included |
| --------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime`  | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O        |
| `statusCode`    | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | Integer                       | O        |
| `statusMessage` | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String                        | O        |
| `responseData`  | See the reference object. | [responseData](#responsedata) |          |

### responseData

  - Type: array

List of the latest data on BITFRONT's coin pairs

Array of [pairList](#pairlist)

### pairList

  - Type: object

| Name | Description | Type    | Included |
| ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | -------- |
| `marketType` | [Market](/5_Terms.md#market-for-coin-trading) type. Displayed as [coin code](/5_Terms.md#coin-code). e. g. Bitcoin as "BTC" and Ethereum as "ETH" | String  | O        |
| `coinType`   | [Currency](/5_Terms.md#currency-for-coin-trading) type. Displayed as [coin code](/5_Terms.md#coin-code). e. g. Bitcoin as "BTC" and Ethereum as "ETH"    | String  | O        |
| `displayNameOfCoinInformation` | Display name of [Currency](/5_Terms.md#currency-for-coin-trading) | String  | O        |
| `coinPairType` | [Coin-pair](/5_Terms.md#coin-pair) type. String concatenation of `marketType` and `coinType` with a dot (.)                                              | String  | O        |
| `minTradeAmount` | minimum transaction amount | Double  | O        |
| `maxTradeAmount` | maximum transaction amount | Double  | O        |
| `minTradeVolume` | minimum transaction volume | Double  | O        |
| `maxTradeVolume` | maximum transaction volume | Double  | O        |
| `tradeMakerFeeRate` | Maker fees, expressed as a percentage (%) of the total transaction volume. | Double  | O        |
| `tradeTakerFeeRate` | Taker fees, expressed as a percentage (%) of the total transaction volume. | Double  | O        |
| `tradeFeeUnit` | Cryptocurrency with which the fee is paid | String  | O        |
| `minPrice` | Minimum offer for transaction. e. g. As for BTC.ETH, minPrice is the minimum BTC offered to trade 1 ETH. <br/>For 7th decimal place and further, it is expressed as [exponential notation](https://en.wikipedia.org/wiki/Scientific_notation#E-notation). | Double | O       |
| `minPriceUnit` | Cryptocurrency in which the minimum offer is made for `minPrice` | String  | O        |
| `minAmountDecimal` | Effective decimal place for the transaction amount. i. e. i. e. If `minAmountDecimal` is 2, the amount can only be input up to the second decimal place. | Double  | O        |
| `minPriceDecimal` | Effective decimal place for the price. i. e. If `minPriceDecimal` is 8, the price can only be input up to the 8th decimal place.                         | Double  | O        |
| `trade` | Whether a trade is possible or note | Boolean | O        |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1553067063052,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "marketType": "BTC",
            "coinType": "AION",
            "displayNameOfCoinInformation": "Aion",
            "coinPairType": "BTC.AION",
            "tradeMinAmount": 0.01,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 0.001,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "BTC",
            "minPrice": 0.000001,
            "minPriceUnit": "BTC",
            "minAmountDecimal": 2,
            "minPriceDecimal": 6,
            "trade": true
        },
        {
            "marketType": "ETH",
            "coinType": "BTM",
            "displayNameOfCoinInformation": "Bytom",
            "coinPairType": "ETH.BTM",
            "tradeMinAmount": 1,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 0.01,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "ETH",
            "minPrice": 1e-8,
            "minPriceUnit": "ETH",
            "minAmountDecimal": 0,
            "minPriceDecimal": 8,
            "trade": false
        },
        {
            "marketType": "USDT",
            "coinType": "BCH",
            "displayNameOfCoinInformation": "Bitcoin Cash",
            "coinPairType": "USDT.BCH",
            "tradeMinAmount": 0.001,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 10,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "USDT",
            "minPrice": 0.01,
            "minPriceUnit": "USDT",
            "minAmountDecimal": 3,
            "minPriceDecimal": 2,
            "trade": true
        },
        //...so on...
    ]
}
```
