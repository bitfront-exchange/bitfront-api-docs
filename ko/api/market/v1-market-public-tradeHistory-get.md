# Market trade history

조건에 따라 BITBOX 내 최근 거래 내역을 조회합니다.<br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.<br/>

> **Note**<br/>
> \- 이 API는 헤더 파라미터에 `X-API-Key`만 전달하면 됩니다.<br/>
> \- 최근 3개월 이내의 내역만 제공합니다.<br/>
> \- 결과 내역은 `responseData`에 저장되며 `responseData[].createAt` 기준 내림차순으로 정렬됩니다.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/market/public/tradeHistory?coinPair={coinPair}&startTime={startTime}&endTime={endTime}&max={max}

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

조회할 [coin pair](../../5_Terms.md#coin-pair). [Currency](../../5_Terms.md#currency-for-coin-trading)와 [Market](../../5_Terms.md#market-for-coin-trading)을 점('.')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 "BCH.ETH"은 ETH으로 BCH를 거래한다는 의미입니다.

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

조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

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

`endTime`

</td>

<td>

조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

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

조회할 거래 내역 최대 개수. 1~100 사이여야 하며 기본값은 100입니다.<br/>
최근 3개월 이내의 내역만 제공하므로 실제 반환되는 개수는 `max`보다 적을 수 있습니다.

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
|---|---|---|---|---|| `coinPair` |  조회할 [coin pair](../../5_Terms.md#coin-pair). [Currency](../../5_Terms.md#currency-for-coin-trading)와 [Market](../../5_Terms.md#market-for-coin-trading)을 점(\'.\')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 \"BCH.ETH\"은 ETH으로 BCH를 거래한다는 의미입니다. | <span class="nowrap">String</span> | query |     || `startTime` |  조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | <span class="nowrap">Integer</span> | query |     || `endTime` |  조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | <span class="nowrap">Integer</span> | query |     || `max` |  조회할 거래 내역 최대 개수. 1\~100 사이여야 하며 기본값은 100입니다.<br/>
최근 3개월 이내의 내역만 제공하므로 실제 반환되는 개수는 `max`보다 적을 수 있습니다. | <span class="nowrap">Integer</span> | query |     | -->

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

  - Type:  array
    </p>
    BITBOX 내의 최근 거래 내역입니다.

[history](#history)
객체의 배열입니다.

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

트랜잭션의 ID

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

[Market](../../5_Terms.md#market-for-coin-trading)의 [coin code](../../5_Terms.md#coin-code)

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

[Currency](../../5_Terms.md#currency-for-coin-trading)의 [coin code](../../5_Terms.md#coin-code)

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

단위 가격

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

총수량

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`totalValue`

</td>

<td>

`amount` \* `price`

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

주문 방향. 다음 중 하나입니다.<br/>
\- "BUY": 사기<br/>
\- "SELL": 팔기

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

트랜잭션 생성 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

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
  "responseTime": 1528358968115,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": [
      {
          "transactionID": 10100000046610,
          "market": "ETH",
          "currency": "BCH",
          "price": 0.0008,
          "amount": 11,
          "totalValue": 0.0088,
          "orderSide": "BUY",
          "createdAt": 1528354656926
      },
      {
          "transactionID": 10100000046609,
          "market": "ETH",
          "currency": "BCH",
          "price": 0.0008,
          "amount": 11,
          "totalValue": 0.0088,
          "orderSide": "BUY",
          "createdAt": 1528354382338
      },
      {
          "transactionID": 10100000046606,
          "market": "BTC",
          "currency": "ETH",
          "price": 0.024001,
          "amount": 10,
          "totalValue": 0.24001,
          "orderSide": "SELL",
          "createdAt": 1528348471297
      },
      {
          "transactionID": 10100000046599,
          "market": "BTC",
          "currency": "BCH",
          "price": 0.158136,
          "amount": 4.982,
          "totalValue": 0.787833552,
          "orderSide": "SELL",
          "createdAt": 1528338502467
      },
      {
          "transactionID": 10100000046597,
          "market": "BTC",
          "currency": "BCH",
          "price": 0.158137,
          "amount": 0.02,
          "totalValue": 0.00316274,
          "orderSide": "SELL",
          "createdAt": 1528338502467
      }
  ]
}
```

<p/>
