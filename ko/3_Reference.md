# Reference

BITBOX API가 제공하는 모든 API의 상세 설명을 기술합니다.

> **Note**
> 
> [LINK](http://link.network)의 공식 티커 심볼에 따라, BITBOX의 API는 [Currency](/5_Terms.md#currency-for-coin-trading)가 LINK일 때 “LN”로 표기하여 반환합니다.
> 단, 주문 조회 시 2019년 3분기까지 한시적으로 “LINK”로 반환하는 [Order information API(`/v1/account/orders/orderID`)](/api/account/v1-account-orders-orderID-get.md#order-information-deprecated)를 제공합니다.

> **Tip**
> 
> 요청 파라미터의 설명에서 `Loc.` 항목은 파라미터를 전달하는 위치를 나타냅니다.
> 
>   - path: 파라미터를 요청 경로로 전달합니다.
> 
>   - query: 파라미터를 쿼리 스트링으로 전달합니다.
> 
>   - header: 파라미터를 헤더 속성으로 전달합니다.
> 
>   - body: 파라미터를 요청 본문으로 전달합니다.

## Public API

  - [Server time](api/public/v1-public-time-get.md)

## Market API

  - [Market coin pair policy](api/market/v1-market-public-coins-pairPolicy-get.md)
  - [Tick values](api/market/v1-market-public-currentTickValue-get.md)
  - [Order book](api/market/v1-market-public-orderBooks-get.md)
  - [Market trade history](api/market/v1-market-public-tradeHistory-get.md)

## Trade API

  - [Limit order](api/trade/v1-trade-limitOrders-post.md)
  - [Market order](api/trade/v1-trade-marketOrders-post.md)
  - [Open orders](api/trade/v1-trade-openOrders-get.md)
  - [Cancellation](api/trade/v1-trade-orders-delete.md)
  - [Cancellation of all open orders](api/trade/v1-trade-openOrders-delete.md)

## Account API

  - [Balance](api/account/v1-account-balances-get.md)
  - [Currency balance](api/account/v1-account-balances-currency-get.md)
  - [User trade history v2](api/account/v2-account-tradeHistory-get.md)
  - [Order information (Deprecated)](api/account/v1-account-orders-orderID-get.md)
  - [Order information v2](api/account/v2-account-orders-orderID-get.md)
  - [Coin transfer history](api/account/v1-account-transactionHistory-get.md)
