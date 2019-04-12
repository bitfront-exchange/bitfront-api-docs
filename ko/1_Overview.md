# 개요

암호화폐 거래소인 BITBOX는 거래를 프로그래밍할 수 있도록 API를 제공합니다.

BITBOX API를 사용하면 BITBOX 사이트에 접속하지 않고도 계정 상태나 거래 내역을 확인할 수 있고, 암호화폐를 사거나 팔 수 있습니다. 또 설정한 조건에 따라 자동으로 주문을 할 수도 있습니다. 예를 들어 어떤 암호화폐의 가격이 5%를 초과하여 하락할 때 특정 양을 구매하는 것이 가능합니다.

여기서는 BITBOX API의 기본 정보를 기술하고 상세한 예시를 제공합니다.

## 사전 준비

BITBOX API는 REST API입니다.
모든 요청과 응답은 HTTPS로 전송되므로 HTTPS를 지원하는 어떤 플랫폼에서든 API를 호출할 수 있습니다.
요청에 문제가 발생하지 않도록 여기서 기술하는 기본 정보와 각 API의 상세 설명을 자세히 읽어보시기 바랍니다.

BITBOX API를 사용하려면 API KEY를 발급받아야 합니다. [BITBOX 홈페이지](https://bitbox.me)에 로그인한 후 “계정” \> “Open API” 메뉴에서 발급 신청하십시오.

발급이 완료되면 API KEY와 API SECRET 같은 인증 정보를 받게 됩니다.
API 요청에는 반드시 API KEY를 헤더에 넣어 전달해야 하며, API 서버는 유효한 API KEY를 가진 요청만 처리합니다.
API SECRET은 API 요청을 서명하기 위한 비밀 키입니다. 상세한 것은 [인증 및 보안 정책](2_Authentication_and_Security_Policy.md#인증-및-보안-정책)을 참고하십시오.

## Endpoint

BITBOX API의 endpoint는 다음과 같습니다.

``` postscript
https://openapi.bitbox.me/{version}/{api_path}?{query_string}
```

  - `https://openapi.bitbox.me/` 는 API의 기본 URL입니다.
  - `version`은 사용할 API 집합의 버전입니다.
  - `api_path`는 호출할 API의 경로입니다.
  - `query_string`은 쿼리 파라미터의 집합입니다. 각 파라미터는 `key=value` 쌍이며 각각 ’&’으로 구분합니다.

## 요청

BITBOX API의 API 요청은 다음 조건을 따라야 합니다.

  - 모든 API 요청은 HTTPS로 전송합니다.
  - API에 따라 GET, POST, PUT, DELETE 메서드를 사용할 수 있습니다.
  - **POST, PUT, DELETE 메서드로 요청을 보낼 때, 파라미터는 쿼리 문자열(query string)이나 `Content-Type`이 `application/x-www-form-urlencoded`인 요청 본문(request body)으로 전달해야 합니다.** 쿼리 문자열과 요청 본문을 모두 사용할 수도 있습니다.
  - API 서버는 등록된 IP를 가진 서버에서 전송한 요청만 처리하므로 반드시 [API KEY](2_Authentication_and_Security_Policy.md#api-key와-api-secret)에 허용 IP 목록을 등록해야 합니다.
  - 요청은 반드시 서명을 포함해야 합니다. 상세 내용은 [서명 정책](2_Authentication_and_Security_Policy.md#서명-정책)에서 기술합니다.
  - 하나의 서명은 한 번만 유효하며 중복 서명을 사용하면 API 서버가 요청을 거절합니다.
  - BITBOX API는 다음의 RPS 정책을 따릅니다.
      - 주문 또는 주문 취소 요청일 경우, 하나의 API KEY는 30 RPS를 허용합니다.
      - 주문 또는 주문 취소 외의 요청일 경우, 하나의 API KEY는 50 RPS를 허용합니다.
      - 주문 또는 주문 취소 요청일 경우, 각 요청 간 시간 간격은 최소 10ms를 권장합니다. 이보다 짧으면 요청을 처리하는데 실패할 수 있습니다.

## 응답

BITBOX API는 요청에 대한 결과를 응답 객체(Response Object)로 전달합니다.
API 서버에 문제가 없을 때 응답의 HTTP 상태 코드는 200이며, 상세한 처리 결과는 수신한 응답 객체를 통해 확인할 수 있습니다.

> **주의**
> 
> HTTP 상태 코드는 요청 처리 상태를 나타내지 않습니다. 응답의 HTTP 상태 코드가 200 OK인 것이 요청이 성공적으로 처리되었다는 의미는 아닙니다.
> 상세 내용은 아래의 응답 객체 설명을 참고하십시오.

응답 객체의 구성은 다음과 같습니다.

| 필드              | 설명                                                                                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `responseData`  | 실제 결과 데이터를 JSON 포맷 형태로 저장합니다. 구조는 API 별로 다르므로 각 [API 설명](3_Reference.md#reference)을 참고하십시오.                                                                               |
| `responseTime`  | API 서버의 응답 시간을 보여줍니다.                                                                                                                                                     |
| `statusCode`    | 요청 결과의 상태를 나타냅니다. 요청이 성공적으로 처리되었는지 보려면 반드시 이 필드를 확인해야 합니다. 이 필드 값이 1000이면 요청이 잘 처리되었다는 뜻이며, 그 외의 값은 요청이 실패한 것으로 간주합니다. 자세한 정보는 [`statusCode` 정의](#statuscode-정의)를 참고하십시오. |
| `statusMessage` | 요청 결과의 상세한 정보를 제공합니다. `statusCode`가 1000이 아닐 때, 이 필드에서 상세한 실패 원인을 확인할 수 있습니다.                                                                                             |
| `timezone`      | `responseTime`의 기준 시간을 나타내며, 항상 “UTC”입니다. 아래를 참고하십시오.                                                                                                                     |

> **참고**
> 
> 모든 API의 타임스탬프는 밀리초 단위의 [UTC Unix Epoch](https://en.wikipedia.org/wiki/Unix_time)입니다.

아래는 응답 객체의 예시입니다.

``` json
// An example of a normal response (1000)
{
    "timezone": "UTC",
    "responseTime": 1525066555636,
    "statusCode": 1000,
    "statusMessage": "SUCCESS",
    "responseData": {
      ......
    }
}

// An example of a failed response
{
    "timezone": "UTC",
    "responseTime": 1525264994801,
    "statusCode": 4001,
    "statusMessage": "The request has to be sent with X-API-Key, X-API-SIGN, X-API-TIMESTAMP."
}
```

## statusCode 정의

응답 객체에서 사용하는 `statusCode`와 `statusMessage`의 목록은 다음과 같습니다.

| **`statusCode`** | **`statusMessage`**                                     | **설명**                                                                                                                                               |
| :--------------: | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
|       1000       | Success                                                 | 요청이 성공적으로 처리되었습니다.                                                                                                                                   |
|       1202       | Member not found                                        | 해당 회원이 없습니다.                                                                                                                                         |
|       3113       | Currency pair system is in maintenance                  | Currency pair 시스템이 유지보수 중입니다.                                                                                                                        |
|       3203       | Unit price cannot be lower than the minimum value       | 단위 가격이 최솟값보다 작습니다.                                                                                                                                   |
|       3204       | Unit price is out of scale                              | 단위 가격이 minimum price decimal보다 작습니다. [Market coin pair policy](api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy)를 확인하십시오. |
|       3211       | Amount is too low                                       | 총수량이 최솟값보다 작습니다.                                                                                                                                     |
|       3212       | Amount is too high to order                             | 총수량이 너무 높아 주문할 수 없습니다.                                                                                                                               |
|       3213       | AMOUNT has out of scale                                 | 총수량이 minimum amount decimal보다 작습니다. [Market coin pair policy](api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy)를 확인하십시오.  |
|       3221       | Volume is too low                                       | 규모가 최솟값보다 작습니다.                                                                                                                                      |
|       3222       | Volume is too high to order                             | 규모 값이 너무 높아 주문할 수 없습니다.                                                                                                                              |
|       3301       | Not enough balance for an order                         | 주문 요청한 만큼의 잔액을 가지고 있지 않습니다.                                                                                                                          |
|       3302       | Not enough remained amount for a request                | 해당 회원에게 이 요청을 처리할만한 주문 수량이 없습니다.                                                                                                                     |
|       3311       | Active order count exceed                               | 활성 주문 수를 초과했습니다.                                                                                                                                     |
|       3321       | Original request not found                              | 원본 요청을 찾을 수 없습니다.                                                                                                                                    |
|       3401       | Internal core system error                              | 내부 코어 시스템에 에러가 발생했습니다.                                                                                                                               |
|       4000       | Bad request                                             | 잘못된 요청입니다.                                                                                                                                           |
|       4001       | X-API-Key, X-API-SIGN, or X-API-TIMESTAMP is missing    | 헤더에 필수 파라미터가 없습니다.                                                                                                                                   |
|       4002       | Invalid parameter value                                 | 유효하지 않은 파라미터입니다.                                                                                                                                     |
|       4003       | Invalid signature                                       | 유효하지 않은 서명입니다.                                                                                                                                       |
|       4005       | Duplicate signature usage detected                      | 요청의 서명이 이미 사용되었습니다(중복 요청).                                                                                                                           |
|       4006       | Invalid ‘orderSide’ parameter                           | `orderSide`값은 “SELL”이나 “BUY”여야 합니다.                                                                                                                  |
|       4007       | Invalid ‘quantity’ parameter (should be greater than 0) | `quantity`값은 0보다 커야 합니다.                                                                                                                             |
|       4008       | Invalid ‘price’ parameter (should be greater than 0)    | `price`값은 0보다 커야 합니다.                                                                                                                                |
|       4009       | Invalid ‘coinPair’                                      | [Coin pair](5_Terms.md#coin-pair)가 유효하지 않습니다.                                                                                                        |
|       4010       | Invalid ‘market’                                        | [Market](5_Terms.md#market-for-coin-trading)이 유효하지 않습니다.                                                                                             |
|       4011       | Invalid ‘currency’                                      | [Currency](5_Terms.md#currency-for-coin-trading)가 유효하지 않습니다.                                                                                         |
|       4012       | Mandatory parameter not passed                          | 필수 파라미터가 없습니다.                                                                                                                                       |
|       4013       | Invalid timestamp                                       | 타임스탬프가 유효하지 않습니다.                                                                                                                                    |
|       4014       | Invalid transfer type                                   | 전송 타입이 유효하지 않습니다.                                                                                                                                    |
|       4015       | Invalid page number                                     | 페이지 번호가 유효하지 않습니다.                                                                                                                                   |
|       4016       | Invalid page size                                       | 페이지 크기 값이 유효하지 않습니다.                                                                                                                                 |
|       4017       | Unsupported request method                              | 요청 메서드를 지원하지 않습니다.                                                                                                                                   |
|       4018       | Invalid X-API-NONCE                                     | `X-API-NONCE`는 5자리 양수여야 합니다.                                                                                                                         |
|       4101       | Account not found                                       | 해당 계정이 존재하지 않습니다.                                                                                                                                    |
|       4102       | Unsupported currency                                    | 해당 암호화폐를 지원하지 않습니다.                                                                                                                                  |
|       5000       | Internal server side error                              | API 서버가 요청을 받았으나 비즈니스 로직에 오류가 발생했습니다.                                                                                                                |
|       5001       | Internal timeout error                                  | API 서버가 요청을 받았으나 서버 내에서 타임아웃이 발생했습니다.                                                                                                                |
|       5002       | Socket timeout exception                                | API 서버가 요청을 받았으나 소켓 타임아웃이 발생했습니다.                                                                                                                    |
|       6000       | Unauthorized request                                    | 인증되지 않은 요청입니다.                                                                                                                                       |
|       6001       | Unregistered API KEY                                    | API KEY가 등록되지 않았습니다.                                                                                                                                 |
|       6002       | Invalid API KEY                                         | API KEY가 유효하지 않습니다.                                                                                                                                  |
|       6003       | Unauthorized IP                                         | 허가되지 않은 IP에서 요청했습니다.                                                                                                                                 |
|       6004       | API RPS limit exceeded                                  | API RPS 제한을 초과했습니다.                                                                                                                                  |
|       6005       | Invalid request timestamp                               | 요청의 타임스탬프가 유효하지 않습니다.                                                                                                                                |
