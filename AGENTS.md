# AGENTS.md - 천하제일 입코딩 대회 2026

## 나에 대해
나는 개발 초보자입니다. 오늘 **음성(마이크)으로만** 코딩합니다. 키보드와 마우스를 사용할 수 없습니다.
내 명령은 짧고 불완전할 수 있지만, 의도를 최대한 파악해서 완전한 코드를 만들어주세요.

## 대회 정보
- **주제**: 개인 생산성 향상 웹 앱
- **제한 시간**: 4시간 (12:30 ~ 16:30)
- **배포**: Azure (Azure Static Web Apps 또는 Azure App Service)
- **제출 마감**: 16:30

## ⚠️ 필수 규칙 3가지 (반드시 지킬 것)
1. **웹 앱**으로 만들 것
2. **GitHub Copilot SDK를 앱 안에서 직접 사용**할 것 — 앱 자체에 AI 기능을 넣어야 함
3. **Azure 클라우드에 배포**할 것

### Copilot SDK 사용 방법
앱 안에서 GitHub Models API (OpenAI 호환)를 호출해서 AI 기능을 구현:
```javascript
// GitHub Models API 호출 예시 (fetch 사용)
const response = await fetch("https://models.github.ai/inference/chat/completions", {
  method: "POST",
  headers: {
    "Authorization": `Bearer ${GITHUB_TOKEN}`,
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    model: "gpt-4o-mini",
    messages: [{ role: "user", content: "사용자 입력" }]
  })
});
```
- API 키(GitHub Token)는 사용자가 입력창에 직접 넣도록 UI 구성
- 현재 정적 웹앱 구현에서는 사용자가 입력창에 직접 넣는 방식을 기본으로 사용
- Azure 환경변수 방식은 서버사이드 API 또는 Functions 프록시가 있을 때만 안전하게 사용 가능
- 심사자나 자동 검증이 토큰을 넣기 어려운 경우를 위해 앱에 데모 분석 버튼을 함께 제공

## 절대 원칙

1. **완성된 코드만** 주세요. TODO, 플레이스홀더, "여기에 추가하세요" 같은 미완성 코드 금지
2. **한 파일로** 시작하세요. `index.html` 하나에 HTML + CSS + JS 전부 넣기
3. **즉시 실행 가능**해야 합니다. 브라우저에서 파일을 열면 바로 동작해야 함
4. **한국어 UI** - 모든 텍스트는 한국어로
5. 설명은 짧게, **코드 먼저** 주세요

## 기술 스택

- **프론트엔드**: HTML + CSS + JavaScript (단일 index.html 파일)
- **AI 연동**: GitHub Models API (fetch로 직접 호출, 라이브러리 불필요)
- **백엔드**: 없음 (API 키는 프론트에서 처리)
- **배포**: Azure Static Web Apps

## 파일 구조

```
내앱/
├── index.html      ← 전부 여기에
├── AGENTS.md       ← 이 파일
├── PRD.md          ← 기획서
└── README.md       ← 제출용
```

## 음성 명령 해석 가이드

| 내가 말하는 것 | Copilot이 해야 하는 것 |
|---|---|
| "만들어줘" | PRD.md를 읽고 index.html을 처음부터 완성 |
| "추가해줘" | 기존 코드를 유지하면서 새 기능 추가 |
| "고쳐줘" | 현재 오류 찾아서 수정 |
| "예쁘게 해줘" | 디자인/CSS 개선 |
| "저장되게 해줘" | localStorage 연동 추가 |
| "배포해줘" | Azure 배포 명령어 알려주기 |
| "처음부터 다시" | index.html 새로 작성 |

## Azure 배포 방법

정적 HTML 앱 배포 순서:
```bash
# 1. Azure Static Web Apps 배포 (가장 빠름)
az staticwebapp create --name my-productivity-app --resource-group mygroup --location eastasia

# 또는 Azure Developer CLI 사용
azd init
azd up
```

## 앱 디자인 원칙
- 배경: 어두운 색 (다크 테마) 또는 밝은 민트/파스텔
- 폰트: 시스템 기본 폰트 사용
- 버튼: 크고 클릭하기 쉽게
- 모바일 반응형 필수
- 그림자, 둥근 모서리로 모던하게

## PRD 읽기
코드 작성 전에 반드시 `PRD.md` 파일을 읽고 앱의 기능과 요구사항을 파악하세요.
