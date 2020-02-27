# Market coin pair policy

BITFRONT가 지원하는 coin pair의 최신 정보를 조회합니다.

> **Note**
> 
> 이 API는 API KEY 발급 없이 사용할 수 있습니다.

## Endpoint URI

    GET https://openapi.bitfront.me/v1/market/public/coins/pairPolicy

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

BITFRONT가 지원하는 coin pair의 최신 정보 목록입니다.

[pairList](#pairlist) 객체의 배열입니다.

### pairList

  - Type: object

| Name                           | Description                                                                                                                                                           | Type    | Included |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | -------- |
| `marketType`                   | [Market](/ko/5_Terms.md#market-for-coin-trading) 타입. 해당하는 암호화폐의 [coin code](/ko/5_Terms.md#coin-code)로 나타납니다. 예를 들어 비트코인은 “BTC”, 이더리움은 “ETH”입니다.                      | String  | O        |
| `coinType`                     | [Currency](/ko/5_Terms.md#currency-for-coin-trading) 타입. 해당하는 암호화폐의 [coin code](/ko/5_Terms.md#coin-code)로 나타납니다. 예를 들어 비트코인은 “BTC”, 이더리움은 “ETH”입니다.                  | String  | O        |
| `displayNameOfCoinInformation` | [Currency](/ko/5_Terms.md#currency-for-coin-trading)의 노출 이름                                                                                                           | String  | O        |
| `coinPairType`                 | [Coin-pair](/ko/5_Terms.md#coin-pair) 타입. `marketType`과 `coinType`을 점(.)으로 연결한 문자열입니다.                                                                                | String  | O        |
| `minTradeAmount`               | 최소 거래 수량                                                                                                                                                              | Double  | O        |
| `maxTradeAmount`               | 최대 거래 수량                                                                                                                                                              | Double  | O        |
| `minTradeVolume`               | 최소 거래 금액                                                                                                                                                              | Double  | O        |
| `maxTradeVolume`               | 최대 거래 금액                                                                                                                                                              | Double  | O        |
| `tradeMakerFeeRate`            | [Maker](/ko/5_Terms.md#maker) 거래 수수료. 총 거래 금액의 백분율(%)입니다.                                                                                                             | Double  | O        |
| `tradeTakerFeeRate`            | [Taker](/ko/5_Terms.md#taker) 거래 수수료. 총 거래 금액의 백분율(%)입니다.                                                                                                             | Double  | O        |
| `tradeFeeUnit`                 | 수수료 지불 암호화폐                                                                                                                                                           | String  | O        |
| `minPrice`                     | 거래 암호화폐의 단위별 최소 가격. 예를 들어 BTC.ETH라면, 1ETH을 거래할 때 최소 제시해야 하는 BTC를 말합니다. <br/>소수점 7자리부터는 [E-표기법](https://en.wikipedia.org/wiki/Scientific_notation#E-notation)으로 나타납니다. | Double  | O        |
| `minPriceUnit`                 | `minPrice`의 단위 암호화폐                                                                                                                                                   | String  | O        |
| `minAmountDecimal`             | 주문 수량의 유효 소수점 자릿수. 이 값이 2이면 주문 수량은 소수점 둘째 자리까지만 입력할 수 있습니다.                                                                                                           | Double  | O        |
| `minPriceDecimal`              | 주문 가격의 유효 소수점 자릿수. 이 값이 8이면 주문 가격은 소수점 여덟째 자리까지만 입력할 수 있습니다.                                                                                                          | Double  | O        |
| `trade`                        | 거래 가능 여부                                                                                                                                                              | Boolean | O        |

**A response example**

``` json
{
    "timezone": "UTC",
    "responseTime": 1553067063052,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": [
        {
            "marketType": "BTC",
            "coinType": "AION",
            "displayNameOfCoinInformation": "Aion",
            "coinPairType": "BTC.AION",
            "tradeMinAmount": 0.01,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 0.001,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "BTC",
            "minPrice": 0.000001,
            "minPriceUnit": "BTC",
            "minAmountDecimal": 2,
            "minPriceDecimal": 6,
            "trade": true
        },
        {
            "marketType": "ETH",
            "coinType": "BTM",
            "displayNameOfCoinInformation": "Bytom",
            "coinPairType": "ETH.BTM",
            "tradeMinAmount": 1,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 0.01,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "ETH",
            "minPrice": 1e-8,
            "minPriceUnit": "ETH",
            "minAmountDecimal": 0,
            "minPriceDecimal": 8,
            "trade": false
        },
        {
            "marketType": "USDT",
            "coinType": "BCH",
            "displayNameOfCoinInformation": "Bitcoin Cash",
            "coinPairType": "USDT.BCH",
            "tradeMinAmount": 0.001,
            "tradeMaxAmount": 99999999999999999,
            "tradeMinVolume": 10,
            "tradeMaxVolume": 99999999999999999,
            "tradeMakerFeeRate": 0.1,
            "tradeTakerFeeRate": 0.1,
            "tradeFeeUnit": "USDT",
            "minPrice": 0.01,
            "minPriceUnit": "USDT",
            "minAmountDecimal": 3,
            "minPriceDecimal": 2,
            "trade": true
        },
        //...이하 생략됨
    ]
}
```
