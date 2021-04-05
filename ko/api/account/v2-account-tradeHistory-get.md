# User trade history v2

조건에 따라 BITFRONT 내 거래 내역을 조회합니다. <br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.

> **Note**
> 
>   - 조회 기간은 최대 30일로 제한됩니다. 즉, `startTime`에서 `endTime`까지의 날짜가 30일을 초과할 수 없습니다.
>   - 결과 내역은 `responseData`에 저장되며 `responseData[].createAt` 기준 내림차순으로 정렬됩니다.
>   - 이 API 호출 횟수는 1초당 1회, 1분당 30회만 허용합니다.

## Endpoint URI

    GET https://openapi.bitfront.me/v2/account/tradeHistory?coinPair={coinPair}&startTime={startTime}&endTime={endTime}&max={max}

## Request parameters

| Name        | Description                                                                                                                                                                                                                      | Type    | Loc.  | Required |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | -------- |
| `coinPair`  | 조회할 [coin pair](/ko/5_Terms.md#coin-code). [Currency](/ko/5_Terms.md#currency-for-coin-trading)와 [Market](/ko/5_Terms.md#market-for-coin-trading)을 점(‘.’)으로 구분한 문자열로, 대소문자를 구분합니다. <br/>예를 들어 “BCH.ETH”은 ETH으로 BCH를 거래한다는 의미입니다. | String  | query | O        |
| `startTime` | 조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                                                                                                                                                                             | Integer | query | O        |
| `endTime`   | 조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. <br/>값을 지정하지 않을 경우 기본값인 `startTime`+24hrs가 됩니다.                                                                                                                            | Integer | query |          |
| `max`       | 조회할 거래 내역 최대 개수. 1\~100 사이여야 하며 기본값은 100입니다. 지정한 기간에 발생한 내역만 제공하므로 실제 반환되는 개수는 `max`보다 적을 수 있습니다.                                                                                                                                | Integer | query |          |

## Response

| Name            | Description                                                             | Type                          | Included |
| --------------- | ----------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | `responseTime`의 기준 시간. 항상 “UTC”입니다.                                     | String                        | O        |
| `responseTime`  | 응답 시간. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                               | Long                          | O        |
| `statusCode`    | 결과 상태 코드. [`StatusCode` 정의](/ko/1_Overview.md#statuscode-정의)를 참고하십시오.   | Integer                       | O        |
| `statusMessage` | 결과의 상세 메시지. [`StatusCode` 정의](/ko/1_Overview.md#statuscode-정의)를 참고하십시오. | String                        | O        |
| `responseData`  | 대상 객체 설명을 참고하십시오.                                                       | [responseData](#responsedata) |          |

### responseData

  - Type: array

거래 내역 목록.

[history](#history) 객체의 배열입니다.

### history

  - Type: object

| Name                 | Description                                                                                 | Type   | Included |
| -------------------- | ------------------------------------------------------------------------------------------- | ------ | -------- |
| `transactionID`      | 트랜잭션의 ID                                                                                    | Long   |          |
| `orderID`            | 주문의 ID                                                                                      | Long   |          |
| `market`             | [Market](/ko/5_Terms.md#market-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code)     | String |          |
| `currency`           | [Currency](/ko/5_Terms.md#currency-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code) | String |          |
| `price`              | 단위 가격                                                                                       | Double |          |
| `amount`             | 총수량                                                                                         | Double |          |
| `fee`                | 거래 수수료                                                                                      | Double |          |
| `totalConsideration` | `price * amount + fee`                                                                      | Double |          |
| `orderSide`          | 주문 방향. 다음 중 하나입니다. <br/>- “BUY”: 사기 <br/>- “SELL”: 팔기                                       | String |          |
| `fillType`           | 체결 타입. 다음 중 하나입니다. <br/>- “FULL”: 트랜잭션 전체 수량이 체결됨 <br/>- “PARTIAL”: 트랜잭션 부분 수량이 체결됨         | String |          |
| `createAt`           | 트랜잭션 생성 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                                              | Long   |          |

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
