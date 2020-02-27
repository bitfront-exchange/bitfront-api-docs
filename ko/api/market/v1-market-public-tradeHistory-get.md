# Market trade history

조건에 따라 BITFRONT 내 최근 거래 내역을 조회합니다. <br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.

> **Note**
> 
>   - 이 API는 API KEY 발급 없이 사용할 수 있습니다.
>   - 최근 3개월 이내의 내역만 제공합니다.
>   - 결과 내역은 `responseData`에 저장되며 `responseData[].createAt` 기준 내림차순으로 정렬됩니다.

## Endpoint URI

    GET https://openapi.bitfront.me/v1/market/public/tradeHistory?coinPair={coinPair}&startTime={startTime}&endTime={endTime}&max={max}

## Request parameters

| Name        | Description                                                                                                                                                                                                                      | Type    | Loc.  | Required |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | -------- |
| `coinPair`  | 조회할 [coin pair](/ko/5_Terms.md#coin-pair). [Currency](/ko/5_Terms.md#currency-for-coin-trading)와 [Market](/ko/5_Terms.md#market-for-coin-trading)을 점(‘.’)으로 구분한 문자열로, 대소문자를 구분합니다. <br/>예를 들어 “BCH.ETH”은 ETH으로 BCH를 거래한다는 의미입니다. | String  | query |          |
| `startTime` | 조회할 거래 내역의 처음 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                                                                                                                                                                             | Integer | query |          |
| `endTime`   | 조회할 거래 내역의 마지막 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                                                                                                                                                                            | Integer | query |          |
| `max`       | 조회할 거래 내역 최대 개수. 1\~100 사이여야 하며 기본값은 100입니다. <br/>최근 3개월 이내의 내역만 제공하므로 실제 반환되는 개수는 `max`보다 적을 수 있습니다.                                                                                                                            | Integer | query |          |

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

BITFRONT 내의 최근 거래 내역입니다.

[history](#history) 객체의 배열입니다.

### history

  - Type: object

| Name            | Description                                                                                 | Type   | Included |
| --------------- | ------------------------------------------------------------------------------------------- | ------ | -------- |
| `transactionID` | 트랜잭션의 ID                                                                                    | Long   |          |
| `market`        | [Market](/ko/5_Terms.md#market-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code)     | String |          |
| `currency`      | [Currency](/ko/5_Terms.md#currency-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code) | String |          |
| `price`         | 단위 가격                                                                                       | Double |          |
| `amount`        | 총수량                                                                                         | Double |          |
| `totalValue`    | `amount` \* `price`                                                                         | Double |          |
| `orderSide`     | 주문 방향. 다음 중 하나입니다. <br/>- “BUY”: 사기 <br/>- “SELL”: 팔기                                       | String |          |
| `createAt`      | 트랜잭션 생성 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                                              | Long   |          |

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
