# Cancellation of all open orders

지정한 [coin pair](/ko/5_Terms.md#coin-pair)의 열린 주문 전체를 취소하라고 요청합니다. 취소 요청된 주문 ID 목록을 반환합니다.
각 주문에 대해, 주문이 부분 체결되었으면 남은 부분만 취소하려고 시도합니다.

> **Caution**
> 
> `statusCode`가 1000이라는 것은 취소 요청이 잘 전해졌다는 뜻이며 성공적으로 취소되었다는 뜻이 아닙니다. 주문이 취소되었는지 확인하려면 [`/v2/account/orders/{orderID}`](/ko/api/account/v2-account-orders-orderID-get.md#order-information-v2)를 사용하십시오.

## Endpoint URI

    DELETE https://openapi.bitfront.me/v1/trade/openOrders/{coinPair}

## Request parameters

| Name       | Description                                                                                                                                                                                                                         | Type   | Loc. | Required |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ---- | -------- |
| `coinPair` | 취소 요청할 [coin pair](/ko/5_Terms.md#coin-pair). [Currency](/ko/5_Terms.md#currency-for-coin-trading)와 [Market](/ko/5_Terms.md#market-for-coin-trading)을 점(‘.’)으로 구분한 문자열로, 대소문자를 구분합니다. <br/>예를 들어 “BCH.ETH”은 ETH으로 BCH를 거래한다는 의미입니다. | String | path | O        |

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

| Name          | Description                                  | Type  | Included |
| ------------- | -------------------------------------------- | ----- | -------- |
| `orderIDList` | Long의 배열입니다. 주문 ID 목록                        | array |          |
| `requestAt`   | 주문 요청 시각. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다. | Long  |          |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1525080718,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "orderIDList": [
            10100000000561,
            10100000000563,
            10100000000564,
            10100000000565
        ],
        "requestAt": 1525080718
    }
}
```
