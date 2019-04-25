## Revision history

**v0.4 (2019-4-25)**

  - 주요 변경
    
    BITBOX의 [Maker](5_Terms.md#maker) 및 [Taker](5_Terms.md#taker) 거래수수료 차등수취 및 LINK로 수수료를 지불하는 정책에 따라 Order information API(`/v1/account/orders/{orderID}`)의 반환값이 변경되었습니다.

  - API 설명 업데이트
    
      - [Order information](api/account/v1-account-orders-orderID-get.md#order-information) 반환값에 `feeRate` 필드 제거, `makerFeeRate`, `takerFeeRate`, `enableLinkFee`, `makerLinkFeeRate`, `takerLinkFeeRate` 필드 추가

**v0.3 (2019-4-15)**

  - 주요 변경
    
    지난 버전까지 문서에 테이블로 제공하던 BITBOX Trading pair policy를 API로 제공합니다.
    이에 따라 관련 부록 페이지를 삭제하고 새로운 API를 추가했습니다.
    
    User trade history API(`/v1/account/tradeHistory`)가 지원 중단되어 관련 내용을 삭제했습니다.

  - API 설명 업데이트
    
      - [Market Coin Pair Policy](api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy) 추가
      - User trade history API 삭제

  - Trading pair policy 삭제

**v0.2 (2019-2-27)**

  - API 설명 업데이트
      - [User trade history API](#user-trade-history-deprecated) 지원 중단 표기
      - [User trade history API v2](api/account/v2-account-tradeHistory-get.md#user-trade-history-v2) 추가
  - Trading pair policy 업데이트

**v0.1 (2018-9-11)**

  - Beta 버전 초기 배포
