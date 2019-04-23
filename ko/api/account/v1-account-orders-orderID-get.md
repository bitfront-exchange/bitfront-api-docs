# Order information

한 주문의 상세 정보를 가져옵니다.<br/>
다음 식을 사용하여 이 주문이 취소되었는지 확인할 수 있습니다.<br/>
`filledAmount` + `remainAmount` \< `initialRequestAmount`

<ul>

<li>

`filledAmount` + `remainAmount` \< `initialRequestAmount`이면,<br/> `initialRequestAmount` - (`filledAmount` + `remainAmount`) 만큼 취소되었다는 의미입니다.

</li>

<li>

`filledAmount` + `remainAmount` = `initialRequestAmount`이면,<br/> 취소된 것이 없다는 의미입니다.

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

가져올 주문의 ID. 주문 ID는 주문을 요청하거나 요청 목록을 가져올 때 확인할 수 있습니다.

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
|---|---|---|---|---|| `orderID` |  가져올 주문의 ID. 주문 ID는 주문을 요청하거나 요청 목록을 가져올 때 확인할 수 있습니다. | <span class="nowrap">Long</span> | path |  O  | -->

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

`orderType`

</td>

<td>

주문 타입. 다음 중 하나입니다.<br/>
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

`price`

</td>

<td>

`orderType`이 "LIMIT"일 때 제한 가격

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

처음 요청한 총수량

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

취소한 후의 총수량

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

체결되지도 않고 취소되지도 않은 총수량

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

체결된 총수량

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

주문의 예상 가치.<br/>
예를 들어 `currency`가 "XRP", `market`이 "BTC"일 때,<br/>
\- `orderSide`가 "BUY"이면, `reservedValue`는 BTC로<br/>
`requestAmount` \* `price` \* (1 + *fee rate*)입니다.<br/>
\- `orderSide`가 "SELL"이면, `reservedValue`는 XRP로<br/>
`requestAmount`입니다.

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

주문 내 남은 총수량 예상 가치.<br/>
예를 들어 `currency`가 "XRP", `market`이 "BTC"일 때,<br/>
\- `orderSide`가 "BUY"이면, `reserveRemainingValue`는 BTC로<br/>
`remainAmount` \* `price` \* (1 + *fee Rate*)입니다.<br/>
\- `orderSide`가 "SELL"이면, `reserveRemainingValue`는 XRP로<br/>
`remainAmount`입니다.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`makerFeeRate`

</td>

<td>

[Maker](../../5_Terms.md#maker) 주문에 대한 수수료 비율.<br/>
수수료는 절대값이 아닙니다. 예를 들어 이 값이 0.001이면 수수료 비율이 0.1%라는 의미입니다.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`takerFeeRate`

</td>

<td>

[Taker](../../5_Terms.md#taker) 주문에 대한 수수료 비율.<br/>
수수료는 절대값이 아닙니다. 예를 들어 이 값이 0.001이면 수수료 비율이 0.1%라는 의미입니다.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`enableLinkFee`

</td>

<td>

LINK로 거래 수수료 결제 여부.<br/>
LINK로 거래 수수료를 결제하는 방법에 관한 상세한 설명은 [Transaction fees](https://www.bitbox.me/fees/)를 참고하십시오.

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`makerLinkFeeRate`

</td>

<td>

LINK로 거래 수수료 결제 시 [Maker](../../5_Terms.md#maker) 주문에 대한 수수료 비율.<br/>
`enableLinkFee`가 false이면 이 값은 0입니다.

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`takerLinkFeeRate`

</td>

<td>

LINK로 거래 수수료 결제 시 [Taker](../../5_Terms.md#taker) 주문에 대한 수수료 비율.<br/>
`enableLinkFee`가 false이면 이 값은 0입니다.

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

주문의 상태. 다음 중 하나입니다.<br/>
\- "CREATE": 주문이 생성됨<br/>
\- "REQUEST": 주문이 주문장에 요청됨<br/>
\- "PROCESS": 주문이 부분적으로 취소되거나 체결됨<br/>
\- "COMPLETE": 주문이 [완료](../../5_Terms.md#completed-order)됨 (취소된 것도 포함).

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

<tr>

<td>

`completedAt`

</td>

<td>

주문이 [완료](../../5_Terms.md#completed-order)된 시각.<br/>
밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.<br/>
주문이 완료되지 않았다면 이 값은 0입니다.

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

체결된 총수량의 평균 가격

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
       "makerFeeRate": 0.1,
       "takerFeeRate": 0.1,
       "enableLinkFee": false,
       "makerLinkFeeRate": 0,
       "takerLinkFeeRate": 0,
       "status": "COMPLETE",
       "createdAt": 1528998406713,
       "completedAt": 1528998406907,
       "averageFillPrice": 0.00100915
   }
}
```

<p/>
