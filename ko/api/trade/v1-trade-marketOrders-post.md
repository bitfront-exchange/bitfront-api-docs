# Market order

지정 조건으로 시장가 주문을 합니다. <br/>
쿼리 파라미터에서 조건을 설정할 수 있습니다. 파라미터 설명을 참고하십시오.

## Endpoint URI

```
POST https://openapi.bitbox.me/v1/trade/marketOrders
```

## Request parameters

| Name                                     | Description                                                                                                                                                               | Type   | Loc. | Required |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ---- | -------- |
| `coinPair`                               | 주문할 [coin pair](/5_Terms.md#coin-pair). [Currency](/5_Terms.md#currency-for-coin-trading)와 [Market](/5_Terms.md#market-for-coin-trading)을 점('.')으로 구분한 문자열로, 대소문자를 구분합니다. <br/>예를 들어 “BCH.ETH”은 ETH으로 BCH를 거래한다는 의미입니다. | String | body   | O    |          |
| `quantity`                               | 주문할 최대 혹은 최소 양. 0보다 커야 합니다. | Double | body | O        |
| `orderSide`                              | 주문 방향. 다음 중 하나여야 합니다.  <br/>- “BUY”: 사기 <br/>- “SELL”: 팔기 | String | body | O |

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

| Name        | Description                                  | Type | Included |
| ----------- | -------------------------------------------- | ---- | -------- |
| `orderID`   | 주문의 ID. 주문의 상세 정보를 확인하거나 취소할 때 사용할 수 있습니다.   | Long |          |
| `requestAt` | 주문 요청 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | Long |          |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1525079412,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": {
      "orderID": 10100000000565,
      "requestAt": 1525079412
  }
}
```
