# Open orders

지정한 [currency](/5_Terms.md#currency-for-coin-trading)와 [market](/5_Terms.md#market-for-coin-trading)의 열린 주문을 모두 조회합니다. 파라미터 `max` 개수만큼 반환하며, `max`를 지정하지 않으면 최대 100개만 반환합니다. 조회된 주문은 주문 날짜 기준 내림차순으로 정렬됩니다.<br/>

> **Note**<br/>
> 필수로 표기된 파라미터는 없지만, `market`과 `currency` 파라미터 중 하나는 반드시 입력해야 합니다.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/trade/openOrders?market={market}&currency={currency}&max={max}

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

`market`

</td>

<td>

조회할 [Market](/5_Terms.md#market-for-coin-trading)의 [coin code](/5_Terms.md#coin-code).<br/>
예를 들어 비트코인 캐시는 "BCH"가 됩니다.

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

`currency`

</td>

<td>

조회할 [Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code).<br/>
예를 들어 이더리움은 "ETH"가 됩니다.

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

`max`

</td>

<td>

조회할 열린 주문의 총 개수. 1에서 100까지 입력할 수 있습니다. 기본값은 100입니다.

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
|---|---|---|---|---|| `market` |  조회할 [Market](/5_Terms.md#market-for-coin-trading)의 [coin code](/5_Terms.md#coin-code).<br/>
예를 들어 비트코인 캐시는 \"BCH\"가 됩니다. | <span class="nowrap">String</span> | query |     || `currency` |  조회할 [Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code).<br/>
예를 들어 이더리움은 \"ETH\"가 됩니다. | <span class="nowrap">String</span> | query |     || `max` |  조회할 열린 주문의 총 개수. 1에서 100까지 입력할 수 있습니다. 기본값은 100입니다. | <span class="nowrap">Integer</span> | query |     | -->

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

  - Type:  array
    </p>

[openOrder](#openorder)
객체의 배열입니다.

### openOrder

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

주문의 ID

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

[Market](/5_Terms.md#market-for-coin-trading)의 [coin code](/5_Terms.md#coin-code)

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

[Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code)

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

`requestAmount`

</td>

<td>

대상
객체 설명을 참고하십시오.

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

대상
객체 설명을 참고하십시오.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`price`

</td>

<td>

대상
객체 설명을 참고하십시오.

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

열린 주문의 상태. 다음 중 하나입니다.<br/>
\- "CREATE": 주문이 생성됨<br/>
\- "REQUEST": 주문이 주문장에 요청됨<br/>
\- "PROCESS": 주문이 부분적으로 취소되거나 체결됨<br/>
\- "COMPLETE": 주문이 [완료](/5_Terms.md#completed-order)됨 (취소된 것도 포함).

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

주문 생성 시각.<br/>
밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

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

주문이 [완료](/5_Terms.md#completed-order)된 시각.<br/>
밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.<br/>
주문이 완료되지 않았다면 이 값은 0입니다.

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
  "responseTime": 1530249666098,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": [
      {
          "orderID": 10000000033595,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100845,
          "requestAmount": 169,
          "remainAmount": 19,
          "status": "PROCESS",
          "createdAt": 1528998214282,
          "completedAt": 0
      },
      {
          "orderID": 10000000033568,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100838,
          "requestAmount": 145,
          "remainAmount": 36,
          "status": "PROCESS",
          "createdAt": 1528998142757,
          "completedAt": 0
      },
      {
          "orderID": 10000000029692,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100916,
          "requestAmount": 142,
          "remainAmount": 142,
          "status": "REQUEST",
          "createdAt": 1528915974502,
          "completedAt": 0
      },
      {
          "orderID": 10000000029679,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100916,
          "requestAmount": 141,
          "remainAmount": 141,
          "status": "REQUEST",
          "createdAt": 1528915954323,
          "completedAt": 0
      },
      {
          "orderID": 10000000029675,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100916,
          "requestAmount": 166,
          "remainAmount": 166,
          "status": "REQUEST",
          "createdAt": 1528915949534,
          "completedAt": 0
      },
      {
          "orderID": 10000000029480,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100918,
          "requestAmount": 129,
          "remainAmount": 129,
          "status": "REQUEST",
          "createdAt": 1528915489951,
          "completedAt": 0
      },
      {
          "orderID": 10000000029417,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100918,
          "requestAmount": 128,
          "remainAmount": 128,
          "status": "REQUEST",
          "createdAt": 1528915317441,
          "completedAt": 0
      },
      {
          "orderID": 10000000029299,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "SELL",
          "price": 0.00100917,
          "requestAmount": 116,
          "remainAmount": 116,
          "status": "REQUEST",
          "createdAt": 1528915000251,
          "completedAt": 0
      },
      {
          "orderID": 10000000022596,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100831,
          "requestAmount": 117,
          "remainAmount": 65,
          "status": "PROCESS",
          "createdAt": 1528712511367,
          "completedAt": 0
      },
      {
          "orderID": 10000000022381,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100824,
          "requestAmount": 111,
          "remainAmount": 76,
          "status": "PROCESS",
          "createdAt": 1528712049122,
          "completedAt": 0
      },
      {
          "orderID": 10000000022350,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100823,
          "requestAmount": 153,
          "remainAmount": 52,
          "status": "PROCESS",
          "createdAt": 1528711984127,
          "completedAt": 0
      },
      {
          "orderID": 10000000022126,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100815,
          "requestAmount": 176,
          "remainAmount": 51,
          "status": "PROCESS",
          "createdAt": 1528711566057,
          "completedAt": 0
      },
      {
          "orderID": 10000000021962,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100808,
          "requestAmount": 177,
          "remainAmount": 50,
          "status": "PROCESS",
          "createdAt": 1528711240865,
          "completedAt": 0
      },
      {
          "orderID": 10000000021891,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100805,
          "requestAmount": 135,
          "remainAmount": 64,
          "status": "PROCESS",
          "createdAt": 1528711103117,
          "completedAt": 0
      },
      {
          "orderID": 10000000021826,
          "market": "ETH",
          "currency": "XRP",
          "orderSide": "BUY",
          "price": 0.00100802,
          "requestAmount": 147,
          "remainAmount": 48,
          "status": "PROCESS",
          "createdAt": 1528710978840,
          "completedAt": 0
      }]
}
```

<p/>
