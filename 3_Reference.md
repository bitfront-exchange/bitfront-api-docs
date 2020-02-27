# Reference

In this section, you can find the detailed descriptions of each API included in BITFRONT API.

> **Note**
>
> Pursuant to the official ticker symbol of [LINK](http://link.network), BITFRONT’s APIs will return “LN” when [Currency](/5_Terms.md#currency-for-coin-trading) is LINK.

> **Tip**
>
> The `Loc.` column in the request parameter table describes where each parameter passes in.
>
>   - path: The parameter passes in the request path.
>
>   - query: The parameter passes in the query string.
>
>   - header: The parameter passes in header attributes.
>
>   - body: The parameter passes in the request body.

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
  - [Order information v2](api/account/v2-account-orders-orderID-get.md)
  - [Coin transfer history](api/account/v1-account-transactionHistory-get.md)
