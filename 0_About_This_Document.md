## Revision history

**v0.5 (2019-8-12)**

  - Key updates
    
    When the Currency is LINK, the ticker symbol returned by all APIs are changed from “LINK” to “LN”. Only the deprecated Order information(`/v1/account/orders/{orderID}`) will return “LINK”, and this API will be available temporarily.

  - Updated API descriptions
    
      - Deprecated [Order information](/api/account/v1-account-orders-orderID-get.md#order-information-deprecated) and added the use of LINK ticker symbol
      - Added [Order information v2](/api/account/v2-account-orders-orderID-get.md#order-information-v2)
      - Replaced Order information API link in the description of [Cancellation of all open orders](/api/trade/v1-trade-openOrders-delete.md#cancellation-of-all-open-orders) and [Cancellation](/api/trade/v1-trade-orders-delete.md#cancellation) with Order information v2
      - Added the description of LINK ticker symbol in the API list

**v0.4 (2019-4)**

  - Key updates
    
    Pursuant to the BITBOX’s policy on the tiered fee structure for [Maker](/5_Terms.md#maker) & [Taker](/5_Terms.md#taker) and fee payment with LINK, the return value of Order information API (`/v1/account/orders/{orderID}`) has been changed.

  - Updated API descriptions
    
      - `feeRate` field was deleted from the return value of [Order information](/api/account/v1-account-orders-orderID-get.md#order-information-deprecated), and the new fields, namely `makerFeeRate`, `takerFeeRate`, `enableLinkFee`, `makerLinkFeeRate`, and `takerLinkFeeRate`, were added.

  - Made corrections in the documentation
    
      - Corrected the RPS limits in [Request](/1_Overview.md#request) according to the current system policy

**v0.3 (2019-4-15)**

  - Key updates
    
    The BITBOX Trading Pair Policy was provided as an appendix table in the document until the previous version. It is now available via new API with the current update.
    The appendix table was deleted and the relevant section on new API was added.
    
    User trade history API(`/v1/account/tradeHistory`) is no longer supported so the corresponding section was deleted.

  - Updated API descriptions
    
      - Added [Market Coin Pair Policy](/api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy) API
      - Deprecated the User trade history API

  - Deleted the Trading Pair Policy table

  - Made corrections in the documentation
    
      - Corrected the endpoint (`/v1/account/tradeHistory` \>`/v2/account/tradeHistory`) for [User trade history API v2](/api/account/v2-account-tradeHistory-get.md#user-trade-history-v2)

**v0.2 (2019-02-27)**

  - Updated API descriptions
      - Deprecated the user trade history API
      - Added the [user trade history API v2](/api/account/v2-account-tradeHistory-get.md#user-trade-history-v2)
  - Updated the trading pair policy

**v0.1 (2018-09-11)**

  - Initial beta release
