# Tick values

지정된 coin pair의 현재 tick 값을 조회합니다. <br/>
Bid, ask, last prices, 24시간 volume 및 24시간 내 시작가, 종가, 최대 가격, 최소 가격을 확인할 수 있습니다.

> **Note**
>
> 이 API는 헤더 파라미터에 `X-API-Key`만 전달하면 됩니다.

## Endpoint URI

```
GET https://openapi.bitbox.me/v1/market/public/currentTickValue?coinPair={coinPair}
```

## Request parameters

| Name                                     | Description                                                                                                                                                               | Type  | Loc. | Required |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ---- | -------- |
| `coinPair`                               | 조회할 [coin pair](/5_Terms.md#coin-pair). [Currency](/5_Terms.md#currency-for-coin-trading)와 [Market](/5_Terms.md#market-for-coin-trading)을 점('.')으로 구분한 문자열로, 대소문자를 구분합니다. <br/>예를 들어 “BCH.ETH”은 ETH으로 BCH를 거래한다는 의미입니다. | String | query | O    |          |

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

| Name     | Description  | Type   | Included |
| -------- | ------------ | ------ | -------- |
| `bid`    | bid tick 값   | Double | O        |
| `ask`    | ask tick 값   | Double | O        |
| `last`   | last tick 값  | Double | O        |
| `volume` | 24시간 volume  | Double | O        |
| `open`   | 24시간 내 시작가   | Double | O        |
| `close`  | 24시간 내 종가    | Double | O        |
| `high`   | 24시간 내 최대 가격 | Double | O        |
| `low`    | 24시간 내 최소 가격 | Double | O        |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1536567278026,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
        "bid": 0.400006,
        "ask": 0.400009,
        "last": 0.400006,
        "volume": 0.000800015,
        "open": 0.400009,
        "close": 0.400006,
        "high": 0.400009,
        "low": 0.400006
    }
}
```
