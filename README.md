# OTT 인프라·보안 팀 프로젝트

**상태:** 팀 검토 및 설계 준비 · **발표:** 2026-11-16

## 팀 작업 순서

| 순서 | 확인할 곳 | 할 일 |
|---|---|---|
| 1 | [WBS](WBS.md) | 내 이름의 행에서 이번 단계와 기한 확인 |
| 2 | WBS에 적힌 내 Issue 번호 | 번호를 눌러 작업 항목과 완료 기준 확인 |
| 3 | 내 Notion 기술서 | 설계·명령어·설정 코드·오류·시험 과정과 결과 기록 |
| 4 | 같은 Issue의 댓글 | 퇴근 전 오늘 한 일·Notion 링크·막힌 점·다음 작업 작성 |
| 5 | PM 확인 | PM이 댓글을 보고 진행 상황과 필요한 지원 확인 |

**한 줄 규칙:** WBS는 일정, Issue는 진행 현황, Notion은 실제 기술세부내역서.
매일 WBS를 수정하거나 GitHub에 인프라·보안 설정 파일을 만들 필요 없음.

## 프로젝트 자료

| 자료 | 위치 | 내용 |
|---|---|---|
| 현재 계획서 | [v0.2 PDF](plans/project-plan-v0.2.pdf) | 팀 검토안. 확정본 아님 |
| 이전 계획서 | [v0.1 PDF](plans/project-plan-v0.1.pdf) | 변경 전 자료 |
| WBS | [WBS](WBS.md) | 주차·담당·작업 번호 |
| 회의록 | [meetings](meetings/README.md) | 실제 회의 내용과 결정 |
| 계획 설계 | [design](design/README.md) | 전체 구성도, Class Diagram, ERD 등의 팀 합의 자료 |
| 앱 코드 | [frontend](frontend/README.md) · [backend](backend/README.md) · [ai-service](ai-service/README.md) | M5 개발, M3 등 연동 팀원이 내려받을 원본 |
| 팀 Notion 템플릿 | **링크 등록 대기** | PM이 공개 템플릿을 만든 뒤 실제 접근 확인 후 연결 |

## 매일 Issue 댓글 예시

```text
날짜: 10/19
진행: 캐나다 직원망 주소 설계 초안 작성. VPN 상대 주소는 M1 확인 대기.
Notion 기록: [내 기술서의 해당 부분 링크]
막힌 점: 본사 VPN 대역 미확정
다음 작업: M1과 대역 확정 후 구성도 수정
```

PM은 각 댓글에 `확인: 일정·기록 확인 / 지원 사항: ...`처럼 답합니다. **PM 확인은 기술 시험 통과 판정이 아닙니다.**

### 기록할 때

- Issue 체크는 실제 완료 항목만. 아직 안 한 것은 `미수행`, 정하지 않은 것은 `미확정`.
- Notion 링크는 팀원이 열 수 있는 공유 권한 확인. 공개 템플릿과 개인 기술서의 공개 범위는 따로 확인.
- 공개 GitHub와 공개 Notion에 비밀번호, API 키, VPN PSK, 개인키, 실제 개인정보를 쓰지 않음.
- 인프라·보안 명령과 코드도 Notion 기술서에 기록하고, 마지막에 코드 포함 최종 문서로 취합.
- 개발 중인 앱 코드는 GitHub 세 폴더에서 관리. Issue에는 해당 코드 변경 링크만 간단히 연결.

### 첫 작업 바로가기

| 담당 | 첫 Issue |
|---|---|
| 유용수 | [#1 · 본사 네트워크](https://github.com/infra-security-team/ott-security-project/issues/1) |
| 윤서영 | [#2 · 보안·로그](https://github.com/infra-security-team/ott-security-project/issues/2) |
| 홍은서 | [#3 · 서비스망·서버](https://github.com/infra-security-team/ott-security-project/issues/3) |
| 박진혁 | [#4 · 백업·복원](https://github.com/infra-security-team/ott-security-project/issues/4) |
| 유은혜 | [#5 · 캐나다망·앱](https://github.com/infra-security-team/ott-security-project/issues/5) |

첫 Issue가 끝나면 WBS에서 다음 단계의 Issue 번호를 클릭합니다.
