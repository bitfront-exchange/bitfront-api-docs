# Coin transfer history

지정한 조건에 따라 계정의 암호화폐 전송 내역을 조회합니다.<br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.<br/>
결과 데이터는 응답의 `responseData.content`에 저장되며, 이는 `responseData.content.date` 기준 내림차순으로 정렬됩니다.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/account/transactionHistory?currency={currency}&startTime={startTime}&endTime={endTime}&transferType={transferType}&page={page}&pageSize={pageSize}

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

`currency`

</td>

<td>

[Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code).<br/>
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

`startTime`

</td>

<td>

조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

</td>

<td style="text-align: center;">

<span class="nowrap">Long</span>

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

<span class="nowrap">Long</span>

</td>

<td style="text-align: center;">

<span class="nowrap">query<span>

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`transferType`

</td>

<td>

전송 방식. 다음 중 하나이거나 생략해야 합니다.<br/>
\- "WITHDRAW": 출금한 내역만 가져옴<br/>
\- "DEPOSIT": 입금한 내역만 가져옴<br/>
두 가지 방식 내역을 모두 가져오려면 이 파라미터를 생략하십시오.<br/>
대소문자를 구분합니다.

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

`page`

</td>

<td>

조회할 페이지의 번호.<br/>
페이지 번호는 0에서 시작하며 기본값은 0입니다.

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

`pageSize`

</td>

<td>

한 페이지에 보여줄 내역의 개수. 기본값은 20이며 최댓값은 1000입니다.<br/>
\- `page`가 0이고 `pageSize`가 20이면 1번째에서 20번째까지의 내역을 보여줍니다.<br/>
\- `page`가 1이고 `pageSize`가 20이면 21번째에서 40번째까지의 내역을 보여줍니다.

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
|---|---|---|---|---|| `currency` |  [Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code).<br/>
예를 들어 비트코인 캐시는 \"BCH\"가 됩니다. | <span class="nowrap">String</span> | query |     || `startTime` |  조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | <span class="nowrap">Long</span> | query |     || `endTime` |  조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | <span class="nowrap">Long</span> | query |     || `transferType` |  전송 방식. 다음 중 하나이거나 생략해야 합니다.<br/>
- \"WITHDRAW\": 출금한 내역만 가져옴<br/>
- \"DEPOSIT\": 입금한 내역만 가져옴<br/>
두 가지 방식 내역을 모두 가져오려면 이 파라미터를 생략하십시오.<br/>
대소문자를 구분합니다. | <span class="nowrap">String</span> | query |     || `page` |  조회할 페이지의 번호.<br/>
페이지 번호는 0에서 시작하며 기본값은 0입니다. | <span class="nowrap">Integer</span> | query |     || `pageSize` |  한 페이지에 보여줄 내역의 개수. 기본값은 20이며 최댓값은 1000입니다.<br/>
- `page`가 0이고 `pageSize`가 20이면 1번째에서 20번째까지의 내역을 보여줍니다.<br/>
- `page`가 1이고 `pageSize`가 20이면 21번째에서 40번째까지의 내역을 보여줍니다. | <span class="nowrap">Integer</span> | query |     | -->

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

`number`

</td>

<td>

페이지 번호

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`size`

</td>

<td>

페이지 크기

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`totalPages`

</td>

<td>

총 페이지 수

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`numberOfElements`

</td>

<td>

페이지에 포함된 레코드 수

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`totalElements`

</td>

<td>

반환된 전체 레코드 수

</td>

<td style="text-align: center;">

Integer

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`previousPage`

</td>

<td>

이전 페이지가 있는지 나타내는 플래그

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`first`

</td>

<td>

이 페이지가 첫 번째 페이지인지 나타내는 플래그

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`nextPage`

</td>

<td>

다음 페이지가 있는지 나타내는 플래그

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`last`

</td>

<td>

이 페이지가 마지막 페이지인지 나타내는 플래그

</td>

<td style="text-align: center;">

Boolean

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`content`

</td>

<td>

대상
객체 설명을 참고하십시오.

</td>

<td style="text-align: center;">

[content](#content)

</td>

<td style="text-align: center;">

 

</td>

</tr>

</tbody>

</table>

### content

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

`date`

</td>

<td>

암호화폐 전송 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`coinType`

</td>

<td>

전송한 암호화폐의 [coin code](/5_Terms.md#coin-code)

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`transferType`

</td>

<td>

암호화폐 전송 방식. 다음 중 하나입니다.<br/>
\- "WITHDRAW": 출금<br/>
\- "DEPOSIT": 입금

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`amount`

</td>

<td>

전송한 암호화폐 총수량

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

전송 수수료

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`total`

</td>

<td>

`amount + fee`

</td>

<td style="text-align: center;">

Double

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`address`

</td>

<td>

목표 주소

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

 

</td>

</tr>

<tr>

<td>

`status`

</td>

<td>

암호화폐 전송 상태. 다음 중 하나입니다.<br/>
\- "REQUEST": 전송 요청됨<br/>
\- "PENDING": 전송 대기중<br/>
\- "CONFIRM": 전송 확인됨<br/>
\- "FAIL": 전송 실패<br/>
\- "CANCEL\_REQUEST": 전송 취소가 요청됨<br/>
\- "CANCEL": 전송이 완전히 취소됨<br/>
\- "CANCEL\_FAIL": 전송 취소가 요청되었으나 취소가 실패함

</td>

<td style="text-align: center;">

String

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
    "responseTime": 1527658634583,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "number": 0,
        "size": 100,
        "totalPages": 1,
        "numberOfElements": 2,
        "totalElements": 2,
        "previousPage": false,
        "first": true,
        "nextPage": false,
        "last": true,
        "content": [
            {
                "date": 1525420991000,
                "coinType": "BTC",
                "transferType": "WITHDRAW",
                "amount": 0.5,
                "fee": 0,
                "total": 0.5,
                "address": "2N8V9g4Ezd5wFGmoNgJYy8YUuYUMYqnATWJ",
                "status": "CONFIRM"
            },
            {
                "date": 1525420983000,
                "coinType": "BTC",
                "transferType": "WITHDRAW",
                "amount": 0.5,
                "fee": 0,
                "total": 0.5,
                "address": "2N9rMM6SrSZ7Xspfqu1QMmTXVvYGm8KPjTu",
                "status": "CONFIRM"
            }
        ]
    }
}
```

<p/>
