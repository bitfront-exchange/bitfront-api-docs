# Currency balance

Gets your account currency balance for the given currency.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/account/balances/{currency}

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

A [coin code](#coin-code) of the [Currency](#currency).<br/>
For example, BCH for Bitcoin Cash. (See [Trading pair policy](#trading-pair-policy).)

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
|---|---|---|---|---|| `currency` |  A [coin code](#coin-code) of the [Currency](#currency).<br/>
For example, BCH for Bitcoin Cash. (See [Trading pair policy](#trading-pair-policy).) | <span class="nowrap">String</span> | path |  O  | -->

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

`balance`

</td>

<td>

The total cryptocurrency balance

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`availableBalance`

</td>

<td>

The total cryptocurrency balance that can be used (unlocked)

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
    "responseTime": 1525239832135,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "currency": "ETH",
            "balance": 1000107794.9999858,
            "availableBalance": 1000107794.9999858
        }
    ]
}
```

<p/>
