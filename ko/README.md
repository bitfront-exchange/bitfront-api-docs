
# BITBOX API Development Guide

암호화폐 거래소인 BITBOX는 거래를 프로그래밍할 수 있도록 API를 제공합니다.

BITBOX API를 사용하면 BITBOX 사이트에 접속하지 않고도 계정 상태나 거래 내역을 확인할 수 있고, 암호화폐를 사거나 팔 수 있습니다. 또 설정한 조건에 따라 자동으로 주문을 할 수도 있습니다. 예를 들어 어떤 암호화폐의 가격이 5%를 초과하여 하락할 때 특정 양을 구매하는 것이 가능합니다.

여기서는 BITBOX API의 기본 정보를 기술하고 상세한 예시를 제공합니다.

> **NOTE**
>
> 웹 버전 문서를 보려면 [https://bitbox-exchange.github.io/bitbox-api-docs](https://bitbox-exchange.github.io/bitbox-api-docs/)를 방문하세요.

* [Overview](/1_Overview.md)
* [Authentication and security](/2_Authentication_and_Security_Policy.md)
* [Reference](/3_Reference.md)
  * Public API
      * [Server time](/api/public/v1-public-time-get.md)
  * Market API
      * [Market coin pair policy](/api/market/v1-market-public-coins-pairPolicy-get.md)
      * [Tick values](/api/market/v1-market-public-currentTickValue-get.md)
      * [Order book](/api/market/v1-market-public-orderBooks-get.md)
      * [Market trade history](/api/market/v1-market-public-tradeHistory-get.md)
  * Trade API
      * [Limit order](/api/trade/v1-trade-limitOrders-post.md)
      * [Market order](/api/trade/v1-trade-marketOrders-post.md)
      * [Open orders](/api/trade/v1-trade-openOrders-get.md)
      * [Cancellation](/api/trade/v1-trade-orders-delete.md)
      * [Cancellation of all open orders](/api/trade/v1-trade-openOrders-delete.md)
  * Account API
      * [Balance](/api/account/v1-account-balances-get.md)
      * [Currency balance](/api/account/v1-account-balances-currency-get.md)
      * [User trade history v2](/api/account/v2-account-tradeHistory-get.md)
      * [Order information (Deprecated)](/api/account/v1-account-orders-orderID-get.md)
      * [Order information v2](/api/account/v2-account-orders-orderID-get.md)
      * [Coin transfer history](/api/account/v1-account-transactionHistory-get.md)
* [Glossary](/5_Terms.md)
* [Revision history](/0_About_This_Document.md)
* [LICENSE NOTICE](/LICENSE.md)
