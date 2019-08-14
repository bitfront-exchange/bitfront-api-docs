# Open orders

Retrieves all your open orders for the given currency or market. Open orders will be listed as defined by the query parameter `max`. When the `max` value is not assigned, it will list up to maximum of 100 open orders in a descending order of order placement date.<br/>

> **Note**<br/>
> Even if no parameter is indicated as 'required', it should have the value of either `market` or `currency` parameters.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/trade/openOrders?market={market}&currency={currency}&max={max}

## Request parameters

<table>

<colgroup>

<col style="width: 12%">

<col style="width: 36%">

<col style="width: 12%">

<col style="width: 15%">

<col style="width: 25%">

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

<strong>Loc.</strong>

</th>

<th style="text-align: center;">

<strong>Required</strong>

</th>

</tr>

</thead>

<tbody>

<tr>

<td>

`market`

</td>

<td>

A [coin code](/5_Terms.md#coin-code) of the [Market](/5_Terms.md#market-for-coin-trading).<br/>
For example, BCH for Bitcoin Cash.

</td>

<td style="text-align: center;">

<span class="nowrap">String</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`currency`

</td>

<td>

A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading).<br/>
For example, ETH for Ethereum.

</td>

<td style="text-align: center;">

<span class="nowrap">String</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`max`

</td>

<td>

Total number of open orders to retrieve. You can enter between 1 and 100. The default is 100.

</td>

<td style="text-align: center;">

<span class="nowrap">Integer</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

 

</td>

</tr>

</tbody>

</table>

<!-- | Name | Description | Type | Loc. | Required |
|---|---|---|---|---|| `market` |  A [coin code](/5_Terms.md#coin-code) of the [Market](/5_Terms.md#market-for-coin-trading).<br/>
For example, BCH for Bitcoin Cash. | <span class="nowrap">String</span> | query |     || `currency` |  A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading).<br/>
For example, ETH for Ethereum. | <span class="nowrap">String</span> | query |     || `max` |  Total number of open orders to retrieve. You can enter between 1 and 100. The default is 100. | <span class="nowrap">Integer</span> | query |     | -->

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

The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).

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

The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).

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

Array of [openOrder](#openorder)

### openOrder

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

`orderID`

</td>

<td>

The order ID

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`market`

</td>

<td>

A [coin code](/5_Terms.md#coin-code) of the [Market](/5_Terms.md#market-for-coin-trading)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`currency`

</td>

<td>

A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`orderSide`

</td>

<td>

A side of the order. It is one of the following:<br/>
\- "BUY": buy side<br/>
\- "SELL": sell side

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`requestAmount`

</td>

<td>

The amount requested

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`remainAmount`

</td>

<td>

The amount that are not filled or cancelled

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`price`

</td>

<td>

The limit price

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`status`

</td>

<td>

The status of the open order. It is one of the following:<br/>
\- "CREATE": The order is created.<br/>
\- "REQUEST": The order is requested to the order book.<br/>
\- "PROCESS": The order is partially or fully canceled.<br/>
\- "COMPLETE": The order is [completed](/5_Terms.md#completed-order). (including cancellation)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`createAt`

</td>

<td>

The time when the order is created.<br/>
It is in milliseconds since Unix Epoch in UTC.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`completedAt`

</td>

<td>

The time when the order is [completed](/5_Terms.md#completed-order). It is in milliseconds since Unix Epoch in UTC.<br/>
If the order is not yet completed, it is 0.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

</tbody>

</table>

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1530249666098,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": [
      {
          "orderID": 10000000033595,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100845,
          "requestAmount": 169,
          "remainAmount": 19,
          "status": "PROCESS",
          "createdAt": 1528998214282,
          "completedAt": 0
      },
      {
          "orderID": 10000000033568,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100838,
          "requestAmount": 145,
          "remainAmount": 36,
          "status": "PROCESS",
          "createdAt": 1528998142757,
          "completedAt": 0
      },
      {
          "orderID": 10000000029692,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100916,
          "requestAmount": 142,
          "remainAmount": 142,
          "status": "REQUEST",
          "createdAt": 1528915974502,
          "completedAt": 0
      },
      {
          "orderID": 10000000029679,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100916,
          "requestAmount": 141,
          "remainAmount": 141,
          "status": "REQUEST",
          "createdAt": 1528915954323,
          "completedAt": 0
      },
      {
          "orderID": 10000000029675,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100916,
          "requestAmount": 166,
          "remainAmount": 166,
          "status": "REQUEST",
          "createdAt": 1528915949534,
          "completedAt": 0
      },
      {
          "orderID": 10000000029480,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100918,
          "requestAmount": 129,
          "remainAmount": 129,
          "status": "REQUEST",
          "createdAt": 1528915489951,
          "completedAt": 0
      },
      {
          "orderID": 10000000029417,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100918,
          "requestAmount": 128,
          "remainAmount": 128,
          "status": "REQUEST",
          "createdAt": 1528915317441,
          "completedAt": 0
      },
      {
          "orderID": 10000000029299,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100917,
          "requestAmount": 116,
          "remainAmount": 116,
          "status": "REQUEST",
          "createdAt": 1528915000251,
          "completedAt": 0
      },
      {
          "orderID": 10000000022596,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100831,
          "requestAmount": 117,
          "remainAmount": 65,
          "status": "PROCESS",
          "createdAt": 1528712511367,
          "completedAt": 0
      },
      {
          "orderID": 10000000022381,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100824,
          "requestAmount": 111,
          "remainAmount": 76,
          "status": "PROCESS",
          "createdAt": 1528712049122,
          "completedAt": 0
      },
      {
          "orderID": 10000000022350,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100823,
          "requestAmount": 153,
          "remainAmount": 52,
          "status": "PROCESS",
          "createdAt": 1528711984127,
          "completedAt": 0
      },
      {
          "orderID": 10000000022126,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100815,
          "requestAmount": 176,
          "remainAmount": 51,
          "status": "PROCESS",
          "createdAt": 1528711566057,
          "completedAt": 0
      },
      {
          "orderID": 10000000021962,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100808,
          "requestAmount": 177,
          "remainAmount": 50,
          "status": "PROCESS",
          "createdAt": 1528711240865,
          "completedAt": 0
      },
      {
          "orderID": 10000000021891,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100805,
          "requestAmount": 135,
          "remainAmount": 64,
          "status": "PROCESS",
          "createdAt": 1528711103117,
          "completedAt": 0
      },
      {
          "orderID": 10000000021826,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100802,
          "requestAmount": 147,
          "remainAmount": 48,
          "status": "PROCESS",
          "createdAt": 1528710978840,
          "completedAt": 0
      }]
}
```

<p/>
