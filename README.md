# AI 생산성 도우미

## 앱 소개
GitHub Copilot AI 방식의 GitHub Models API를 사용해서 할 일의 우선순위와 예상 시간을 분석해주는 개인 생산성 향상 웹앱입니다.

## 설계 철학
이 앱은 다음 원칙으로 설계되었습니다.

- **사용자 중심**: 할 일이 많아서 뭐부터 해야 할지 모르는 직장인, 학생을 대상으로 합니다.
- **AI 기반 의사결정**: GitHub Models API(gpt-4o-mini)를 활용해 객관적인 우선순위 분석을 제공합니다.
- **프라이버시 우선**: 모든 데이터를 사용자 브라우저의 localStorage에만 저장하며, 서버로 전송하지 않습니다.
- **간단한 구조**: 백엔드 없이 정적 프론트엔드만으로 완전히 동작하는 단일 HTML 파일로 구현합니다.
- **토큰 보안**: GitHub 토큰은 코드에 하드코딩하지 않으며, 사용자가 직접 입력한 후 localStorage에 저장됩니다.

## 타겟 사용자
- 개발에 관심 있는 직장인, 학생
- GitHub 개인 접근 토큰(PAT)을 발급할 수 있는 기술 수준의 사용자
- AI 기반 생산성 도구에 관심 있는 얼리어답터

## 대회 규칙 준수 체크
- 웹앱: HTML / CSS / JavaScript 단일 페이지
- AI 사용: GitHub Models API만 사용
- 기본 모델: gpt-4o-mini
- 토큰 처리: 코드 하드코딩 없음, 사용자 입력 후 localStorage 저장
- Azure 배포 대상: Azure Static Web Apps

## 토큰 처리와 심사 대응
- 현재 앱은 정적 프론트엔드만 사용하므로 GitHub 토큰을 Azure 환경변수로 숨긴 채 브라우저에서 직접 쓰는 방식은 사용하지 않았습니다.
- 실제 AI 분석은 사용자가 직접 입력한 GitHub Token으로만 실행됩니다.
- 심사자 또는 자동 검증이 토큰을 입력하기 어려운 상황을 위해 토큰 없이도 흐름을 확인할 수 있는 데모 분석 버튼을 제공합니다.
- Azure 환경변수 기반 비밀 처리가 꼭 필요하다면, 별도의 서버사이드 API 또는 Azure Functions 프록시를 추가해야 안전합니다.

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
```
lipcoding2026_solbao-dev/
├── index.html                    # 앱 전체 코드 (HTML + CSS + JavaScript)
├── staticwebapp.config.json      # Azure Static Web Apps 라우팅 설정
├── README.md                     # 이 문서
├── PRD.md                        # 제품 요구사항 정의
└── AGENTS.md                     # 음성 코딩 개발 규칙 (참고용)
```

## 왜 이 기술을 선택했나?

### GitHub Models API (GitHub Copilot SDK)
- OpenAI 호환 API로 표준화되어 있음
- 브라우저에서 직접 호출 가능
- gpt-4o-mini는 가볍고 빠른 응답 제공
- 별도 서버 없이도 AI 기능 구현 가능

### localStorage 기반 저장
- 서버 비용과 복잡성 제거
- 사용자 데이터가 개인 브라우저에만 남음
- 새로고침 후에도 데이터 유지
- 즉시 배포 가능한 정적 웹앱 실현

### 백엔드 없는 구조
- 배포 인프라 단순화
- 스케일링 비용 없음
- 보안 공격 표면 최소화
- Azure Static Web Apps의 무료/저가 호스팅 활용

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

## 최종 제출 정보
- GitHub 저장소: https://github.com/solbao-dev/lipcoding2026_solbao-dev
- 라이브 URL: https://red-smoke-003835800.7.azurestaticapps.net/
- 캐시 무효화 확인 URL: https://red-smoke-003835800.7.azurestaticapps.net/?verify=1781937246286
- 배포 워크플로 성공 실행: https://github.com/solbao-dev/lipcoding2026_solbao-dev/actions/runs/27862999742

## 최근 UI 변경
- `앱 데이터 모두 초기화 (새로 시작)` 버튼 위치를 `1) GitHub 토큰 설정` 카드에서
	`개인정보 보호 및 로컬 데이터 처리` 카드로 이동했습니다.
- 의도: 데이터 삭제 동작을 보안/프라이버시 문맥에서 더 명확하게 인지하도록 UX를 정리했습니다.

## 최종 검증 상태
- 토큰 저장/삭제 동작 확인
- 할 일 추가/완료/삭제 동작 확인
- 데모 분석/실제 분석 흐름 확인
- localStorage 저장/복원 확인
- Azure 배포 반영 및 위치 변경 반영 확인

## Azure 배포 상태
- Azure Static Web Apps 배포 완료
- 프로덕션 URL 접속 확인 완료

## 배포 메모
대회 중 재배포가 필요하면 다음 흐름으로 진행합니다.
1. `main` 브랜치에 커밋/푸시
2. GitHub Actions 워크플로(`.github/workflows/azure-static-web-apps.yml`) 실행 확인
3. Azure Static Web Apps 프로덕션 URL에서 반영 확인

### 배포 경로 고정
- 배포 소스는 루트 경로(`/`)로 고정합니다.
- `index.html`과 `staticwebapp.config.json`을 직접 배포하므로 `dist` 수동 동기화가 필수가 아닙니다.

### GitHub Secret
- 저장소 Secrets에 `AZURE_STATIC_WEB_APPS_API_TOKEN`을 등록해야 자동 배포가 동작합니다.
