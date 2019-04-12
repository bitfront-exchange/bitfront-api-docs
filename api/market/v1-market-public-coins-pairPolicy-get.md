# Market coin pair policy

Shows the latest data on BITBOX's coin pairs<br/>

> **Note**<br/>
> Only `X-API-Key` in the header parameter is needed.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/market/public/coins/pairPolicy

## Request parameters

None

## Response

<table>

<thead>

<tr class="header">

<th>

<strong>Name</strong>

</th>

<th>

<strong>Description</strong>

</th>

<th style="text-align: center;">

<strong>Type</strong>

</th>

<th style="text-align: center;">

<strong>Included</strong>

</th>

</tr>

</thead>

<tbody>

<tr>

<td>

`timezone`

</td>

<td>

The time standard for the `responseTime`. It is always "UTC".

</td>

<td style="text-align: center;">

<span class="nowrap"> String </span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`responseTime`

</td>

<td>

The time when responded.<br/>
It is a timestamp in milliseconds since Unix Epoch in UTC.

</td>

<td style="text-align: center;">

<span class="nowrap"> Long </span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`statusCode`

</td>

<td>

The result status code. See [`statusCode` definitions](../../1_Overview.md#statuscode-definitions).

</td>

<td style="text-align: center;">

<span class="nowrap"> Integer </span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`statusMessage`

</td>

<td>

The detailed message of the result. See [`statusCode` definitions](../../1_Overview.md#statuscode-definitions).

</td>

<td style="text-align: center;">

<span class="nowrap"> String </span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`responseData`

</td>

<td>

See the reference object.

</td>

<td style="text-align: center;">

[responseData](#responsedata)

</td>

<td style="text-align: center;">

</td>

</tr>

</tbody>

</table>

### responseData

  - Type:  array
    </p>
    List of the latest data on BITBOX's coin pairs

Array of [pairList](#pairlist)

### pairList

  - Type:  object
    </p>

<table>

<colgroup>

<col style="width: 12%">

<col style="width: 56%">

<col style="width: 12%">

<col style="width: 20%">

</colgroup>

<thead>

<tr class="header">

<th>

<strong>Name</strong>

</th>

<th>

<strong>Description</strong>

</th>

<th style="text-align: center;">

<strong>Type</strong>

</th>

<th style="text-align: center;">

<strong>Included</strong>

</th>

</tr>

</thead>

<tbody>

<tr>

<td>

`marketType`

</td>

<td>

[Market](../../5_Terms.md#market-for-coin-trading) type. Displayed as [coin code](../../5_Terms.md#coin-code). e. g. Bitcoin as "BTC" and Ethereum as "ETH"

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`coinType`

</td>

<td>

[Currency](../../5_Terms.md#currency-for-coin-trading) type. Displayed as [coin code](../../5_Terms.md#coin-code). e. g. Bitcoin as "BTC" and Ethereum as "ETH"

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`displayNameOfCoinInformation`

</td>

<td>

Display name of [Currency](../../5_Terms.md#currency-for-coin-trading)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`coinPairType`

</td>

<td>

[Coin-pair](../../5_Terms.md#coin-pair) type. String concatenation of `marketType` and `coinType` with a dot (.)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minTradeAmount`

</td>

<td>

minimum transaction amount

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`maxTradeAmount`

</td>

<td>

maximum transaction amount

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minTradeVolume`

</td>

<td>

minimum transaction volume

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`maxTradeVolume`

</td>

<td>

maximum transaction volume

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`tradeMakerFeeRate`

</td>

<td>

Maker fees, expressed as a percentage (%) of the total transaction volume.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`tradeTakerFeeRate`

</td>

<td>

Taker fees, expressed as a percentage (%) of the total transaction volume.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`tradeFeeUnit`

</td>

<td>

Cryptocurrency with which the fee is paid

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minPrice`

</td>

<td>

Minimum offer for transaction. e. g. As for BTC.ETH, minPrice is the minimum BTC offered to trade 1 ETH.<br/>
For 7th decimal place and further, it is expressed as [exponential notation](https://en.wikipedia.org/wiki/Scientific_notation#E-notation).

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minPriceUnit`

</td>

<td>

Cryptocurrency in which the minimum offer is made for `minPrice`

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minAmountDecimal`

</td>

<td>

Effective decimal place for the transaction amount. i. e. i. e. If `minAmountDecimal` is 2, the amount can only be input up to the second decimal place.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minPriceDecimal`

</td>

<td>

Effective decimal place for the price. i. e. If `minPriceDecimal` is 8, the price can only be input up to the 8th decimal place.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`trade`

</td>

<td>

Whether a trade is possible or note

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

O

</td>

</tr>

</tbody>

</table>

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

<p/>
