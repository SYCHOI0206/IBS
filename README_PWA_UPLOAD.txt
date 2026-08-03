IBS 운용 도우미 v5.0 PWA 설치형

이 폴더의 모든 파일을 GitHub 저장소 IBS의 최상단(root)에 업로드하세요.
기존 index.html은 새 index.html로 교체합니다.

필수 파일
- index.html
- manifest.webmanifest
- service-worker.js
- icon-192.png
- icon-512.png
- icon-maskable-192.png
- icon-maskable-512.png
- apple-touch-icon.png
- favicon-32.png

선택 파일(설치 화면 미리보기)
- ui_preview_v43_mobile.png
- ui_preview_v43_desktop.png

GitHub 업로드 순서
1. ZIP을 PC에서 압축 해제합니다.
2. GitHub의 IBS 저장소를 엽니다.
3. Add file > Upload files를 누릅니다.
4. 압축을 푼 폴더 안의 파일을 모두 선택해 업로드합니다.
5. index.html 교체 확인 후 Commit changes를 누릅니다.
6. Settings > Pages에서 배포가 끝날 때까지 기다립니다.
7. https://sychoi0206.github.io/IBS/ 를 Android Chrome에서 엽니다.
8. 페이지를 한 번 새로고침합니다.
9. 상단의 '앱 설치' 버튼 또는 Chrome 메뉴 > 앱 설치를 누릅니다.

중요
- 실제 운용기록은 GitHub가 아니라 폰 Chrome의 localStorage에 저장됩니다.
- 기존 v4.3과 동일한 저장 키를 유지하므로 같은 주소와 같은 Chrome 프로필에서는 기록이 이어집니다.
- 업데이트 전 계산기 설정에서 JSON 백업을 권장합니다.
- 설치 버튼이 바로 보이지 않으면 배포 후 1~3분 기다린 다음 Chrome에서 페이지를 새로고침하세요.
- 이전 서비스워커가 남아 있으면 Chrome > 사이트 설정 > 저장공간에서 해당 사이트 데이터를 지운 뒤 다시 접속할 수 있습니다. 이 경우 기록도 지워질 수 있으므로 반드시 먼저 JSON 백업하세요.
