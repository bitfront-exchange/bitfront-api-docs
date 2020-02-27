# Balance

계정의 잔액을 가져옵니다.

## Endpoint URI

    GET https://openapi.bitfront.me/v1/account/balances

## Request parameters

None

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

[balance](#balance-1) 객체의 배열입니다.

### balance

  - Type: object

| Name               | Description                                                                                 | Type   | Included |
| ------------------ | ------------------------------------------------------------------------------------------- | ------ | -------- |
| `currency`         | [Currency](/ko/5_Terms.md#currency-for-coin-trading)의 [coin code](/ko/5_Terms.md#coin-code) | String |          |
| `balance`          | 암호화폐 총잔액                                                                                    | Double |          |
| `availableBalance` | 사용할 수 있는 (unlocked) 암호화폐 총잔액                                                                | Double |          |

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
