# Order information

Gets the detailed information of a single order.<br/>
You can check whether the order has been cancelled by using the following formula:<br/>
`filledAmount` + `remainAmount` \< `initialRequestAmount`.<br/>

<ul>

<li>

If `filledAmount` + `remainAmount` \< `initialRequestAmount`,<br/> it means `initialRequestAmount` - (`filledAmount` + `remainAmount`) has been cancelled.

</li>

<li>

If `filledAmount` + `remainAmount` = `initialRequestAmount`,<br/> nothing has been cancelled.

</li>

</ul>

## Endpoint URI

    GET https://openapi.bitbox.me/v1/account/orders/{orderID}

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

`orderID`

</td>

<td>

The ID of the order to get. You can get the ID whenever you place an order or retrieve your order list.

</td>

<td style="text-align: center;">

<span class="nowrap">Long</span>

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
|---|---|---|---|---|| `orderID` |  The ID of the order to get. You can get the ID whenever you place an order or retrieve your order list. | <span class="nowrap">Long</span> | path |  O  | -->

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

The result status code. See [StatusCode definitions](#statuscode-definitions).

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

The detailed message of the result

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

The ID of the order

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

A [coin code](#coin-code) of the [Market](#market)

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

A [coin code](#coin-code) of the [Currency](#currency)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`orderType`

</td>

<td>

A type of the order. It is one of the following:<br/>
\- "MARKET": Market order<br/>
\- "LIMIT": Limit order

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

`price`

</td>

<td>

The limit price when `orderType` is "LIMIT"

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`initialRequestAmount`

</td>

<td>

The amount requested for the first time

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`requestAmount`

</td>

<td>

The amount after cancellation

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

`filledAmount`

</td>

<td>

The amount filled

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`reservedValue`

</td>

<td>

The reserved value for the order.<br/>
For example, in "XRP" Currency and "BTC" Market,<br/>
\- When `orderSide` is "BUY", `reservedValue` in BTC is `requestAmount` \* `price` \* (1 + `feeRate`).<br/>
\- When `orderSide` is "SELL", `reservedValue` in XRP is `requestAmount`.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`reserveRemainingValue`

</td>

<td>

The reserved value for the remaining amount of the order.<br/>
For example, in "XRP" Currency and "BTC" Market,<br/>
\- When `orderSide` is "BUY", `reserveRemainingValue` in BTC is `remainAmount` \* `price` \* (1 + `feeRate`).<br/>
\- When `orderSide` is "SELL", `reserveRemainingValue` in XRP is `remainAmount`.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`feeRate`

</td>

<td>

The rate of fee. It is not an absolute value.<br/>
For example, if `feeRate` is 0.1, it means 10%.

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

the status of the order. It is one of the following:<br/>
\- "CREATE": The order is created.<br/>
\- "REQUEST": The order is registered to the order book.<br/>
\- "PROCESS": The order is partially cancelled or filled.<br/>
\- "COMPLETE": The order is [completed](#completed-order) (including cancellation).

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

The time when the transaction is created. It is a timestamp in milliseconds since Unix Epoch in UTC.

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

The time when the order is [completed](../../5_Terms.md#completed-order).<br/>
It is a timestamp in milliseconds since Unix Epoch in UTC.<br/>
If the order is not yet completed, it is 0.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`averageFillPrice`

</td>

<td>

The average price of filled amount

</td>

<td style="text-align: center;">

Double

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
    "responseTime": 1530167599398,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderID": 10100000042564,
        "market": "ETH",
        "currency": "XRP",
        "orderType": "LIMIT",
        "orderSide": "BUY",
        "price": 0.00100915,
        "initialRequestAmount": 200,
        "requestAmount": 200,
        "remainAmount": 0,
        "filledAmount": 200,
        "reservedValue": 0.222013,
        "reserveRemainingValue": 0,
        "feeRate": 0.1,
        "status": "COMPLETE",
        "createdAt": 1528998406713,
        "completedAt": 1528998406907,
        "averageFillPrice": 0.00100915
    }
}
```

<p/>
