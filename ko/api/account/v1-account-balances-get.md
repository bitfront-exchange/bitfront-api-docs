# Balance

계정의 잔액을 가져옵니다.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/account/balances

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

[balance](#balance)
객체의 배열입니다.

### balance

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

`balance`

</td>

<td>

암호화폐 총잔액

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

사용할 수 있는 (unlocked) 암호화폐 총잔액

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
    "responseTime": 1525239801363,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "currency": "BCH",
            "balance": 1000000000,
            "availableBalance": 1000000000
        },
        {
            "currency": "XRP",
            "balance": 1000003043.7,
            "availableBalance": 1000002063.7
        },
        {
            "currency": "ETH",
            "balance": 1000107794.9999858,
            "availableBalance": 1000107794.9999858
        },
        {
            "currency": "BTC",
            "balance": 3999974992.35615,
            "availableBalance": 3999970806.72614
        },
        {
            "currency": "USDT",
            "balance": 1000000000,
            "availableBalance": 999998671.673
        }
    ]
}
```

<p/>
