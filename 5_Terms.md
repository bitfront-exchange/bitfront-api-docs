# Glossary

In this document, we use commonly used terms in the cryptocurrency trading and define some terms.
To help you get a better understanding, we provide the list of important terms.

## Coin code

A ticker symbol of a coin written in uppercase.

BITFRONT uses the commonly or officially used symbols of each cryptocurrency; all available coin codes are listed in [Market coin pair policy](/api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy).

## Coin pair

The string of the relative value of a coin against another coin in crypto-to-crypto trading.
In this document, a coin pair is represented as a concatenated string of the [coin code](#coin-code) of [Currency](#currency-for-coin-trading) and that of [Market](#market-for-coin-trading) with a delimiter.
For example, “BCH.ETH” represents the relation of Bitcoin cash against Ethereum.

Note that a dot (.) is used as a delimiter in API calls while a slash (/) is generally used in cryptocurrency trading.
Available coin pairs are listed in [Market coin pair policy](/api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy).

## Completed order

An order can be fully filled, or partially filled and cancelled.
In this document, we say an order is completed when the order is fulfilled by fill and/or cancellation as mentioned above.
Note that “complete” does NOT mean “fully matched and filled”. A completed order could have a part of the requested amount cancelled.

## Currency (for coin trading)

When you want to buy Ethereum with Bitcoin, the Ethereum is the Currency.

See [Market](#market-for-coin-trading) also.

## Maker

When a user places a buy/sell order which is not immediately matched by an existing order and the order is added to the order book, that user is considered as a Maker.

## Market (for coin trading)

When you want to buy Ethereum with Bitcoin, the Bitcoin is the Market.

See [Currency](#currency-for-coin-trading) also.

## Taker

When a user places a buy/sell order that is immediately filled, that user is considered as a Taker.
