# Order information v2

한 주문의 상세 정보를 가져옵니다.
다음 식을 사용하여 이 주문이 취소되었는지 확인할 수 있습니다.

`filledAmount` + `remainAmount` \< `initialRequestAmount`

  - `filledAmount` + `remainAmount` \< `initialRequestAmount`이면, <br/>
    `initialRequestAmount` - (`filledAmount` + `remainAmount`) 만큼 취소되었다는 의미입니다.
  - `filledAmount` + `remainAmount` = `initialRequestAmount`이면, <br/>
    취소된 것이 없다는 의미입니다.

> **Note**
> 
> 이 API는, 조회한 주문의 Currency가 LINK이면 응답의 `currency` 필드에 티커 심볼인 “LN”을 반환합니다.

## Endpoint URI

    GET https://openapi.bitfront.me/v2/account/orders/{orderID}

## Request parameters

| Name      | Description                                           | Type | Loc. | Required |
| --------- | ----------------------------------------------------- | ---- | ---- | -------- |
| `orderID` | 가져올 주문의 ID. 주문 ID는 주문을 요청하거나 요청 목록을 가져올 때 확인할 수 있습니다. | Long | path | O        |

## Response

| Name            | Description                                                             | Type                          | Included |
| --------------- | ----------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | `responseTime`의 기준 시간. 항상 “UTC”입니다.                                     | String                        | O        |
| `responseTime`  | 응답 시간. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                               | Long                          | O        |
| `statusCode`    | 결과 상태 코드. [`StatusCode` 정의](/ko/1_Overview.md#statuscode-정의)를 참고하십시오.   | Integer                       | O        |
| `statusMessage` | 결과의 상세 메시지. [`StatusCode` 정의](/ko/1_Overview.md#statuscode-정의)를 참고하십시오. | String                        | O        |
| `responseData`  | 대상 객체 설명을 참고하십시오.                                                       | [responseData](#responsedata) |          |

### responseData

  - Type: object

| Name                    | Description                                                                                                                                                                                                                                                      | Type    | Included |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | -------- |
| `orderID`               | 주문의 ID                                                                                                                                                                                                                                                           | Long    |          |
| `market`                | [Market](/ko/5_Terms.md#market-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code)                                                                                                                                                                          | String  |          |
| `currency`              | [Currency](/ko/5_Terms.md#currency-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code)                                                                                                                                                                      | String  |          |
| `orderType`             | 주문 타입. 다음 중 하나입니다. <br/>- “MARKET”: Market order <br/>- “LIMIT”: Limit order <br/>- “STOPLIMIT”: Stop-Limit order                                                                                                                                                | String  |          |
| `orderSide`             | 주문 방향. 다음 중 하나입니다. <br/>- “BUY”: 사기 <br/>- “SELL”: 팔기                                                                                                                                                                                                            | String  |          |
| `price`                 | 제한 가격                                                                                                                                                                                                                                                            | Double  |          |
| `stopPrice`             | 예약 실행 가격. `orderType`이 “STOPLIMIT”일 때만 나타납니다.                                                                                                                                                                                                                    | Double  |          |
| `initialRequestAmount`  | 처음 요청한 총수량                                                                                                                                                                                                                                                       | Double  |          |
| `requestAmount`         | 취소한 후의 총수량                                                                                                                                                                                                                                                       | Double  |          |
| `remainAmount`          | 체결되지도 않고 취소되지도 않은 총수량                                                                                                                                                                                                                                            | Double  |          |
| `filledAmount`          | 체결된 총수량                                                                                                                                                                                                                                                          | Double  |          |
| `reservedValue`         | 주문의 예상 가치. <br/>예를 들어 `currency`가 “XRP”, `market`이 “BTC”일 때, <br/>- `orderSide`가 “BUY”이면, `reservedValue`는 BTC로 `requestAmount` \* `price` \* (1 + *fee rate*)입니다. <br/>- `orderSide`가 “SELL”이면, `reservedValue`는 XRP로 `requestAmount`입니다.                       | Double  |          |
| `reserveRemainingValue` | 주문 내 남은 총수량 예상 가치. <br/>예를 들어 `currency`가 “XRP”, `market`이 “BTC”일 때, <br/>- `orderSide`가 “BUY”이면, `reserveRemainingValue`는 BTC로 `remainAmount` \* `price` \* (1 + *fee rate*)입니다. <br/>- `orderSide`가 “SELL”이면, `reserveRemainingValue`는 XRP로 `remainAmount`입니다. | Double  |          |
| `makerFeeRate`          | [Maker](/ko/5_Terms.md#maker) 주문에 대한 수수료 비율. <br/>수수료는 절대값이 아닙니다. 예를 들어 이 값이 0.001이면 수수료 비율이 0.1%라는 의미입니다.                                                                                                                                                       | Double  |          |
| `takerFeeRate`          | [Taker](/ko/5_Terms.md#taker) 주문에 대한 수수료 비율. <br/>수수료는 절대값이 아닙니다. 예를 들어 이 값이 0.001이면 수수료 비율이 0.1%라는 의미입니다.                                                                                                                                                       | Double  |          |
| `enableLnFee`           | LN으로 거래 수수료 결제 여부. <br/>LN으로 거래 수수료를 결제하는 방법에 관한 상세한 설명은 [Transaction fees](https://www.bitfront.me/fees/)를 참고하십시오.                                                                                                                                              | Boolean |          |
| `makerLnFeeRate`        | LN으로 거래 수수료 결제 시 [Maker](/ko/5_Terms.md#maker) 주문에 대한 수수료 비율. <br/>`enableLnFee`가 false이면 이 값은 0입니다.                                                                                                                                                             | Double  |          |
| `takerLnFeeRate`        | LN로 거래 수수료 결제 시 [Taker](/ko/5_Terms.md#taker) 주문에 대한 수수료 비율. <br/>`enableLnFee`가 false이면 이 값은 0입니다.                                                                                                                                                              | Double  |          |
| `status`                | 주문의 상태. 다음 중 하나입니다. <br/>- “CREATE”: 주문이 생성됨 <br/>- “PENDING”: STOPLIMIT 주문이 예약되었고 아직 실행되지 않음 <br/>- “REQUEST”: 주문이 주문장에 요청됨 <br/>- “PROCESS”: 주문이 부분적으로 취소되거나 체결됨 <br/>- “COMPLETE”: 주문이 [완료](/ko/5_Terms.md#completed-order)됨 (취소된 것도 포함).                     | String  |          |
| `createAt`              | 트랜잭션 생성 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                                                                                                                                                                                                                   | Long    |          |
| `completedAt`           | 주문이 [완료](/ko/5_Terms.md#completed-order)된 시각. <br/>밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. <br/>주문이 완료되지 않았다면 이 값은 0입니다.                                                                                                                                              | Long    |          |
| `averageFillPrice`      | 체결된 총수량의 평균 가격                                                                                                                                                                                                                                                   | Double  |          |

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
       "orderType": "STOPLIMIT",
       "orderSide": "BUY",
       "price": 0.00100915,
       "stopPrice": 0.00101,
       "initialRequestAmount": 200,
       "requestAmount": 200,
       "remainAmount": 0,
       "filledAmount": 200,
       "reservedValue": 0.222013,
       "reserveRemainingValue": 0,
       "makerFeeRate": 0.001,
       "takerFeeRate": 0.001,
       "enableLnFee": false,
       "makerLnFeeRate": 0,
       "takerLnFeeRate": 0,
       "status": "COMPLETE",
       "createdAt": 1528998406713,
       "completedAt": 1528998406907,
       "averageFillPrice": 0.00100915
   }
}
```
