# Order book

주문장에서 지정한 coin pair의 거래를 조회합니다.

> **Note**
> 
> 아 API는 API KEY 발급 없이 사용할 수 있습니다.

## Endpoint URI

    GET https://openapi.bitfront.me/v1/market/public/orderBooks?coinPair={coinPair}&depth={depth}

## Request parameters

| Name       | Description                                                                                                                                                                                                                      | Type    | Loc.  | Required |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ----- | -------- |
| `coinPair` | 조회할 [coin pair](/ko/5_Terms.md#coin-pair). [Currency](/ko/5_Terms.md#currency-for-coin-trading)와 [Market](/ko/5_Terms.md#market-for-coin-trading)을 점(‘.’)으로 구분한 문자열로, 대소문자를 구분합니다. <br/>예를 들어 “BCH.ETH”은 ETH으로 BCH를 거래한다는 의미입니다. | String  | query | O        |
| `depth`    | 조회할 주문장 개수. 1\~1000의 값이어야 하며, 기본값은 100입니다.                                                                                                                                                                                       | Integer | query |          |

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

주문장은 bid 값과 ask 값을 가집니다.
이 데이터는 키-목록 맵으로, 키는 “BID”나 “ASK”이 되고, 목록의 각 항목은 가격과 총수량을 포함합니다. 객체의 상세 설명을 참고하십시오.

| Name  | Description                                           | Type  | Included |
| ----- | ----------------------------------------------------- | ----- | -------- |
| `BID` | [priceAmount](#priceamount)의 배열입니다. 대상 객체 설명을 참고하십시오. | array |          |
| `ASK` | [priceAmount](#priceamount)의 배열입니다. 대상 객체 설명을 참고하십시오. | array |          |

### priceAmount

  - Type: object

| Name     | Description | Type   | Included |
| -------- | ----------- | ------ | -------- |
| `price`  | 주문의 가격      | double |          |
| `amount` | 주문의 총수량     | double |          |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1525078219216,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": {
      "BID": [
          {
              "price": 2748.72327228786,
              "amount": 2.23394525
          },
          {
              "price": 2746.69921216344,
              "amount": 0.9357132
          },
          {
              "price": 2746.6714729717582,
              "amount": 2.66085382
          },
          {
              "price": 2746.6598167849634,
              "amount": 1.53825317
          },
          {
              "price": 2746.648512115077,
              "amount": 6.38919104
          }
      ],
      "ASK": [
          {
              "price": 2759.0795123971097,
              "amount": 0.66742494
          },
          {
              "price": 2759.0790474341684,
              "amount": 2.42865008
          },
          {
              "price": 2759.057958916535,
              "amount": 3.47240736
          },
          {
              "price": 2759.0549591332588,
              "amount": 5.11662824
          },
          {
              "price": 2759.0492733250644,
              "amount": 6.18008926
          }
      ]
  }
}
```
