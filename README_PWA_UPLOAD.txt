IBS 운용 도우미 v5.1 PWA

핵심 변경사항
1. 거래기록 수정
- 매수와 쿼터매도: 수량과 체결단가 수정 가능
- 전량매도: 전략상 당시 전 보유수량을 매도하므로 체결단가만 수정 가능
- 수정 저장 시 해당 거래 이후의 현금, 보유수량, 평균단가, 사이클 손익, 평가자산, MDD, 그래프를 전체 재계산
- 잘못 수정했을 때 '최근 수정 되돌리기'로 직전 상태 복원

2. 과거 SOXL OHLC 화면
- 기록 탭에서 최근 30일, 60일, 120일 또는 전체 기간 선택
- OHLC 캔들차트, 기간 최고/최저, 최근 종가 표시
- 날짜 검색과 20개 단위 페이지 표 제공
- 일별 IBS 구간과 실제 거래 여부 함께 표시
- 시장 CSV 내보내기 지원

3. 과거 OHLC 보강
- 설정에서 Date, Open, High, Low, Close 열이 있는 CSV 등록
- 거래를 이미 시작했어도 최초 일별 기록일보다 이전 날짜는 과거 시장데이터로 추가 가능
- 과거 데이터는 거래·자산 원장과 분리해 보관하며 추세판정과 OHLC 화면에 사용
- 최대 5,000개 거래일 보관
- 직접 입력한 일별·거래 기록은 그대로 유지

중요한 동작
- 거래 수정은 실제 체결기록을 바로잡는 기능입니다. 전략신호 자체를 과거로 돌아가 새로 만들지는 않습니다.
- 매수수량을 줄여 이후 쿼터매도 수량이 당시 보유량을 초과하게 되면 수정이 거부됩니다.
- 이전 매수수량을 수정하면 뒤의 전량매도 수량은 당시 남은 전 보유수량으로 자동 보정됩니다.
- OHLC CSV로 보강한 과거 데이터는 계좌자산 그래프가 아니라 시장가격 차트와 30일 추세판정에 사용됩니다.

GitHub 업데이트 방법
1. 기존 앱에서 설정 > JSON 백업
2. 이 폴더의 파일을 GitHub IBS 저장소 최상단에 모두 업로드
3. 같은 이름의 index.html, manifest.webmanifest, service-worker.js는 새 버전으로 교체
4. ui_preview_v51_mobile.png와 ui_preview_v51_desktop.png도 함께 업로드
5. Commit changes
6. GitHub Pages 배포 후 폰 앱을 완전히 종료하고 다시 실행
7. 화면에 v5.1 PWA가 보이지 않으면 Chrome에서 페이지 새로고침 후 앱 재실행

필수 업로드 파일
- index.html
- manifest.webmanifest
- service-worker.js
- icon-192.png
- icon-512.png
- icon-maskable-192.png
- icon-maskable-512.png
- apple-touch-icon.png
- favicon-32.png
- ui_preview_v51_mobile.png
- ui_preview_v51_desktop.png

저장 호환성
- 기존 localStorage 키 ibs2575_complete_v3 유지
- v3.x, v4.x, v5.0 JSON 백업 복원 가능
- 앱 업데이트 전 JSON 백업 권장
