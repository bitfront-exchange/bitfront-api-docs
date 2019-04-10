## Revision history

**v0.3 (2019-4-15)**

  - Key updates
    
    The BITBOX Trading Pair Policy was provided as an appendix table in the document until the previous version. It is now available via new API with the current update.
    The appendix table was deleted and the relevant section on new API was added.
    
    User trade history API(`/v1/account/tradeHistory`) is no longer supported so the corresponding section was deleted.

  - Updated API descriptions
    
      - Added [Market Coin Pair Policy](api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy) API
      - Deprecated the User trade history API

  - Deleted the Trading Pair Policy table

  - Made corrections in the documentation
    
      - Corrected the endpoint (`/v1/account/tradeHistory` \>`/v2/account/tradeHistory`) for [User trade history API v2](api/account/v2-account-tradeHistory-get.md#user-trade-history-v2)

**v0.2 (2019-02-27)**

  - Updated API descriptions
      - Deprecated the user trade history API
      - Added the [user trade history API v2](api/account/v2-account-tradeHistory-get.md#user-trade-history-v2)
  - Updated the trading pair policy

**v0.1 (2018-09-11)**

  - Initial beta release
