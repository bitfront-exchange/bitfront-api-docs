# Limit order

Places a limit order with the given conditions.<br/>
You can set the conditions through the query parameters. See the parameter descriptions.

## Endpoint URI

    POST https://openapi.bitbox.me/v1/trade/limitOrders

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

A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by '.'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH.

</td>

<td style="text-align: center;">

<span class="nowrap">String</span>

</td>

<td style="text-align: center;">

<span class="nowrap">body<span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`quantity`

</td>

<td>

The maximum or minimum quantity to order. It should be greater than 0.

</td>

<td style="text-align: center;">

<span class="nowrap">Double</span>

</td>

<td style="text-align: center;">

<span class="nowrap">body<span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`price`

</td>

<td>

The maximum or minimum price to order. It should be greater than 0.

</td>

<td style="text-align: center;">

<span class="nowrap">Double</span>

</td>

<td style="text-align: center;">

<span class="nowrap">body<span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`orderSide`

</td>

<td>

The side of order. It should be one of the following:<br/>
\- "BUY": buy order<br/>
\- "SELL": sell order

</td>

<td style="text-align: center;">

<span class="nowrap">String</span>

</td>

<td style="text-align: center;">

<span class="nowrap">body<span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

</tbody>

</table>

<!-- | Name | Description | Type | Loc. | Required |
|---|---|---|---|---|| `coinPair` |  A case-sensitive string literal for the [Currency](/5_Terms.md#currency-for-coin-trading) and the [Market](/5_Terms.md#market-for-coin-trading) separated by \'.\'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH. | <span class="nowrap">String</span> | body |  O  || `quantity` |  The maximum or minimum quantity to order. It should be greater than 0. | <span class="nowrap">Double</span> | body |  O  || `price` |  The maximum or minimum price to order. It should be greater than 0. | <span class="nowrap">Double</span> | body |  O  || `orderSide` |  The side of order. It should be one of the following:<br/>
- \"BUY\": buy order<br/>
- \"SELL\": sell order | <span class="nowrap">String</span> | body |  O  | -->

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

The order ID. Use it to cancel or check the details of the order.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`requestAt`

</td>

<td>

The time when the order is requested. It is a timestamp in milliseconds since Unix Epoch in UTC.

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
  "responseTime": 1525079412,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": {
      "orderID": 10100000000565,
      "requestAt": 1525079412
  }
}
```

<p/>
