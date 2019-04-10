# Cancellation

지정한 주문 하나를 취소하라고 요청합니다.<br/>
주문이 부분 체결되었으면 남은 부분만 취소하려고 시도합니다.<br/>

> **Caution**<br/>
> `statusCode`이 1000이라는 것은 취소 요청이 잘 전해졌다는 뜻이며 성공적으로 취소되었다는 뜻이 아닙니다. 주문이 취소되었는지 확인하려면 [`/v1/account/orders/{orderID}`](../account/v1-account-orders-orderID-get.md#order-information)를 사용하십시오.

## Endpoint URI

    DELETE https://openapi.bitbox.me/v1/trade/orders/{orderID}

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

취소 요청할 주문의 ID. 주문 ID는 주문을 요청하거나 요청 목록을 가져올 때 확인할 수 있습니다.

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
|---|---|---|---|---|| `orderID` |  취소 요청할 주문의 ID. 주문 ID는 주문을 요청하거나 요청 목록을 가져올 때 확인할 수 있습니다. | <span class="nowrap">Long</span> | path |  O  | -->

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

The order ID

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
    "responseTime": 1525080581,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderID": 10100000000561,
        "requestAt": 1525080581
    }
}
```

<p/>
