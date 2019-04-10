# Limit order

지정한 조건으로 지정가 주문을 합니다.<br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.

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

주문할 [coin pair](../../5_Terms.md#coin-pair).<br/>
[Currency](#currency-for-coin-trading)와 [Market](#market-for-coin-trading)을 점('.')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 "BCH.ETH"은 ETH으로 BCH를 거래한다는 의미입니다.

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

주문할 최대 혹은 최소 양. 0보다 커야 합니다.

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

주문할 최고가 혹은 최저가. 0보다 커야 합니다.

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

주문 방향. 다음 중 하나여야 합니다.<br/>
\- "BUY": 사기<br/>
\- "SELL": 팔기

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
|---|---|---|---|---|| `coinPair` |  주문할 [coin pair](../../5_Terms.md#coin-pair).<br/>
[Currency](#currency-for-coin-trading)와 [Market](#market-for-coin-trading)을 점(\'.\')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 \"BCH.ETH\"은 ETH으로 BCH를 거래한다는 의미입니다. | <span class="nowrap">String</span> | body |  O  || `quantity` |  주문할 최대 혹은 최소 양. 0보다 커야 합니다. | <span class="nowrap">Double</span> | body |  O  || `price` |  주문할 최고가 혹은 최저가. 0보다 커야 합니다. | <span class="nowrap">Double</span> | body |  O  || `orderSide` |  주문 방향. 다음 중 하나여야 합니다.<br/>
- \"BUY\": 사기<br/>
- \"SELL\": 팔기 | <span class="nowrap">String</span> | body |  O  | -->

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

결과 상태 코드. [`StatusCode` 정의](../../1_Overview.md#statuscode-정의)를 참고하십시오.

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

결과의 상세 메시지. [`StatusCode` 정의](../../1_Overview.md#statuscode-정의)를 참고하십시오.

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

`orderID`

</td>

<td>

주문의 ID. 주문의 상세 정보를 확인하거나 취소할 때 사용할 수 있습니다.

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

주문 요청 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

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
