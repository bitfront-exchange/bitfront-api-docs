## Revision history

**v0.5 (2019-8-12)**

  - 주요 변경
    
    Currency가 LINK일 때 모든 API가 반환하는 `currency` 필드를 “LINK”에서 “LN”로 변경합니다. 삭제 예정인 Order information(`/v1/account/orders/{orderID}`)만 한시적으로 “LINK”로 반환합니다.

  - API 설명 업데이트
    
      - [Order information](/api/account/v1-account-orders-orderID-get.md#order-information-deprecated) 지원 중단 표기 및 LINK 티커 심볼 설명 추가
      - [Order information v2](/api/account/v2-account-orders-orderID-get.md#order-information-v2) 추가
      - [Cancellation of all open orders](/api/trade/v1-trade-openOrders-delete.md#cancellation-of-all-open-orders), [Cancellation](/api/trade/v1-trade-orders-delete.md#cancellation) 설명의 Order information API 링크를 Order information v2로 변경
      - 전체 API 목록에 LINK 티커 심볼 설명 추가
      - [Open orders](/api/trade/v1-trade-openOrders-get.md#open-orders) 필드에 설명 추가

**v0.4 (2019-4)**

  - 주요 변경
    
    BITBOX의 [Maker](/5_Terms.md#maker) 및 [Taker](/5_Terms.md#taker) 거래수수료 차등수취 및 LINK로 수수료를 지불하는 정책에 따라 Order information API(`/v1/account/orders/{orderID}`)의 반환값이 변경되었습니다.

  - API 설명 업데이트
    
      - [Order information](/api/account/v1-account-orders-orderID-get.md#order-information-deprecated) 반환값에 `feeRate` 필드 제거, `makerFeeRate`, `takerFeeRate`, `enableLinkFee`, `makerLinkFeeRate`, `takerLinkFeeRate` 필드 추가

  - 문서 오류 교정
    
      - [요청](/1_Overview.md#요청)에 기술된 RPS 한도를 현재 시스템 정책에 따라 수정

**v0.3 (2019-4-15)**

  - 주요 변경
    
    지난 버전까지 문서에 테이블로 제공하던 BITBOX Trading pair policy를 API로 제공합니다.
    이에 따라 관련 부록 페이지를 삭제하고 새로운 API를 추가했습니다.
    
    User trade history API(`/v1/account/tradeHistory`)가 지원 중단되어 관련 내용을 삭제했습니다.

  - API 설명 업데이트
    
      - [Market Coin Pair Policy](/api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy) 추가
      - User trade history API 삭제

  - Trading pair policy 삭제

**v0.2 (2019-2-27)**

  - API 설명 업데이트
      - User trade history API 지원 중단 표기
      - [User trade history API v2](/api/account/v2-account-tradeHistory-get.md#user-trade-history-v2) 추가
  - Trading pair policy 업데이트

**v0.1 (2018-9-11)**

  - Beta 버전 초기 배포
