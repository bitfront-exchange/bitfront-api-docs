# User trade history v2

Retrieves your recent trade records under the given conditions.<br/>
You can set the conditions through the query parameters. See the parameter descriptions.<br/>

> **Note**<br/>
> \- The maximum period for the date condition is 30 days. In other words, the number of days from `startTime` to `endTime` MUST NOT exceed 30.<br/>
> \- The result records will be stored in `responseData` and sorted in descending order of `responseData[].createAt`.

## Endpoint URI

    GET https://openapi.bitbox.me/v2/account/tradeHistory?coinPair={coinPair}&startTime={startTime}&endTime={endTime}&max={max}

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

The cryptocurrencies for the trades to retrieve.<br/>
A case-sensitive string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading) and the [Market](../../5_Terms.md#market-for-coin-trading) separated by '.'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH.<br/>
If it is empty, this API will return all coin pair trades.

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

`startTime`

</td>

<td>

The start time of the period condition for retrieving trade records. It is a timestamp in milliseconds since Unix Epoch in UTC.

</td>

<td style="text-align: center;">

<span class="nowrap">Integer</span>

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

`endTime`

</td>

<td>

The end time of the period condition for retrieving trade records. It is a timestamp in milliseconds since Unix Epoch in UTC.<br/>
If unassigned, the default value of `startTime`+24hrs is used.

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

<tr>

<td>

`max`

</td>

<td>

The maximum number of trades to retrieve. It should be in the range of 1-100. The default is 100.<br/>
Note that the returned records can be less than `max` because the API returns only the trades that had been made in the given period.

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
|---|---|---|---|---|| `coinPair` |  The cryptocurrencies for the trades to retrieve.<br/>
A case-sensitive string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading) and the [Market](../../5_Terms.md#market-for-coin-trading) separated by \'.\'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH.<br/>
If it is empty, this API will return all coin pair trades. | <span class="nowrap">String</span> | query |     || `startTime` |  The start time of the period condition for retrieving trade records. It is a timestamp in milliseconds since Unix Epoch in UTC. | <span class="nowrap">Integer</span> | query |  O  || `endTime` |  The end time of the period condition for retrieving trade records. It is a timestamp in milliseconds since Unix Epoch in UTC.<br/>
If unassigned, the default value of `startTime`+24hrs is used. | <span class="nowrap">Integer</span> | query |     || `max` |  The maximum number of trades to retrieve. It should be in the range of 1-100. The default is 100.<br/>
Note that the returned records can be less than `max` because the API returns only the trades that had been made in the given period. | <span class="nowrap">Integer</span> | query |     | -->

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
    A list of the trade records

Array of [history](#history)

### history

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

`transactionID`

</td>

<td>

The ID of a transaction

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`orderID`

</td>

<td>

The ID of an order

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

A [coin code](../../5_Terms.md#coin-code) of the [Market](../../5_Terms.md#market-for-coin-trading)

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

A [coin code](../../5_Terms.md#coin-code) of the [Currency](../../5_Terms.md#currency-for-coin-trading)

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

A unit price

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`amount`

</td>

<td>

An amount

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`fee`

</td>

<td>

A trading fee

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`totalConsideration`

</td>

<td>

price \* amount + fee\`

</td>

<td style="text-align: center;">

Double

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

`fillType`

</td>

<td>

A type of fill. It is one of the following:<br/>
\- "FULL": The transaction is fully filled<br/>
\- "PARTIAL": The transaction is partially filled

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

</tbody>

</table>

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1528359043142,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "transactionID": 10100000046610,
            "orderID": 10100000030913,
            "market": "ETH",
            "currency": "BCH",
            "price": 0.0008,
            "amount": 11,
            "fee": 0.00088,
            "totalConsideration": 0.00968,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1528354656926
        },
        {
            "transactionID": 10100000046609,
            "orderID": 10100000030912,
            "market": "ETH",
            "currency": "BCH",
            "price": 0.0008,
            "amount": 11,
            "fee": 0.00088,
            "totalConsideration": 0.00968,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1528354382338
        },
        {
            "transactionID": 10100000046591,
            "orderID": 10100000030830,
            "market": "ETH",
            "currency": "BCH",
            "price": 0.0008,
            "amount": 1,
            "fee": 0.00008,
            "totalConsideration": 0.00088,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1528337226919
        },
        {
            "transactionID": 10100000029950,
            "orderID": 10100000021826,
            "market": "BTC",
            "currency": "ETH",
            "price": 0.077845,
            "amount": 0.1,
            "fee": 0.00077845,
            "totalConsideration": 0.00856295,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1527672213108
        },
        {
            "transactionID": 10100000029948,
            "orderID": 10100000021825,
            "market": "BTC",
            "currency": "ETH",
            "price": 0.077845,
            "amount": 0.1,
            "fee": 0.00077845,
            "totalConsideration": 0.00856295,
            "orderSide": "BUY",
            "fillType": "FULL",
            "createdAt": 1527672213108
        }
    ]
}
```

<p/>
