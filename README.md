# AI 생산성 도우미

## 앱 소개
GitHub Copilot AI 방식의 GitHub Models API를 사용해서 할 일의 우선순위와 예상 시간을 분석해주는 개인 생산성 향상 웹앱입니다.

## 대회 규칙 준수 체크
- 웹앱: HTML / CSS / JavaScript 단일 페이지
- AI 사용: GitHub Models API만 사용
- 기본 모델: gpt-4o-mini
- 토큰 처리: 코드 하드코딩 없음, 사용자 입력 후 localStorage 저장
- Azure 배포 대상: Azure Static Web Apps

## 주요 기능
- GitHub Token 저장 / 삭제
- 할 일 추가 / 완료 체크 / 삭제
- 할 일 전용 음성 입력 버튼
- 샘플 할 일 자동 입력
- 토큰 없이도 확인 가능한 데모 분석 버튼
- localStorage 저장으로 새로고침 후 유지
- AI 분석 결과 카드 표시
- 앱 내부 단계별 검증 상태 표시

## 파일 구조
- index.html: 앱 전체 코드
- staticwebapp.config.json: Azure Static Web Apps 기본 설정
- .azure/deployment-plan.md: Azure 배포 준비 계획

## 로컬 실행 방법
1. index.html 파일을 브라우저에서 엽니다.
2. GitHub Personal Access Token을 입력하고 저장합니다.
3. 할 일을 추가하거나 샘플 할 일 넣기를 누릅니다.
4. 완료 체크와 삭제 버튼을 먼저 테스트합니다.
5. AI 분석 시작 버튼을 눌러 결과를 확인합니다.

## 단계별 검증 순서
1. 토큰 저장 버튼을 눌렀을 때 상태 메시지가 보이는지 확인
2. 할 일을 추가했을 때 목록에 바로 나타나는지 확인
3. 체크박스를 누르면 취소선이 적용되는지 확인
4. 삭제 버튼이 정상 동작하는지 확인
5. 음성 입력 버튼을 눌렀을 때 입력칸이 채워지는지 확인
6. 새로고침 후 토큰과 할 일이 유지되는지 확인
7. AI 분석 실행 후 우선순위 / 예상 시간 / 분류 / 이유가 카드로 보이는지 확인
8. 새로고침 후 분석 결과가 복구되는지 확인

## 음성 입력 참고
- 음성 입력은 할 일 입력에만 사용됩니다.
- 로컬 HTTP 테스트보다 Azure Static Web Apps의 HTTPS 주소에서 마이크 권한 동작이 더 안정적일 수 있습니다.
- 권한 팝업이 바로 뜨지 않으면 주소창의 사이트 권한에서 마이크 허용 상태를 먼저 확인하세요.

## 배포 URL
- https://red-smoke-003835800.7.azurestaticapps.net/

## Azure 배포 상태
- Azure Static Web Apps 배포 완료
- 프로덕션 URL 접속 확인 완료

## 배포 메모
대회 중 재배포가 필요하면 다음 흐름으로 진행합니다.
1. `dist` 폴더 재생성 (`index.html`, `staticwebapp.config.json` 복사)
2. SWA deployment token 확인
3. SWA CLI로 production 재배포
