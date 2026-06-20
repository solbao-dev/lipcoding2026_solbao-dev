# Azure Deployment Plan

## Status
Deployed (Azure Static Web Apps)

## Goal
대회 규칙을 모두 준수하는 개인 생산성 향상 웹앱을 Azure Static Web Apps에 배포 가능한 형태로 준비한다.

## Contest Constraints
- 웹앱이어야 함
- AI 기능은 GitHub Models API만 사용
- 기본 모델은 gpt-4o-mini 유지
- 토큰은 코드에 하드코딩하지 않음
- 초보자도 이해할 수 있게 단순한 구조 유지
- Azure 배포를 전제로 준비

## Workspace Mode
MODIFY

## Current App Shape
- 단일 파일 웹앱: index.html
- 프론트엔드만 사용: HTML + CSS + JavaScript
- localStorage 사용
- GitHub Token을 사용해 GitHub Models API 호출

## Architecture Decision
- Frontend: 정적 단일 페이지 앱
- AI integration: GitHub Models API fetch 호출
- Hosting target: Azure Static Web Apps
- Persistence: 브라우저 localStorage

## Implementation Steps
1. 초보자용 사용 흐름과 단계 설명을 UI에 추가
2. 기능을 작은 단위로 검증할 수 있는 체크리스트 추가
3. README에 사용법, 검증 순서, 배포 준비 상태 정리
4. Azure Static Web Apps용 최소 설정 파일 추가
5. 변경 파일 정적 오류 확인

## Validation Plan
- index.html 정적 오류 확인
- README 및 JSON 설정 파일 형식 확인
- 토큰 저장, 할 일 추가, 완료 체크, 삭제, 분석 흐름을 수동 검증 가능하도록 문서화

## Deployment Notes
- Azure Static Web Apps 리소스 생성 완료: `lipcoding-swa-3593`
- 프로덕션 배포 URL: `https://red-smoke-003835800.7.azurestaticapps.net/`
- 현재 상태: 배포 및 접속 확인 완료

## Latest Updates (2026-06-20)
- ✅ 개인정보 보호 및 로컬 데이터 처리 안내 섹션 추가
  - 진행률 카드 바로 아래 배치
  - GitHub 토큰, 할 일 목록, 분석 결과 모두 로컬 저장 명시
  - 신뢰감을 위해 초록색 테마 + 체크마크 디자인 적용
- ✅ 음성 입력 자동 마이크 권한 요청 기능 추가
  - 음성 입력 버튼 클릭 시 getUserMedia()를 통해 권한 자동 요청
  - 권한 거부/허용 상태에 따른 명확한 안내 메시지 표시
  - InvalidStateError 등 예외 상황 처리 개선
- ✅ 모든 변경사항 Azure Static Web Apps에 배포 완료

## Features Completed
1. ✅ 웹 기반 개인 생산성 도우미 앱
2. ✅ 음성 입력 (Web Speech API, 한국어)
3. ✅ 할 일 추가/삭제/완료 체크
4. ✅ GitHub Models API 연동 (gpt-4o-mini)
5. ✅ AI 우선순위 분석 및 집중 추천
6. ✅ 데모 분석 버튼 (토큰 없이도 테스트 가능)
7. ✅ localStorage 데이터 영속성
8. ✅ 진행률 시각화 (프로그레스 바)
9. ✅ 개인정보 보호 명시 안내
10. ✅ 초보자 친화적 UI와 단계별 가이드
11. ✅ 제출 전 최종 점검 체크리스트

## Ready for Submission
- 모든 필수 규칙 준수 ✅
- Azure 배포 완료 ✅
- GitHub Copilot SDK/Models API 통합 ✅
- 한국어 UI ✅
- 음성 입력 가능 ✅
- 개인정보 보호 명시 ✅
