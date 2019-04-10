# 인증 및 보안 정책

BITBOX API (beta)는 사용자 보호를 위해 인증 및 보안 정책을 적용합니다. API를 사용하는 모든 사용자는 아래 정책을 따라야 합니다.

## API KEY와 API SECRET

BITBOX API (beta)를 사용하려면 반드시 API KEY와 API SECRET이 있어야 합니다.

  - API KEY와 API SECRET 발급 신청은 [BITBOX 공지 사항](https://www.bitbox.me/notice/20091925)을 참고하십시오.
    발급 신청을 하려면 [BITBOX](http://bitbox.me) 회원으로 가입해야 합니다.
  - API KEY와 API SECRET은 대소문자를 구분합니다.

> **주의**
> 
> 인증 정보는 개인이 안전한 곳에 보관해야 합니다. 민감한 정보를 보호하기 위해 이 정보를 두 번 다시 출력하지 않으므로 API KEY를 잃어버리면 기존 API KEY를 삭제하고 새로 발급해야 합니다.

## 필수 파라미터

### Public API

`/v1/public`으로 시작하는 API는 요청 HTTP 헤더(header)에 다음 파라미터를 포함시켜 전송해야 합니다.

| **파라미터 이름 ** | **설명**                      |
| :----------: | --------------------------- |
| `X-API-KEY`  | 사용자가 BITBOX에서 발급받은 API\_KEY |

아래는 요청 예시입니다.

``` bash
curl https://openapi.bitbox.me/v1/public/time \
  --header "X-API-KEY: <Your API KEY>"
```

### Trade, Market, Account API

`/v1/public`으로 시작하는 것을 제외한 모든 API는 요청 HTTP 헤더에 다음 파라미터를 포함시켜 전송해야 합니다.

| **파라미터 이름**       | **설명**                                              |
| ----------------- | --------------------------------------------------- |
| `X-API-KEY`       | 사용자가 BITBOX에서 발급받은 API KEY                          |
| `X-API-SIGN`      | [서명 정책](#서명-정책)에 따라 생성한 HMAC SHA256 서명              |
| `X-API-TIMESTAMP` | 밀리초 단위 UTC Unix Epoch 타임스탬프                         |
| `X-API-NONCE`     | 같은 타임스탬프를 가진 요청에서 사용되지 않은 5자리의 임의의 양의 정수 (예, 12345) |

아래는 요청 예시입니다.

``` bash
curl https://openapi.bitbox.me/v1/market/public/currentTickValue?coinPair=BCH.ETH \
  --header "X-API-KEY: <your api key>" \
  --header "X-API-SIGN: <the user generated message signature>" \
  --header "X-API-TIMESTAMP: <a timestamp for your request>" \
  --header "X-API-NONCE: <a nonce value>"
```

## 타임스탬프 검증

API 서버는 API 요청이 왔을 때 그 타임스탬프와 서버의 타임스탬프를 비교하여 해당 요청이 시간적으로 적합한 요청인지 확인합니다. 시간적으로 안전하지 않은 요청은 거절합니다.

시간상 부적합으로 판단하는 조건은 다음과 같습니다.

  - API 요청의 타임스탬프가 서버의 타임스탬프보다 1초 이상 빠르면 요청을 거절합니다.
  - API 요청 헤더의 타임스탬프와 서버의 타임스탬프를 비교하여 정해진 시간 간격을 초과하면 요청을 거절합니다. 정해진 시간 간격은 API에 따라 다릅니다.
      - 주문 취소 요청은 시간 간격이 10초를 초과하면 요청 거절
      - 그 외의 요청은 시간 간격이 5초를 초과하면 요청 거절

## RPS 제한 정책

하나의 API KEY를 사용한 API 요청은 다음처럼 횟수를 제한합니다.

  - 주문 또는 주문 취소 요청일 경우, 하나의 API KEY는 30 RPS를 허용합니다.
  - 주문 또는 주문 취소 외의 요청일 경우, 하나의 API KEY는 50 RPS를 허용합니다.
  - 주문 또는 주문 취소 요청일 경우, 각 요청 간 시간 간격은 최소 10ms를 권장합니다. 이보다 짧으면 요청을 처리하는데 실패할 수 있습니다.
  - 제한 RPS를 초과하는 요청은 거절합니다.

## 서명 정책

API 요청에는 반드시 서명이 있어야 합니다.

  - 사전에 발급받은 API SECRET을 이용해 논스값(nonce), 타임스탬프, 메서드, 요청 경로(request path), 쿼리 문자열(query string), 요청 본문(request body)을 차례대로 붙여서 만든 문자열로 HMAC-SHA256 서명을 만듭니다.

  - 논스값은 헤더 파라미터의 `X-API-NONCE`와 같은 값으로, 5자리 임의의 양수 정수이며 같은 타임스탬프 범위 내에서 사용하지 않은 값이어야 합니다.

  - **타임스탬프는 헤더 파라미터의 `X-API-TIMESTAMP`와 같은 값이며, UTC Unix Epoch 형식입니다.**

  - 메서드는 API 요청의 HTTP 메서드이며, 대문자여야 합니다.

  - 요청 경로는 요청 URI의 path 부분을 의미합니다.
    
    예를 들어, 요청 URI가 `https://openapi.bitbox.me/v1/market/public/orderBooks?coinPair=ETH.BTC&depth=5`이면, 요청 경로는 `/v1/market/public/orderBooks`입니다.

  - 쿼리 문자열은 요청 URI의 쿼리 파라미터를 의미합니다.
    
    예를 들어, 요청 URI가 `https://openapi.bitbox.me/v1/market/public/orderBooks?coinPair=ETH.BTC&depth=5`이면, 쿼리 문자열은 `coinPair=ETH.BTC&depth=5`입니다.
    요청 경로와 구분하는 물음표(‘?’)는 포함하지 않으니 주의하십시오.
    
    POST 요청일 때는 생략 가능합니다.

  - 요청 본문은 HTTP 요청 본문에 포함된 문자열로, 쿼리 문자열과 같이 각 파라미터의 키와 값을 ‘&’과’=’로 연결한 형식입니다.
    
    GET 요청일 때는 생략 가능합니다.

### 생성 예제

아래 예제는 서명을 생성하고, 이를 이용해 요청을 보내는 방법을 보여줍니다.

예제에서 사용할 기본 데이터는 다음과 같습니다.

| 항목         | 값                                |
| ---------- | -------------------------------- |
| API KEY    | 6W206egN32nCQ0VB                 |
| API SECRET | dwjnGqCVzfHlW6Q9r4BjXpmiK1WCdMBI |
| 타임스탬프      | 1523864107010                    |
| 논스값        | 12345                            |

**예제 1: 쿼리 문자열 방식**

첫 번째 예제는 쿼리 문자열 방식으로 파라미터를 전달합니다.
예제의 API 요청 정보는 다음과 같다고 가정합니다.

| 항목       | 값                                  |
| -------- | ---------------------------------- |
| HTTP 메서드 | GET                                |
| 요청 경로    | `/v1/market/public/orderBooks`     |
| 파라미터     | `coinPair`: ETH.BTC, `depth`: 1000 |

서명에 필요한 문자열은 다음처럼 만들 수 있습니다.

![](images/signature_ex1.png)

LINUX에서 `echo`와 `openssl`을 사용해 HMAC SHA256 서명을 생성합니다.

``` bash
echo -n "123451523864107010GET/v1/market/public/orderBookscoinPair=ETH.BTC&depth=1000" \
  | openssl dgst -sha256 -hmac "dwjnGqCVzfHlW6Q9r4BjXpmiK1WCdMBI"
  (stdin)= 4e211ada0a332cb8611560c2109eed51618ea4aed3976eb973e9edae12d433e4
```

`curl`을 이용해 생성한 서명을 API 요청 헤더에 전달합니다.

``` bash
curl --header "X-API-KEY: 6W206egN32nCQ0VB" \
     --header "X-API-SIGN: 4e211ada0a332cb8611560c2109eed51618ea4aed3976eb973e9edae12d433e4" \
     --header "X-API-TIMESTAMP: 1523864107010" \
     --header "X-API-NONCE: 12345" \
     --header 'content-type: application/x-www-form-urlencoded' \
     -X GET '/v1/market/public/orderBooks?coinPair=ETH.BTC&depth=1000' \
```

**예제 2: 요청 본문 방식**

두 번째 예제는 요청 본문 방식으로 파라미터를 전달합니다.
예제의 API 요청 정보는 다음과 같다고 가정합니다.

| 항목       | 값                                                    |
| -------- | ---------------------------------------------------- |
| HTTP 메서드 | POST                                                 |
| 요청 경로    | `/v1/trade/marketOrders`                             |
| 파라미터     | `quantity`: 1, `coinPair`: ETH.BTC, `orderSide`: BUY |

서명에 필요한 문자열은 다음처럼 만들 수 있습니다.

![](images/signature_ex2.png)

LINUX에서 `echo`와 `openssl`을 사용해 HMAC SHA256 서명을 생성합니다.

``` bash
$ echo -n "123451523864107010POST/v1/trade/marketOrdersquantity=1&coinPair=BCH.ETH&orderSide=BUY" | openssl dgst -sha256 -hmac "dwjnGqCVzfHlW6Q9r4BjXpmiK1WCdMBI"
  (stdin)=03838b25c336e0a6fb3617b9b07c9da9d91d96ab0e61598aa7e6cd1396b2b3ef
```

`curl`을 이용해 생성한 서명을 API 요청 헤더에 전달합니다.

``` bash
curl --header "X-API-KEY: 6W206egN32nCQ0VB" \
     --header "X-API-SIGN: 03838b25c336e0a6fb3617b9b07c9da9d91d96ab0e61598aa7e6cd1396b2b3ef" \
     --header "X-API-TIMESTAMP: 1523864107010" \
     --header "X-API-NONCE: 12345" \
     --header 'content-type: application/x-www-form-urlencoded' \
     -X POST 'https://openapi.bitbox.me/v1/trade/marketOrders' \
     --data 'quantity=1&coinPair=BCH.ETH&orderSide=BUY'
```
