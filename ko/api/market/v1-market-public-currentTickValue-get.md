# Tick values

지정된 coin pair의 현재 tick 값을 조회합니다.<br/>
Bid, ask, last prices, 24시간 volume 및 24시간 내 시작가, 종가, 최대 가격, 최소 가격을 확인할 수 있습니다.<br/>

> **Note**<br/>
> 이 API는 헤더 파라미터에 `X-API-Key`만 전달하면 됩니다.

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

조회할 [coin pair](/5_Terms.md#coin-pair). [Currency](/5_Terms.md#currency-for-coin-trading)와 [Market](/5_Terms.md#market-for-coin-trading)을 점('.')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 "BCH.ETH"은 ETH으로 BCH를 거래한다는 의미입니다.

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
|---|---|---|---|---|| `coinPair` |  조회할 [coin pair](/5_Terms.md#coin-pair). [Currency](/5_Terms.md#currency-for-coin-trading)와 [Market](/5_Terms.md#market-for-coin-trading)을 점(\'.\')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 \"BCH.ETH\"은 ETH으로 BCH를 거래한다는 의미입니다. | <span class="nowrap">String</span> | query |  O  | -->

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

`responseTime`의 기준 시간. 항상 "UTC"입니다.

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

응답 시간. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

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

결과 상태 코드. [`StatusCode` 정의](/1_Overview.md#statuscode-정의)를 참고하십시오.

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

결과의 상세 메시지. [`StatusCode` 정의](/1_Overview.md#statuscode-정의)를 참고하십시오.

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

대상 객체 설명을 참고하십시오.

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

bid tick 값

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

ask tick 값

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

last tick 값

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

24시간 volume

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

24시간 내 시작가

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

24시간 내 종가

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

24시간 내 최대 가격

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

24시간 내 최소 가격

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
