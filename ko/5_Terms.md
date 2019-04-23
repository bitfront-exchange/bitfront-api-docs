# Glossary

이 문서는 암호화폐 거래 관련 널리 사용되는 용어와 몇 가지 새로 정의한 용어를 사용하고 있습니다.
이해를 돕기 위해 중요한 용어를 설명합니다.

## Coin code

암호화폐의 심벌(ticker symbol)을 대문자로 쓴 것.

BITBOX는 각 암호화폐에 대해 공식적으로 혹은 널리 사용되는 심벌을 사용합니다. 가능한 coin code는 [Market coin pair policy](api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy)에서 볼 수 있습니다.

## Coin pair

암호화폐 간 거래에서 한 암호화폐에 대한 다른 암호화폐의 상대적 가치를 나타내는 문구.
이 문서에서 coin pair는 [Currency](#currency-for-coin-trading)의 [coin code](#coin-code)와 [Market](#market-for-coin-trading)의 [coin code](#coin-code)를 구분 문자를 이용해 연결한 것을 말합니다.
예를 들어 “BCH.ETH”는 이더리움 기준에서 비트코인 캐시의 가치를 나타냅니다.

암호화폐 거래 시에는 일반적으로 사선(/)을 구분 문자로 사용하나, 여기서는 점(.)을 사용하는 것에 유의하십시오.
가능한 coin pair는 [Market coin pair policy](api/market/v1-market-public-coins-pairPolicy-get.md#market-coin-pair-policy)에서 볼 수 있습니다.

## Completed order

주문은 총수량이 모두 체결되거나, 일부 체결 및 취소될 수 있습니다.
이 문서에서는 이렇게 체결되거나 취소된 수량이 총수량과 같은 주문을 완료된 주문이라고 부릅니다.
즉, “완료되었다”는 말은 “매치되어 전 수량이 체결되었다”는 의미가 아닙니다. 완료된 주문의 일부 수량은 취소되었을 수 있습니다.

## Currency (for coin trading)

이 문서에서는 A로 B를 구매할 때 B를 Currency라고 부릅니다. 예를 들어 비트코인으로 이더리움을 구매할 때는 이더리움이 Currency가 됩니다.

[Market](#market-for-coin-trading)도 함께 참고하십시오.

## Maker

체결되지 않는 주문을 걸어 호가창에 매수/매도 잔량을 만드는 사용자를 의미합니다.

## Market (for coin trading)

이 문서에서는 A로 B를 구매할 때 A를 Market이라고 부릅니다. 예를 들어 비트코인으로 이더리움을 구매할 때는 비트코인이 Market이 됩니다.

[Currency](#currency-for-coin-trading)도 함께 참고하십시오.

## Taker

호가창의 매수/매도 잔량을 자신의 주문으로 즉시 체결시키는 사용자를 의미합니다.
