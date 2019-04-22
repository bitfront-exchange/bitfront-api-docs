# Cancellation of all open orders

Request to cancel your all open orders. It will returns the list of orders you requested to cancel.<br/>
For each order, if the order is partially filled, it only tries to cancel the remaining amount.<br/>

> **Caution**<br/>
> `statusCode` of 1000 means the cancellation is NOT successfully done BUT requested well.<br/>
> If you want to check whether the order has been cancelled, use [`/v1/account/orders/{orderID}`](../account/v1-account-orders-orderID-get.md#order-information).

## Endpoint URI

    DELETE https://openapi.bitbox.me/v1/trade/openOrders/{coinPair}

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

A [coin pair](../../5_Terms.md#coin-pair) for the orders to request to cancel.<br/>
A case-sensitive string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading) and the [Market](../../5_Terms.md#market-for-coin-trading) separated by '.'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH.

</td>

<td style="text-align: center;">

<span class="nowrap">String</span>

</td>

<td style="text-align: center;">

<span class="nowrap">path<span>

</td>

<td style="text-align: center;">

O

</td>

</tr>

</tbody>

</table>

<!-- | Name | Description | Type | Loc. | Required |
|---|---|---|---|---|| `coinPair` |  A [coin pair](../../5_Terms.md#coin-pair) for the orders to request to cancel.<br/>
A case-sensitive string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading) and the [Market](../../5_Terms.md#market-for-coin-trading) separated by \'.\'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH. | <span class="nowrap">String</span> | path |  O  | -->

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

`orderIDList`

</td>

<td>

Array of Long. the list of the order IDs

</td>

<td style="text-align: center;">

array

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
    "responseTime": 1525080718,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderIDList": [
            10100000000561,
            10100000000563,
            10100000000564,
            10100000000565
        ],
        "requestAt": 1525080718
    }
}
```

<p/>
