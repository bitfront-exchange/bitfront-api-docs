# Coin transfer history

Retrieves your coin transfer history under the given conditions.<br/>
You can set the conditions through the query parameters. See the parameter descriptions.<br/>
`responseData.content` in the response will pass the result data, which are sorted in descending order of `responseData.content.date`.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/account/transactionHistory?currency={currency}&startTime={startTime}&endTime={endTime}&transferType={transferType}&page={page}&pageSize={pageSize}

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

`currency`

</td>

<td>

A string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading).<br/>
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

`startTime`

</td>

<td>

The earliest time of trades to retrieve. It is in milliseconds in UTC.

</td>

<td style="text-align: center;">

<span class="nowrap">Long</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`endTime`

</td>

<td>

The latest time of trades to retrieve. It is in milliseconds in UTC.

</td>

<td style="text-align: center;">

<span class="nowrap">Long</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`transferType`

</td>

<td>

The type of transfer. It should be empty or one of the following:<br/>
\- "WITHDRAW": retrieves the withdrawal records only.<br/>
\- "DEPOSIT": retrieve the deposit records only.<br/>
Omit it to retrieve both types of transfer.<br/>
Note that this parameter is not case sensitive.

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

`page`

</td>

<td>

The page number to retrieve.<br/>
The number starts at 0, and the default is 0.

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

`pageSize`

</td>

<td>

The number of records each page will display. The default is 20, and maximum is 1000.<br/>
\- If `page` is 0 and `pageSize` is 20, then this API will return 1st-20th records.<br/>
\- If `page` is 1 and `pageSize` is 20, then this API will return 21th-40th records.

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
|---|---|---|---|---|| `currency` |  A string literal for the [Currency](../../5_Terms.md#currency-for-coin-trading).<br/>
For example, BCH for Bitcoin Cash. | <span class="nowrap">String</span> | query |     || `startTime` |  The earliest time of trades to retrieve. It is in milliseconds in UTC. | <span class="nowrap">Long</span> | query |     || `endTime` |  The latest time of trades to retrieve. It is in milliseconds in UTC. | <span class="nowrap">Long</span> | query |     || `transferType` |  The type of transfer. It should be empty or one of the following:<br/>
- \"WITHDRAW\": retrieves the withdrawal records only.<br/>
- \"DEPOSIT\": retrieve the deposit records only.<br/>
Omit it to retrieve both types of transfer.<br/>
Note that this parameter is not case sensitive. | <span class="nowrap">String</span> | query |     || `page` |  The page number to retrieve.<br/>
The number starts at 0, and the default is 0. | <span class="nowrap">Integer</span> | query |     || `pageSize` |  The number of records each page will display. The default is 20, and maximum is 1000.<br/>
- If `page` is 0 and `pageSize` is 20, then this API will return 1st-20th records.<br/>
- If `page` is 1 and `pageSize` is 20, then this API will return 21th-40th records. | <span class="nowrap">Integer</span> | query |     | -->

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

`number`

</td>

<td>

The page number

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`size`

</td>

<td>

The size of the page

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`totalPages`

</td>

<td>

The number of pages

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`numberOfElements`

</td>

<td>

The number of elements in the page

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`totalElements`

</td>

<td>

The number of elements returned

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`previousPage`

</td>

<td>

The flag indicating whether it has a previous page

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`first`

</td>

<td>

The flag indicating whether it is the first page

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`nextPage`

</td>

<td>

The flag indicating whether it has a next page

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`last`

</td>

<td>

The flag indicating whether it is the last page

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`content`

</td>

<td>

See the reference object.

</td>

<td style="text-align: center;">

[content](#content)

</td>

<td style="text-align: center;">

 

</td>

</tr>

</tbody>

</table>

content

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

`date`

</td>

<td>

The time of the coin transfer. It is a timestamp in milliseconds since Unix Epoch in UTC.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`coinType`

</td>

<td>

A [coin code](../../5_Terms.md#coin-code) of the transferred coin

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`transferType`

</td>

<td>

The type of the coin transfer. It is one of the following:<br/>
\- "WITHDRAW": Withdrawal transfer<br/>
\- "DEPOSIT": Deposit transfer

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`amount`

</td>

<td>

The amount of the coin to transfer

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

The transfer fee

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`total`

</td>

<td>

`amount + fee`

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`address`

</td>

<td>

The target address

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`status`

</td>

<td>

The status of the coin transfer. It should be one of the following:<br/>
\- "REQUEST": The transfer is requested.<br/>
\- "PENDING": The transfer is pending.<br/>
\- "CONFIRM": The transfer is confirmed.<br/>
\- "FAIL": The transfer fails.<br/>
\- "CANCEL\_REQUEST": The transfer is requested for cancellation.<br/>
\- "CANCEL": The transfer is completely cancelled.<br/>
\- "CANCEL\_FAIL": The transfer is requested for cancellation but the cancellation fails.

</td>

<td style="text-align: center;">

String

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
    "responseTime": 1527658634583,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "number": 0,
        "size": 100,
        "totalPages": 1,
        "numberOfElements": 2,
        "totalElements": 2,
        "previousPage": false,
        "first": true,
        "nextPage": false,
        "last": true,
        "content": [
            {
                "date": 1525420991000,
                "coinType": "BTC",
                "transferType": "WITHDRAW",
                "amount": 0.5,
                "fee": 0,
                "total": 0.5,
                "address": "2N8V9g4Ezd5wFGmoNgJYy8YUuYUMYqnATWJ",
                "status": "CONFIRM"
            },
            {
                "date": 1525420983000,
                "coinType": "BTC",
                "transferType": "WITHDRAW",
                "amount": 0.5,
                "fee": 0,
                "total": 0.5,
                "address": "2N9rMM6SrSZ7Xspfqu1QMmTXVvYGm8KPjTu",
                "status": "CONFIRM"
            }
        ]
    }
}
```

<p/>
