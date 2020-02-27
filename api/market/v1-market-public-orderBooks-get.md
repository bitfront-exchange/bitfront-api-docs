# Order book

Retrieves records for the given coin pair from the order book.

> **Note**
>
> This API can be used without API KEY.

## Endpoint URI

```
GET https://openapi.bitfront.me/v1/market/public/orderBooks?coinPair={coinPair}&depth={depth}
```

## Request parameters

| Name | Description | Type | Loc. | Required |
|--- |--- |--- |--- |--- |
| `coinPair` |A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'. <br/>For example, BCH.ETH means buying or selling BCH with ETH.|String|query|O|
| `depth` |The book depth (the number of price levels available) to retrieve. It should be in the range of 1-1000, the default is 100.|Integer|query| |

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

The order book including bid and ask. <br/>
It forms as a key-list map; the key of the map can be "BID" or "ASK", and each item in the list has a price and an amount. See the detailed description.

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `BID` |Array of [priceAmount](#priceamount). See the reference object.|array| |
| `ASK` |Array of [priceAmount](#priceamount). See the reference object.|array| |

### priceAmount

  - Type: object

| Name | Description | Type | Included |
|--- |--- |--- |--- |
| `price` |The price of an order|double| |
| `amount` |The amount of an order|double| |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1525078219216,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": {
      "BID": [
          {
              "price": 2748.72327228786,
              "amount": 2.23394525
          },
          {
              "price": 2746.69921216344,
              "amount": 0.9357132
          },
          {
              "price": 2746.6714729717582,
              "amount": 2.66085382
          },
          {
              "price": 2746.6598167849634,
              "amount": 1.53825317
          },
          {
              "price": 2746.648512115077,
              "amount": 6.38919104
          }
      ],
      "ASK": [
          {
              "price": 2759.0795123971097,
              "amount": 0.66742494
          },
          {
              "price": 2759.0790474341684,
              "amount": 2.42865008
          },
          {
              "price": 2759.057958916535,
              "amount": 3.47240736
          },
          {
              "price": 2759.0549591332588,
              "amount": 5.11662824
          },
          {
              "price": 2759.0492733250644,
              "amount": 6.18008926
          }
      ]
  }
}
```
