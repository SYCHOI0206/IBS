# IBS RG100-delay PWA

이 저장소의 유일한 전략은 `IBS RG100-delay v1.0`입니다. 이전 기본형·추세형 IBS는 제거했습니다.

## 최소 파일 구성

- `index.html`: 계산기, 상태머신, 거래·일별 기록, JSON 백업/복원, CSV 입출력
- `strategy.config.json`: 자동매매 구현용 기계가독 전략 계약
- `manifest.webmanifest`, `service-worker.js`, 아이콘 5개: 설치형·오프라인 PWA

## 고정 전략

- 종목/데이터: SOXL only
- IBS: `(Close-Low)/(High-Low)`, 1~4차 모두 `IBS<=0.25`, 기본 청산 `IBS>=0.75`
- Dual Proxy A: `A[t]=A[t-1]*(1+(g[t]-1)/3)`
- Dual Proxy B: `B[t]=B[t-1]*g[t]^(1/3)`
- STRONG: A/B 모두 가격>SMA200 및 SMA50>SMA200
- BULL: A 또는 B 가격>SMA200
- DEEP: A 또는 B 가격/SMA200<0.86
- 1차 체결 시 계획 고정: STRONG 35/30/20/15, BULL 30/27/23/20, BEAR 20/20/20/20
- STRONG 진입 사이클의 1~2차: IBS>=0.75, 평단 이상, +25% 미만이면 보유수량 25% QSELL 1회
- STRONG 전량목표: 종가>=평단×1.25
- DEEP trim: 2차 이상, 종가<=평단×0.97이면 보유수량 5% 1회
- 예산은 사이클 시작자산 기준 고정, 정수주 `floor`, 매도일 재매수 금지

## delay 한 가지 추가 규칙

실제 QSELL 뒤의 거래일에 공식 종가가 QSELL 신호일 공식 종가보다 한 번이라도 높게 마감하고, 아직 2차 보유 상태라면 첫 `IBS<=0.25` 3차 신호를 건너뜁니다. 다음 입력 거래일에는 매도행동이 없을 때 IBS와 무관하게 원래 3차 고정예산으로 매수합니다. D+1 매도가 있거나 수량이 0이면 취소하며 D+2로 이월하지 않습니다. 4차는 지연하지 않습니다.

행동 우선순위: `DEEP_TRIM > SELL/QSELL/FULL_SELL > DELAYED_3RD_BUY > NORMAL_IBS_BUY`.

## 사용 전 주의

레짐 계산에는 분할조정 SOXL 종가 최소 201개가 필요합니다. CSV 헤더는 `Date,Open,High,Low,Close`입니다. 앱의 “신호대로 기록”은 연구용 공식 종가 체결이며, 실전 애프터마켓 체결은 “실제 체결 기록”으로 별도 입력합니다. 주문 API는 이 저장소에 포함하지 않습니다.

구 v5.2 백업은 전략 정의가 달라 자동 복원하지 않습니다. 새 버전은 별도 저장 키를 사용합니다.
