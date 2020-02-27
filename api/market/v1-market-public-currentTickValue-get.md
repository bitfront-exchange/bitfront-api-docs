# Tick values

Retrieves the current tick values for the given coin pair. <br/>
The tick values include bid, ask, last prices, 24 hour volume, and others.

> **Note**
>
> This API can be used without API KEY.

## Endpoint URI

```
GET https://openapi.bitfront.me/v1/market/public/currentTickValue?coinPair={coinPair}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `coinPair` |The target cryptocurrencies. <br/>A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'. <br/>For example, BCH.ETH means buying or selling BCH with ETH. | String | query | √ |

## Response

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `timezone` |The time standard for the `responseTime`. It is always "UTC".|String|O|
| `responseTime` |The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC.|Long|O|
| `statusCode` |The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).|Integer|O|
| `statusMessage` |The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).|String|O|
| `responseData` |See the reference object.|[responseData](#responsedata)| |

### responseData

  - Type: object

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `bid` |The bid tick value|Double|O|
| `ask` |The ask tick value|Double|O|
| `last` |The last tick value|Double|O|
| `volume` |24 hour volume|Double|O|
| `open` |The open price in the last 24 hours|Double|O|
| `close` |The close price in the last 24 hours|Double|O|
| `high` |The highest price in the last 24 hours|Double|O|
| `low` |The lowest price in the last 24 hours|Double|O|

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1536567278026,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "bid": 0.400006,
        "ask": 0.400009,
        "last": 0.400006,
        "volume": 0.000800015,
        "open": 0.400009,
        "close": 0.400006,
        "high": 0.400009,
        "low": 0.400006
    }
}
```
