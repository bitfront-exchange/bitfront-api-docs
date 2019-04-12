# User trade history v2

조건에 따라 BITBOX 내 거래 내역을 조회합니다.<br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.<br/>

> **Note**<br/>
> \- 조회 기간은 최대 30일로 제한됩니다. 즉, `startTime`에서 `endTime`까지의 날짜가 30일을 초과할 수 없습니다.<br/>
> \- 결과 내역은 `responseData`에 저장되며 `responseData[].createAt` 기준 내림차순으로 정렬됩니다.<br/>
> \- 이 API는 [RPS 제한 정책](../../2_Authentication_and_Security_Policy.md#rps-제한-정책)과 별도로, 1RPS만 허용됩니다.

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

조회할 [coin pair](../../5_Terms.md#coin-code). [Currency](../../5_Terms.md#currency-for-coin-trading)와 [Market](../../5_Terms.md#market-for-coin-trading)을 점('.')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 "BCH.ETH"은 ETH으로 BCH를 거래한다는 의미입니다.<br/>
이 파라미터가 생략되면 API는 모든 암호화폐 거래 내역을 반환합니다.

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

O

</td>

</tr>

<tr>

<td>

`endTime`

</td>

<td>

조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.<br/>
값을 지정하지 않을 경우 기본값인 `startTime`+24hrs가 됩니다.

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
지정한 기간에 발생한 내역만 제공하므로 실제 반환되는 개수는 `max`보다 적을 수 있습니다.

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
|---|---|---|---|---|| `coinPair` |  조회할 [coin pair](../../5_Terms.md#coin-code). [Currency](../../5_Terms.md#currency-for-coin-trading)와 [Market](../../5_Terms.md#market-for-coin-trading)을 점(\'.\')으로 구분한 문자열로, 대소문자를 구분합니다.<br/>
예를 들어 \"BCH.ETH\"은 ETH으로 BCH를 거래한다는 의미입니다.<br/>
이 파라미터가 생략되면 API는 모든 암호화폐 거래 내역을 반환합니다. | <span class="nowrap">String</span> | query |     || `startTime` |  조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | <span class="nowrap">Integer</span> | query |  O  || `endTime` |  조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.<br/>
값을 지정하지 않을 경우 기본값인 `startTime`+24hrs가 됩니다. | <span class="nowrap">Integer</span> | query |     || `max` |  조회할 거래 내역 최대 개수. 1\~100 사이여야 하며 기본값은 100입니다.<br/>
지정한 기간에 발생한 내역만 제공하므로 실제 반환되는 개수는 `max`보다 적을 수 있습니다. | <span class="nowrap">Integer</span> | query |     | -->

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
    거래 내역 목록

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

`fee`

</td>

<td>

거래 수수료

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

`price * amount + fee`

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

`fillType`

</td>

<td>

체결 타입. 다음 중 하나입니다.<br/>
\- "FULL": 트랜잭션 전체 수량이 체결됨<br/>
\- "PARTIAL": 트랜잭션 부분 수량이 체결됨

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
