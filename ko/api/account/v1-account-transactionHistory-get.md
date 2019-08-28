# Coin transfer history

지정한 조건에 따라 계정의 암호화폐 전송 내역을 조회합니다. <br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오. <br/>
결과 데이터는 응답의 `responseData.content`에 저장되며, 이는 `responseData.content.date` 기준 내림차순으로 정렬됩니다.

## Endpoint URI

```
GET https://openapi.bitbox.me/v1/account/transactionHistory?currency={currency}&startTime={startTime}&endTime={endTime}&transferType={transferType}&page={page}&pageSize={pageSize}
```

## Request parameters

| Name                       | Description                                                                            | Type  | Loc.  | Required |
| -------------------------- | -------------------------------------------------------------------------------------- | ----- | ----- | -------- |
| `currency`                 | [Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code). <br/>예를 들어 비트코인 캐시는 “BCH”가 됩니다. | String  | query |       |          |
| `startTime`                | 조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.  | Long  | query |          |
| `endTime`                  | 조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.  | Long  | query |          |
| `transferType`             | 전송 방식. 다음 중 하나이거나 생략해야 합니다. <br/>- “WITHDRAW”: 출금한 내역만 가져옴 <br/>- “DEPOSIT”: 입금한 내역만 가져옴 <br/>두 가지 방식 내역을 모두 가져오려면 이 파라미터를 생략하십시오. <br/>대소문자를 구분합니다. | String | query | |
| `page` | 조회할 페이지의 번호. <br/>페이지 번호는 0에서 시작하며 기본값은 0입니다. | Integer | query | |
| `pageSize` | 한 페이지에 보여줄 내역의 개수. 기본값은 20이며 최댓값은 1000입니다. <br/>- `page`가 0이고 `pageSize`가 20이면 1번째에서 20번째까지의 내역을 보여줍니다. <br/>- `page`가 1이고 `pageSize`가 20이면 21번째에서 40번째까지의 내역을 보여줍니다. | Integer | query | |

## Response

| Name            | Description                                                          | Type                          | Included |
| --------------- | -------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | `responseTime`의 기준 시간. 항상 “UTC”입니다.                                  | String                        | O        |
| `responseTime`  | 응답 시간. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                            | Long                          | O        |
| `statusCode`    | 결과 상태 코드. [`StatusCode` 정의](/1_Overview.md#statuscode-정의)를 참고하십시오.   | Integer                       | O        |
| `statusMessage` | 결과의 상세 메시지. [`StatusCode` 정의](/1_Overview.md#statuscode-정의)를 참고하십시오. | String                        | O        |
| `responseData`  | 대상 객체 설명을 참고하십시오.                                                    | [responseData](#responsedata) |          |

### responseData

  - Type: object

| Name               | Description                | Type    | Included |
| ------------------ | -------------------------- | ------- | -------- |
| `number`           | 페이지 번호                   | Integer |          |
| `size`             | 페이지 크기                   | Integer |          |
| `totalPages`       | 총 페이지 수                  | String  |          |
| `numberOfElements` | 페이지에 포함된 레코드 수        | Integer |          |
| `totalElements`    | 반환된 전체 레코드 수           | Integer |          |
| `previousPage`     | 이전 페이지가 있는지 나타내는 플래그         | Boolean |          |
| `first`            | 이 페이지가 첫 번째 페이지인지 나타내는 플래그 | Boolean |          |
| `nextPage`         | 다음 페이지가 있는지 나타내는 플래그         | Boolean |          |
| `last`             | 이 페이지가 마지막 페이지인지 나타내는 플래그  | Boolean |          |
| `content`          | 대상 객체 설명을 참고하십시오.     | [content](#content)        |         |          |

### content

  - Type: object

| Name           | Description                                    | Type   | Included |
| -------------- | ---------------------------------------------- | ------ | -------- |
| `date`         | 암호화폐 전송 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | Long   |          |
| `coinType`     | 전송한 암호화폐의 [coin code](/5_Terms.md#coin-code)   | String |          |
| `transferType` | 암호화폐 전송 방식. 다음 중 하나입니다.  <br/>- “WITHDRAW”: 출금 <br/>- “DEPOSIT”: 입금 | String | |
| `amount` | 전송한 암호화폐 총수량 | Double | |
| `fee` | 전송 수수료 | Double | |
| `total` | `amount + fee` | Double | |
| `address` | 목표 주소 | String | |
| `status` | 암호화폐 전송 상태. 다음 중 하나입니다. <br/>- “REQUEST”: 전송 요청됨 <br/>- “PENDING”: 전송 대기중 <br/>- “CONFIRM”: 전송 확인됨 <br/>- “FAIL”: 전송 실패 <br/>- “CANCEL_REQUEST”: 전송 취소가 요청됨 <br/>- “CANCEL”: 전송이 완전히 취소됨 <br/>- “CANCEL_FAIL”: 전송 취소가 요청되었으나 취소가 실패함 | String | |

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
