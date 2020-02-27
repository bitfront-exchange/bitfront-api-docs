# BITFRONT API Development Guide

암호화폐 거래소인 BITFRONT는 거래를 프로그래밍할 수 있도록 API를 제공합니다.

본 문서에서는 BITFRONT API의 기본 정보를 기술하고 상세한 예시를 제공합니다.

> **NOTE**
> 
> 웹 버전 문서를 보려면 [https://bitfront-exchange.github.io/bitfront-api-docs](https://bitfront-exchange.github.io/bitfront-api-docs/)를 방문하세요.

  - [Overview](/ko/1_Overview.md)
  - [Authentication and security](/ko/2_Authentication_and_Security_Policy.md)
  - [Reference](/ko/3_Reference.md)
      - Public API
          - [Server time](/ko/api/public/v1-public-time-get.md)
      - Market API
          - [Market coin pair policy](/ko/api/market/v1-market-public-coins-pairPolicy-get.md)
          - [Tick values](/ko/api/market/v1-market-public-currentTickValue-get.md)
          - [Order book](/ko/api/market/v1-market-public-orderBooks-get.md)
          - [Market trade history](/ko/api/market/v1-market-public-tradeHistory-get.md)
      - Trade API
          - [Limit order](/ko/api/trade/v1-trade-limitOrders-post.md)
          - [Market order](/ko/api/trade/v1-trade-marketOrders-post.md)
          - [Open orders](/ko/api/trade/v1-trade-openOrders-get.md)
          - [Cancellation](/ko/api/trade/v1-trade-orders-delete.md)
          - [Cancellation of all open orders](/ko/api/trade/v1-trade-openOrders-delete.md)
      - Account API
          - [Balance](/ko/api/account/v1-account-balances-get.md)
          - [Currency balance](/ko/api/account/v1-account-balances-currency-get.md)
          - [User trade history v2](/ko/api/account/v2-account-tradeHistory-get.md)
          - [Order information v2](/ko/api/account/v2-account-orders-orderID-get.md)
          - [Coin transfer history](/ko/api/account/v1-account-transactionHistory-get.md)
  - [Glossary](/ko/5_Terms.md)
  - [Revision history](/ko/0_About_This_Document.md)
  - [LICENSE NOTICE](/ko/LICENSE.md)
