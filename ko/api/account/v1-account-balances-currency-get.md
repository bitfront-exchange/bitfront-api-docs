# Currency balance

계정에서 지정 암호화폐의 잔액을 가져옵니다.

## Endpoint URI

```
GET https://openapi.bitbox.me/v1/account/balances/{currency}
```

## Request parameters

| Name       |  Description  | Type   | Loc. | Required |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ---- | -------- |
| `currency` | 잔액을 확인할 [Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code). 예를 들어 비트코인 캐시는 “BCH”가 됩니다. | String | path | O        |

## Response

| Name            | Description                                                                             | Type                          | Included |
| --------------- | --------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`      | `responseTime`의 기준 시간. 항상 “UTC”입니다.                                           | String                        | O        |
| `responseTime`  | 응답 시간. 밀리초 단위의 Unix Epoch (UTC) 타임스탬프입니다.                             | Long                          | O        |
| `statusCode`    | 결과 상태 코드. [`StatusCode` 정의](/1_Overview.md#statuscode-정의)를 참고하십시오.     | Integer                       | O        |
| `statusMessage` | 결과의 상세 메시지. [`StatusCode` 정의](/1_Overview.md#statuscode-정의)를 참고하십시오. | String                        | O        |
| `responseData`  | 대상 객체 설명을 참고하십시오.                                                          | [responseData](#responsedata) |          |

### responseData

- Type: object

| Name               | Description                                                                            | Type   | Included |
| ------------------ | -------------------------------------------------------------------------------------- | ------ | -------- |
| `currency`         | [Currency](/5_Terms.md#currency-for-coin-trading)의 [coin code](/5_Terms.md#coin-code) | String |          |
| `balance`          | 암호화폐 총잔액                                                                        | Double |          |
| `availableBalance` | 사용할 수 있는 (unlocked) 암호화폐 총잔액                                              | Double |          |

**A response example**

```json
{
  "timezone": "UTC",
  "responseTime": 1525239832135,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": [
    {
      "currency": "ETH",
      "balance": 1000107794.9999858,
      "availableBalance": 1000107794.9999858
    }
  ]
}
```
