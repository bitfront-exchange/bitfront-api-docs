# Market coin pair policy

BITBOX가 지원하는 coin pair의 최신 정보를 조회합니다.<br/>

> **Note**<br/>
> 이 API는 헤더 파라미터에 `X-API-Key`만 전달하면 됩니다.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/market/public/coins/pairPolicy

## Request parameters

None

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
    BITBOX가 지원하는 coin pair의 최신 정보 목록입니다.

[pairList](#pairlist)
객체의 배열입니다.

### pairList

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

`marketType`

</td>

<td>

[Market](../../5_Terms.md#market-for-coin-trading) 타입. 해당하는 암호화폐의 [coin code](../../5_Terms.md#coin-code)로 나타납니다. 예를 들어 비트코인은 "BTC", 이더리움은 "ETH"입니다.

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`coinType`

</td>

<td>

[Currency](../../5_Terms.md#currency-for-coin-trading) 타입. 해당하는 암호화폐의 [coin code](../../5_Terms.md#coin-code)로 나타납니다. 예를 들어 비트코인은 "BTC", 이더리움은 "ETH"입니다.

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`displayNameOfCoinInformation`

</td>

<td>

[Currency](../../5_Terms.md#currency-for-coin-trading)의 노출 이름

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`coinPairType`

</td>

<td>

[Coin-pair](../../5_Terms.md#coin-pair) 타입. `marketType`과 `coinType`을 점(.)으로 연결한 문자열입니다.

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minTradeAmount`

</td>

<td>

최소 거래 수량

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

`maxTradeAmount`

</td>

<td>

최대 거래 수량

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

`minTradeVolume`

</td>

<td>

최소 거래 금액

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

`maxTradeVolume`

</td>

<td>

최대 거래 금액

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

`tradeMakerFeeRate`

</td>

<td>

Maker 거래 수수료. 총 거래 금액의 백분율(%)입니다.

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

`tradeTakerFeeRate`

</td>

<td>

Taker 거래 수수료. 총 거래 금액의 백분율(%)입니다.

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

`tradeFeeUnit`

</td>

<td>

수수료 지불 암호화폐

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minPrice`

</td>

<td>

거래 암호화폐의 단위별 최소 가격. 예를 들어 BTC.ETH라면, 1ETH을 거래할 때 최소 제시해야 하는 BTC를 말합니다.<br/>
소수점 7자리부터는 [E-표기법](https://en.wikipedia.org/wiki/Scientific_notation#E-notation)으로 나타납니다.

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

`minPriceUnit`

</td>

<td>

`minPrice`의 단위 암호화폐

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`minAmountDecimal`

</td>

<td>

주문 수량의 유효 소수점 자릿수. 이 값이 2이면 주문 수량은 소수점 둘째 자리까지만 입력할 수 있습니다..

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

`minPriceDecimal`

</td>

<td>

주문 가격의 유효 소수점 자릿수. 이 값이 8이면 주문 가격은 소수점 여덟째 자리까지만 입력할 수 있습니다.

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

`trade`

</td>

<td>

거래 가능 여부

</td>

<td style="text-align: center;">

Boolean

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
    "responseTime": 1553067063052,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "marketType": "BTC",
            "coinType": "AION",
            "displayNameOfCoinInformation": "Aion",
            "coinPairType": "BTC.AION",
            "tradeMinAmount": 0.01,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 0.001,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "BTC",
            "minPrice": 0.000001,
            "minPriceUnit": "BTC",
            "minAmountDecimal": 2,
            "minPriceDecimal": 6,
            "trade": true
        },
        {
            "marketType": "ETH",
            "coinType": "BTM",
            "displayNameOfCoinInformation": "Bytom",
            "coinPairType": "ETH.BTM",
            "tradeMinAmount": 1,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 0.01,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "ETH",
            "minPrice": 1e-8,
            "minPriceUnit": "ETH",
            "minAmountDecimal": 0,
            "minPriceDecimal": 8,
            "trade": false
        },
        {
            "marketType": "USDT",
            "coinType": "BCH",
            "displayNameOfCoinInformation": "Bitcoin Cash",
            "coinPairType": "USDT.BCH",
            "tradeMinAmount": 0.001,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 10,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "USDT",
            "minPrice": 0.01,
            "minPriceUnit": "USDT",
            "minAmountDecimal": 3,
            "minPriceDecimal": 2,
            "trade": true
        },
        //...이하 생략됨
    ]
}
```

<p/>
