# Tick values

Retrieves the current tick values for the given coin pair.<br/>
The tick values include bid, ask, last prices, 24 hour volume, and others.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/market/public/currentTickValue?coinPair={coinPair}

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

The target cryptocurrencies.<br/>
A case-sensitive string literal for the [Currency](#currency) and the [Market](#market) separated by '.'.<br/>
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

</tbody>

</table>

<!-- | Name | Description | Type | Loc. | Required |
|---|---|---|---|---|| `coinPair` |  The target cryptocurrencies.<br/>
A case-sensitive string literal for the [Currency](#currency) and the [Market](#market) separated by \'.\'.<br/>
For example, BCH.ETH means buying or selling BCH with ETH. | <span class="nowrap">String</span> | query |  O  | -->

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

`bid`

</td>

<td>

The bid tick value

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

`ask`

</td>

<td>

The ask tick value

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

`last`

</td>

<td>

The last tick value

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

`volume`

</td>

<td>

24 hour volume

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

`open`

</td>

<td>

The open price in the last 24 hours

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

`close`

</td>

<td>

The close price in the last 24 hours

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

`high`

</td>

<td>

The highest price in the last 24 hours

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

`low`

</td>

<td>

The lowest price in the last 24 hours

</td>

<td style="text-align: center;">

Double

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
    "responseTime": 1536567278026,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "bid": 0.400006,
        "ask": 0.400009,
        "last": 0.400006,
        "volume": 0.000800015,
        "open": 0.400009,
        "close": 0.400006,
        "high": 0.400009,
        "low": 0.400006
    }
}
```

<p/>
