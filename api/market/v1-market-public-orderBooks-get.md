# Order book

Retrieves records for the given coin pair from the order book.<br/>

> **Note**<br/>
> Only `X-API-Key` in the header parameter is needed.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/market/public/orderBooks?coinPair={coinPair}&depth={depth}

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

`coinPair`

</td>

<td>

A case-sensitive string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading) and the [Market](../../5_Terms.md#market-for-coin-trading) separated by '.'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH.

</td>

<td style="text-align: center;">

<span class="nowrap">String</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`depth`

</td>

<td>

The book depth (the number of price levels available) to retrieve. It should be in the range of 1-1000, the default is 10.

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
|---|---|---|---|---|| `coinPair` |  A case-sensitive string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading) and the [Market](../../5_Terms.md#market-for-coin-trading) separated by \'.\'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH. | <span class="nowrap">String</span> | query |  O  || `depth` |  The book depth (the number of price levels available) to retrieve. It should be in the range of 1-1000, the default is 10. | <span class="nowrap">Integer</span> | query |     | -->

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

  - Type:  object
    </p>
    The order book including bid and ask.<br/>
    It forms as a key-list map; the key of the map can be "BID" or "ASK", and each item in the list has a price and an amount. See the detailed description.

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

`BID`

</td>

<td>

Array of [priceAmount](#priceamount). See the reference object.

</td>

<td style="text-align: center;">

array

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`ASK`

</td>

<td>

Array of [priceAmount](#priceamount). See the reference object.

</td>

<td style="text-align: center;">

array

</td>

<td style="text-align: center;">

 

</td>

</tr>

</tbody>

</table>

### priceAmount

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

`price`

</td>

<td>

The price of an order

</td>

<td style="text-align: center;">

double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`amount`

</td>

<td>

The amount of an order

</td>

<td style="text-align: center;">

double

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

<p/>
