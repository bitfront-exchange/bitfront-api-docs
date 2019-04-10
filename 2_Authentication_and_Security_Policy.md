# Authentication and security policy

BITBOX API (beta) has an authentication and security policy for user protection.
All users who want to use the API must comply with the policy.

## API KEY and API SECRET

To use BITBOX API (beta), you must have your own API KEY and API SECRET.

  - To gain an API KEY and an API SECRET, see the [notice in BITBOX](https://www.bitbox.me/notice/20091925).
    You must sign up to [BITBOX](http://bitbox.me) to get API KEY and API SECRET.
  - API KEYs and API SECRETs are case sensitive.

> **Note**
> 
> You must store these credentials in a safe place. We will not show them again for your protection. If you lose your API KEY, you must create a new one.

## Mandatory parameters

### For public APIs

For public APIs which start with `/v1/public`, the following parameter must be included in the HTTP header.

| **Parameter name** | **Description**                  |
| ------------------ | -------------------------------- |
| `X-API-KEY`        | API KEY of user issued by BITBOX |

Here is an example of a request.

``` bash
curl https://openapi.bitbox.me/v1/public/time \
  --header "X-API-KEY: <Your API KEY>"
```

### For trade, market, and account APIs

For all APIs other than public APIs, the following parameters must be included in the HTTP header.

| **Parameter name** | **Description**                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------- |
| `X-API-KEY`        | API KEY of user issued by BITBOX                                                                          |
| `X-API-SIGN`       | HMAC-SHA256 signature, pre-generated in compliance with the [Signature policy](#signature-policy) section |
| `X-API-TIMESTAMP`  | UTC Unix Epoch in milliseconds                                                                            |
| `X-API-NONCE`      | A 5-digit arbitrary positive integer that has not been used before within the same timestamp (e.g. 12345) |

Here is an example of a request.

``` bash
curl https://openapi.bitbox.me/v1/market/public/currentTickValue?coinPair=BCH.ETH \
  --header "X-API-KEY: <your API KEY>" \
  --header "X-API-SIGN: <the user generated message signature>" \
  --header "X-API-TIMESTAMP: <a timestamp for your request>" \
  --header "X-API-NONCE: <a nonce value>"
```

## Timing security

Upon receiving user requests, the API server compares the timestamp of the requests with the current timestamp in the server as a safety measure.

Requests are deemed as unsafe and rejected under the following conditions:

  - When the request timestamp is more than 1 seconds earlier than the server timestamp, the request is rejected.
  - When the time difference between the timestamps is outside the acceptable range, the request is rejected. The acceptable range varies depending on the API.
      - For cancellation requests, the time difference must be less than 10 seconds.
      - For all other requests, the time difference must be less than 5 seconds.

## RPS limit policy

The number of requests per API KEY is limited as follows:

  - For orders or order cancellations, one API KEY handles a maximum of 30 RPS.
  - For requests other than orders or order cancellations, one API KEY handles a maximum of 50 RPS.
  - For orders or order cancellations, the recommended interval between requests is at least 10ms. Any interval shorter than the recommendation can result in failure.
  - Any requests exceeding the RPS limit are rejected.

## Signature policy

All API request must be signed.

  - Signatures must be HMAC-SHA256 signatures, which can be constructed using user API SECRET with a concatenated string of nonce, timestamp, method, requestPath, queryString, and requestBody.

  - Nonce is the value stored in `X-API-NONCE`. Nonce must be a 5-digit arbitrary positive integer that has not been used before within the same timestamp.

  - **Timestamp is the value stored in `X-API-TIMESTAMP`, which is Unix Epoch of UTC.**

  - Method is the HTTP method of the request and must be in uppercase.

  - RequestPath is the path of the requested URI.
    
    For example, the requestPath is `/v1/market/public/orderBooks` when the URI is `https://openapi.bitbox.me/v1/market/public/orderBooks?coinPair=ETH.BTC&depth=5`.

  - QueryString is the query parameter string of the requested URI.
    
    For example, the queryString is `coinPair=ETH.BTC&depth=5` when the URI is `https://openapi.bitbox.me/v1/market/public/orderBooks?coinPair=ETH.BTC&depth=5`.
    Note that “?”, the delimiter character, is excluded.
    
    QueryString is omissible for POST requests.

  - RequestBody is the body string of the request. It must be a string concatenation of body parameters with “&” and “=” as delimiters.
    
    Requestbody is omissible for GET requests.

### Generating a signature

These examples show how to generate a signature and send a request using the generated signature.

These examples use the following data:

| **Item**   | **Value**                        |
| :--------- | :------------------------------- |
| API KEY    | 6W206egN32nCQ0VB                 |
| API SECRET | dwjnGqCVzfHlW6Q9r4BjXpmiK1WCdMBI |
| Timestamp  | 1523864107010                    |
| Nonce      | 12345                            |

**Example 1: Query string**

In this example, the request passes parameters as a query string.
The API for the example is as follows:

| **Item**     | **Value**                          |
| :----------- | :--------------------------------- |
| HTTP Method  | GET                                |
| Request path | `/v1/market/public/orderBooks`     |
| Parameters   | `coinPair`: ETH.BTC, `depth`: 1000 |

The target string for the signature is as follows:

![](images/signature_ex1.png)

In LINUX, generate the HMAC-SHA256 signature by using the `echo` and `openssl` commands.

``` bash
echo -n "123451523864107010GET/v1/market/public/orderBookscoinPair=ETH.BTC&depth=1000" | openssl dgst -sha256 -hmac "dwjnGqCVzfHlW6Q9r4BjXpmiK1WCdMBI"
(stdin)= 4e211ada0a332cb8611560c2109eed51618ea4aed3976eb973e9edae12d433e4
```

Next, send an API request including the signature by using the `curl` command.

``` bash
curl --header "X-API-KEY: 6W206egN32nCQ0VB" \
     --header "X-API-SIGN: 4e211ada0a332cb8611560c2109eed51618ea4aed3976eb973e9edae12d433e4" \
     --header "X-API-TIMESTAMP: 1523864107010" \
     --header "X-API-NONCE: 12345" \
     --header 'content-type: application/x-www-form-urlencoded' \
     -X GET '/v1/market/public/orderBooks?coinPair=ETH.BTC&depth=1000' \
```

**Example 2: Request body**

In this example, the request passes parameters as a body string.
The API for the example is as follows:

| **Item**     | **Value**                                            |
| :----------- | :--------------------------------------------------- |
| HTTP Method  | POST                                                 |
| Request path | `/v1/trade/marketOrders`                             |
| Parameters   | `quantity`: 1, `coinPair`: ETH.BTC, `orderSide`: BUY |

The target string for the signature is as follows:

![](images/signature_ex2.png)

In LINUX, generate the HMAC-SHA256 signature by using the `echo` and `openssl` commands.

``` bash
echo -n "123451523864107010POST/v1/trade/marketOrdersquantity=1&coinPair=BCH.ETH&orderSide=BUY" | openssl dgst -sha256 -hmac "dwjnGqCVzfHlW6Q9r4BjXpmiK1WCdMBI"
(stdin)=03838b25c336e0a6fb3617b9b07c9da9d91d96ab0e61598aa7e6cd1396b2b3ef
```

Next, send an API request including the signature by using the `curl` command.

``` bash
curl --header "X-API-KEY: 6W206egN32nCQ0VB" \
     --header "X-API-SIGN: 03838b25c336e0a6fb3617b9b07c9da9d91d96ab0e61598aa7e6cd1396b2b3ef" \
     --header "X-API-TIMESTAMP: 1523864107010" \
     --header "X-API-NONCE: 12345" \
     --header 'content-type: application/x-www-form-urlencoded' \
     -X POST 'https://openapi.bitbox.me/v1/trade/marketOrders' \
     --data 'quantity=1&coinPair=BCH.ETH&orderSide=BUY'
```
